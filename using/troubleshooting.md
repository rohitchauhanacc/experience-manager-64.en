---
uuid: 097afda5-30b5-46a6-993c-023b557260b0
index: y
internal: n
snippet: y
translate: y
---

# Troubleshooting

This section includes detailed information on logs available to help you troubleshoot and also includes information on some of the problems you might encounter with AEM.

### Troubleshoot Author Performance

Analyzing slow performance on Authoring instance can become quite complex. As first step it is required to figure out on which level of the technology stack the performance is decreasing.

The following decision tree provides guidenance to narrow down the bottleneck. 
![](assets/chlimage_1.png) 

#### Basic Optimization
![](assets/chlimage_1.png) 

### Configuring log files and audit logs

AEM records detailed logs that you might want to configure in order to troubleshoot installation issues. For information, see the [Working with Audit Records and Log Files](monitoring-and-maintaining.md#WorkingwithAuditRecordsandLogFiles) section.

### Using the Verbose Option

When you start AEM WCM, you can add the -v (verbose) option to the command line as in: java -jar cq-wcm-quickstart-&lt;version&gt;.jar -v.

The verbose option displays some of the Quickstart log output on the console, so it can be used for troubleshooting.

### Common Installation Issues

The following section describes some installation issues and their solutions.

#### Double-clicking the Quickstart jar does not have any effect or opens the jar file with another program (for example, archive manager)

This usually indicates a problem with the way your operating system's desktop environment is configured to open files with extension .jar. It may also indicate that you do not have Java installed, or that you are using an unsupported version of Java.

As jar files use the ubiquitous ZIP format, some of the archiving programs may automatically configure the desktop to open jar files as archive files.

To troubleshoot, do the following:

* Double check that you have at least Java version 1.6 installed.

* Try a context menu (usually right-mouse click) on the AEM WCM Quickstart, and select "Open With...."

* Check if Java or Sun Java is listed, and try to run AEM WCM with it. If you have multiple Java versions installed, select the supported one.

  If you succeed with this step, and your operating systems offers an option to always use the selected program to run the .jar files, select it. Double-clicking should work from now on.

* Sometimes reinstalling the supported Java version helps restore the correct association.

* You can always run CRX using the command line or start/stop scripts as described earlier in this document.

#### My application running on CRX throws out-of-memory errors

>[!NOTE]
>
><p>See also <a href="/content/help/en/experience-manager/kb/AnalyzeMemoryProblems.html">Analyze Memory Problems</a>.</p>

My application running on CRX throws out-of-memory errors

CRX itself has a very low memory footprint. If the application running within CRX has bigger memory requirements or requests memory-heavy operations (for example, large transactions), the JVM instance where CRX runs needs to be started with appropriate memory settings.

Use Java command options to define memory settings of the JVM (for example, java -Xmx512m -jar crx*.jar to set heapsize to 512MB).

Specify the memory setting option while starting AEM WCM from the command line. The AEM WCM start/stop scripts or custom scripts for managing AEM WCM startup can also be modified to define the required memory settings.

If you have already defined your heapsize to 512MB, you may want to analyze the memory issue further by creating a heap dump:

To automatically create a heap dump when running out of memory, use the following command:

java -Xmx256m -XX:+HeapDumpOnOutOfMemoryError -jar *.jar

This generates a heap dump file (**java_...hprof**) whenever the process runs out of memory. The process may continue to run after the heap dump was generated. Usually, one heap dump file is enough to analyze the problem.

#### The AEM Welcome screen does not display in the browser after double-clicking AEM Quickstart

In certain situations, the AEM WCM Welcome screens does not automatically display even though the repository itself is successfully running. This may depend on operating system setup, browser configuration, or similar factors.

The usual symptom is that the AEM WCM Quickstart window displays "AEM WCM starting up, waiting for server startup...." If that message displays for a relatively long time, enter the AEM WCM URL into the browser window manually, using the default 4502 port, or the port on which the instance is running: http://localhost:4502/.

Also, logs may reveal the reason for the browser not starting.

Sometimes, the AEM WCM Quickstart window has the message "AEM WCM running on http://localhost:port/" and the browser does not start automatically. In this case, click on the URL in the AEM WCM Quickstart window (it is a hyperlink) or manually enter the URL in the browser.

If everything else fails, check the logs to find out what has happened.

### Troubleshooting Installations with an Application Server

#### Page Not Found returned when requesting a geometrixx-outdoor page

**Applies to WebLogic 10.3.5 and JBoss 5.1**

****When a request to geometrixx-outdoors/en page returns a 404 (Page Not Foun) then you may recheck that you have set the additional sling property in the sling.properties file needed for these specific Application Servers.

See in the *Deploy AEM web application* steps for the details.

#### Response header size can be greater than 4Kb

502 errors can indicate that the web server cannot handle the size of the AEM HTTP response header. AEM can generate HTTP response headers that include include cookies of size greater than 4Kb. Ensure that your servlet container is configured so that the maximum response header size can exceed 4kb.

For example, for Tomcat 7.0, the maxHttpHeaderSize attribute of the [HTTP Connector](http://tomcat.apache.org/tomcat-7.0-doc/config/http.html) controls limitations on header size.

### Uninstalling Adobe Experience Manager

Because AEM installs into a single directory, there is no need for an uninstall utility. Uninstalling can be as simple as deleting the entire installation directory, although how you uninstall AEM depends on what you want to achieve and what persistent storage you use.

If persistent storage is embedded in the installation directory, for example, in the default TarPM installation, deleting folders removes data as well.

>[!NOTE]
>
><p>Adobe highly recommends that you back up your repository before deleting AEM. If you delete the entire &lt;cq-installation-directory&gt;, you will delete the repository. To keep the repository data before deleting, move or copy the &lt;cq-installation-directory&gt;/crx-quickstart/repository folder somewhere else before deleting the other folders.</p>

If your installation of AEM uses external storage, for example, a database server, removing folder does not remove the data automatically, but it does remove the storage configuration, which makes restoring the JCR content difficult.

#### JSP files are not compiled on JBoss

If you install or update JSP files to Experience Manager on JBoss and the corresponding servlets are not compiled, ensure the JBoss JSP compiler is correclty configured. For information, see the  [JSP Compilation Issues in JBoss](/content/help/en/experience-manager/kb/jsps-dont-compile-jboss) article.