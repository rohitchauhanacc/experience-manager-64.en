---
title: Improve performance of large forms with lazy loading
seo-title: Improve performance of large forms with lazy loading
description: Lazy loading significantly improves the performance of large and complex adaptive forms by deferring initialization and loading of form fragments until they are visible.
seo-description: Lazy loading significantly improves the performance of large and complex adaptive forms by deferring initialization and loading of form fragments until they are visible.
uuid: 3ead2b82-f895-4a7b-9683-495fcd94fade
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: d570ead9-8f9c-4668-8b23-e8984d9b25e9
feature: Adaptive Forms
exl-id: 92d88888-343c-4edb-9b11-8e876539573a
---
# Improve performance of large forms with lazy loading {#improve-performance-of-large-forms-with-lazy-loading}

## Introduction to lazy loading {#introduction-to-lazy-loading}

When form become large and complex with hundreds and thousands of fields, end users experience long response time when rendering forms at runtime. To minimize the response time, adaptive forms allows you to break forms into logical fragments and configure to defer initialization or loading of fragments until the fragment needs to be visible. It is referred to as lazy loading. In addition, the fragments configured for lazy loading are unloaded once user navigates to other sections in the form and the fragments are no longer visible.

Let's first understand the requirements and preparatory steps before you configure lazy loading.

## Preparing to configure lazy loading {#preparing-to-configure-lazy-loading}

Before you configure lazy loading of fragments in your adaptive form, it is important you define strategies to create fragments, identify values that are used in scripts or referred in other fragments, and define rules to control visibility of fields in lazily loaded fragments.

* **Identify and create fragments** 
  You can configure only adaptive form fragments for lazy loading. A fragment is a stand-alone segment that resides outside an adaptive form and can be reused across forms. So, the first step toward implementing lazy loading is to identify logical sections in a form and convert them into fragments. You can create a fragment from scratch or save an existing form panel as fragment.  
  
  For more information about creating fragments, see [Adaptive form fragments](/help/forms/using/adaptive-form-fragments.md).

* **Identify and mark global values** 
  Forms-based transactions involve dynamic elements to capture relevant data from users and process it to simplify form filling experience. For example, your form has field A in fragment X whose value determines the validity of field B in another fragment. In this case, if fragment X is marked for lazy loading, the value of field A must be available to validate field B even when fragment X is not loaded. To achieve this, you can mark field A as global, which ensures that its value is available for validating field B when fragment X is not loaded.  
  
  For information about how to make a field value global, see [Configuring lazy loading](/help/forms/using/lazy-loading-adaptive-forms.md#p-configuring-lazy-loading-p).

* **Write rules to control visibility of fields** 
  Forms include some fields and sections that are not applicable to all users and in all conditions. Forms authors and developers use visibility or show-hide rules to control their visibility based on user inputs. For example, the Office Address field is not shown to the users who choose Unemployed in the Employment Status field in a form. For more information about writing rules, see [Using rule editor](/help/forms/using/rule-editor.md).  
  
  You can leverage visibility rules in the lazily loaded fragments so that conditional fields are shown only when they are required. Also, mark the conditional field global to refer to it in the visibility expression of the lazily loaded fragment.

## Configuring lazy loading {#configuring-lazy-loading}

Perform the following steps to enable lazy loading on an adaptive form fragment:

1. Open the adaptive form in authoring mode that contains the fragment you want to enable for lazy loading.
1. Select the adaptive form fragment and tap ![cmppr](assets/cmppr.png).
1. In the sidebar, enable **[!UICONTROL Load fragment lazily]** and tap **Done**.

   ![Enable lazy loading for the adaptive form fragment](assets/lazy-loading-fragment.png)

   The fragment is now enabled for lazy loading.

You can mark the values of objects in the lazily loaded fragment as global so that they are available for use in scripts when the containing fragment is not loaded. Do the following:

1. Open the adaptive form fragment in authoring mode.
1. Tap the field whose value you want to mark as global, and then tap ![](assets/cmppr.png).
1. In the sidebar, enable **[!UICONTROL Use value during lazy loading]**.
   ![Lazy loading field in sidebar](assets/enable-lazy-loading.png)

   The value is now marked as global and will be available for use in scripts even when the containing fragment is unloaded.

## Considerations and best practices for configuring lazy loading {#considerations-and-best-practices-for-configuring-lazy-loading}

Some limitations, recommendations, and important points to keep in mind when working with lazy loading are as follows:

* It is recommended to use XSD schema-based adaptive forms over XFA-based adaptive forms for configuring lazy loading on large forms. The performance gain due to lazy loading implementation in XFA-based adaptive forms is relatively less than gain in XSD-based adaptive forms.
* Do not configure lazy loading on fragments in a responsive grid layout. It can result in degraded performance.
* It is recommended not to configure lazy loading on fragments in the first panel that renders on loading the adaptive form.
* Lazy loading is supported up to two levels in the fragment hierarchy.
* Ensure that fields marked as global are unique across an adaptive form.
* Consider writing visibility rules for fragments that should show or hide based on a condition. For example, you can show or hide the Spouse Details fragment based on the marital status specified by a user. 
* File attachment and Terms and conditions components are not supported in lazily loaded fragments.

### Scripting best practices for configuring lazy loading {#scripting-best-practices-for-configuring-lazy-loading}

Important points to keep in mind while developing scripts for lazy loading panels are as follows:

* Ensure that initialize and calculate scripts used on the fields of a lazy loaded fragment are are idempotent in nature. Idempotent scripts are those which have same effect even after multiple executions.
* Use the globally available property of fields to make value of fields located in a lazy loading panel available to all other panels of a form.
* Do not forward reference value of a field inside a lazy panel irrespective of field being marked globally across fragments or not.
* Use panel reset feature to reset everything visible on the panel by using the following click expression.

  guideBridge.resolveNode(guideBridge.getFocus({"focusOption": "navigablePanel"})).resetData()
