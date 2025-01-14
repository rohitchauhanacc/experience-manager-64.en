---
title: Embed adaptive form in external web page
seo-title: Embed adaptive form in external web page
description: Learn how to embed an adaptive form in an external web page
seo-description: Learn how to embed an adaptive form in an external HTML web page
uuid: c612ca3b-62f7-4021-939b-e0c05dbbf0d7
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: author
discoiquuid: b99c7b93-ba05-42ee-9ca8-0079e15d8602
feature: Adaptive Forms
exl-id: 84a46197-9933-4b94-a8e3-e7baf9c644b1
---
# Embed adaptive form in external web page{#embed-adaptive-form-in-external-web-page}

Learn how to embed an adaptive form in an external web page

You can [Embed adaptive form in AEM Sites](/help/forms/using/embed-adaptive-form-aem-sites.md) page or a web page hosted outside AEM. The embedded adaptive form is fully functional and users can fill and submit the form without leaving the page. It helps the user remain in the context of other elements on the web page and simultaneously interact with the form.

## Prerequisites {#prerequisites}

Perform the following steps before embedding an adaptive form to an external website:

* Publish the adaptive form on AEM Publish instance.
* Create or identify a webpage on your website to host the adaptive form. Ensure that the webpage can [read jQuery files from a CDN](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) or has a local copy of the jQuery embeded. jQuery is required to render an adaptive form.
* When AEM server and the web page are on different domains, perform the steps listed in sectiion, [enable AEM Forms to serve adaptive forms to a cross domain site](#cross-domain-sites).
* [Setup reverse proxy](#reveseproxy) to enable communication between external page and AEM Forms server.

## Embed adaptive form {#embed-adaptive-form}

You can embed an adaptive form by inserting a few lines of JavaScript in the web page. The API in the code sends an HTTP request to the AEM server for adaptive form resources and injects the adaptive form in the specified form container. Here is a sample code to embed an adaptive form to an external page. Don't use the code as it is in a production environment. Customize the code to suit your website like using an iFrame for websites which use their own version of jQuery. Using iFrame helps avoid conflicts within jQuery versions:


1. Embed the following code to a webpage on your website: 

   ```html
   <!doctype html>
   <html>
   <head>
    <title>This is the title of the webpage!</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
   </head>
   <body>
   <div class="customafsection"/>
   <p>This section is replaced with the adaptive form.</p>
     
    <script>
    var options = {path:"/content/forms/af/locbasic.html", dataRef:"", themepath:"", CSS_Selector:".customafsection"};
    alert(options.path);
    var loadAdaptiveForm = function(options){
    //alert(options.path);
    if(options.path) {
        // options.path refers to the publish URL of the adaptive form
        // For Example: http:myserver:4503/content/forms/af/ABC, where ABC is the adaptive form
        // Note: If AEM server is running on a context path, the adaptive form URL must contain the context path 
        var path = options.path;
        path += "/jcr:content/guideContainer.html";
        $.ajax({
            url  : path ,
            type : "GET",
            data : {
                // Set the wcmmode to be disabled
                wcmmode : "disabled"
                // Set the data reference, if any
               // "dataRef": options.dataRef
                // Specify a different theme for the form object
              //  "themeOverride" : options.themepath
            },
            async: false,
            success: function (data) {
                // If jquery is loaded, set the inner html of the container
                // If jquery is not loaded, use APIs provided by document to set the inner HTML but these APIs would not evaluate the script tag in HTML as per the HTML5 spec
                // For example: document.getElementById().innerHTML
                if(window.$ && options.CSS_Selector){
                    // HTML API of jquery extracts the tags, updates the DOM, and evaluates the code embedded in the script tag.
                    $(options.CSS_Selector).html(data);
                }
            },
            error: function (data) {
                // any error handler
            }
        });
    } else {
        if (typeof(console) !== "undefined") {
            console.log("Path of Adaptive Form not specified to loadAdaptiveForm");
        }
    }
    }(options);
     
    </script>
   </body>
   </html>
   ```

1. In the embedded code:

    * Change value of the `options.path` variable with the path of the publish URL of the adaptive form. If the AEM server is running on a context path, ensure that the URL includes the context path. For example, the above code and adaptive from reside on same aem forms server so the example uses context path of adaptive form /content/forms/af/locbasic.html. 
    * Replace `options.dataRef` with attributes to pass with the URL. You can use the dataref variable to [prefill an adaptive form](/help/forms/using/prepopulate-adaptive-form-fields.md).
    * Replace `options.themePath` with the path to a theme other than the theme configured in the adaptive form. Alternatively, you can specify the theme path using the request attribute.
    * `CSS_Selector` is the CSS selector of the form container in which the adaptive form is embedded. For example, .customafsection css class is the CSS selector in the above example.

The adaptive form is embedded in the web page. Observe the following in the embedded adaptive form:

* Header and footer in the original adaptive form are not included in the embedded form.
* Drafts and submitted forms are available in the Drafts and Submissions tab in the Forms Portal.
* Submit action configured on the original adaptive form is retained in the embedded form.
* Adaptive form rules are retained and fully functional in the embedded form.
* Experience targeting and A/B tests configured in the original adaptive form do not work in the embedded form.
* If Adobe Analytics is configured on the original form, the analytics data is captured in Adobe Analytics server. However, it is not available in the Forms analytics report.

## Seup Reverse Proxy  {#reveseproxy}

The external web page that embeds the adaptive form sends requests to the AEM server, which typically sits behind the firewall in a private network. To ensure that the requests are securely directed to the AEM server, it is recommended to set up a reverse proxy server.

Let's look at an example how you can set up an Apache 2.4 reverse proxy server without dispatcher. In this example, you will host the AEM server with `/forms` context path and map `/forms` for the reverse proxy. It ensures that any request for `/forms` on Apache server are directed to the AEM instance. This topology helps reduces the number of rules at the dispatcher layer as all request prefixed with `/forms` route to the AEM server.

1. Open the `httpd.conf` configuration file and uncomment the following lines of code. Alternatively, you can add these lines of code in the file.

   ```
   LoadModule proxy_html_module modules/mod_proxy_html.so 
    LoadModule proxy_http_module modules/mod_proxy_http.so
   ```

1. Set up proxy rules by adding the following lines of code in the `httpd-proxy.conf` configuration file.

   ```
   ProxyPass /forms https://[AEM_Instance]/forms 
    ProxyPassReverse /forms https://[AEM_Instance]/forms
   ```

   Replace `[AEM_Instance]` with the AEM server publish URL in the rules.

If you do not mount the AEM server on a context path, the proxy rules at Apache layer will be as follows:

```java
ProxyPass /content https://<AEM_Instance>/content
ProxyPass /etc https://<AEM_Instance>/etc
ProxyPass /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# CSRF Filter
ProxyPass /libs/granite/csrf/token.json https://<AEM_Instance>/libs/granite/csrf/token.json
  
ProxyPassReverse /etc https://<AEM_Instance>/etc
ProxyPassReverse /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# written for thank you page and other URL present in AF during redirect
ProxyPassReverse /content https://<AEM_Instance>/content
```

>[!NOTE]
>
>If you set up any other topology, ensure that you add the submit, prefill, and other URLs to the allowlist at the dispatcher layer.

## Best practices {#best-practices}

When embedding an adaptive form in a web page, consider the following best practices:

* Ensure that the styling rules defined in the web page CSS do not conflict with the form object CSS. To avoid the conflicts, you can reuse the web page CSS in the adaptive form theme using AEM client library. For information about using client library in adaptive form themes, see [Themes in AEM Forms](/help/forms/using/themes.md).
* Make the form container in the web page use the entire window width. It ensures that the CSS rules configured for mobile devices work without any changes. If the form container does not take the entire window width, you need to write custom CSS to make the form adapt to different mobile devices. 
* Use  [getData](https://helpx.adobe.com/experience-manager/6-4/forms/javascript-api/GuideBridge.html) API to get the XML or JSON representation of form data in client. 
* Use [unloadAdaptiveForm](https://helpx.adobe.com/experience-manager/6-4/forms/javascript-api/GuideBridge.html) API to unload the adaptive form from HTML DOM.
* Set up the access-control-origin header when sending response from AEM server.

## Enable AEM Forms to serve adaptive forms to a cross domain site  {#cross-domain-sites}

1. On AEM publish instance, go to AEM Web Console Configuration Manager at `http://[server]:[port]/system/console/configMgr`.
1. Locate and open the **Apache Sling Referrer** Filter configuration.
1. In the **Allowed Hosts** field, specify the domain where the web page resides. It enables the host to make POST requests to the AEM server. You can also use regular expression to specify a series of external application domains.
