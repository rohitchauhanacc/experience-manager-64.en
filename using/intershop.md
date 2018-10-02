---
uuid: d44b9195-941c-42dd-9f8f-9571b355c4e7
index: y
internal: n
snippet: y
translate: y
---

# Intershop

>[!NOTE]
>
><p>This page contains links to the&nbsp;<a href="http://www.intershop.com/">Intershop website</a>. Certain areas need an account for full access.</p>

---

## Deploying eCommerce with Intershop

Deploying the necessary eCommerce packages provides the full functionality of the eCommerce framework, together with a reference implementation of eCommerce functionality as provided with Intershop implementation (including a demonstration catalog).

This catalog is available under the English (US) branch ( `/content/geometrixx-outdoors/en_US`) of the Geometrixx Outdoors site.

### Technical Requirements

This document applies to both Intershop 7.4 and Intershop 7.4 CI (Continuous Integration).

### Setup Geometrixx in Intershop 7

This procedure will initialize the Intershop system with a Geometrixx organization to work with the AEM reference implementation.

>[!CAUTION]
>
><p>The three following Intershop 7 cartridges must have been successfully deployed on the Intershop instance:</p> <ul> <li><span class="code">adobe_app_sf_rest</span></li> <li><span class="code">adobe_app_bo_ch_sales</span></li> <li><span class="code">adobe_init</span></li> </ul>

A database initialization needs to be performed on `adobe_init`. To do that:

1. Add the cartridge to the `dbinit` section of the `cartridgelist.properties`.

1. Open an ANT build shell.

1. Type:

   ```shell
   dbinit -t=adobe_init -!
   ```

1. Login to the new Geometrixx organization:

    * **Login**: `admin`    
    * **Password**: `intershop7`    
    * **Organization**: `Geometrixx`

>[!NOTE]
>
><p>See the <a href="https://support.intershop.com/kb/index.php">Intershop Knowledge Base</a> for more information.</p>

### Installation of eCommerce with Intershop

To install AEM with an Intershop integration configuration (using the demonstration catalog, Geometrixx Outdoors), the basic steps are:

1. [Install AEM](deploy.md).

1. Install the demonstration content packages using the [Package Manager](/content/help/en/experience-manager/6-4/sites/administering/using/package-manager).

   >[!NOTE]
   >
   ><p>Packages are available on demand. To be able to find and download them, please&nbsp;<a href="http://www.intershop.com/contact">contact Intershop</a>.</p> 

1. [Author](/content/help/en/experience-manager/6-4/sites/authoring/using/page-authoring) any supplementary pages that you need in AEM.

Configure the Intershop REST Client:

1. Navigate to [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).

1. Open `Intershop REST Client`.

1. Update the properties to point to the Intershop instance.
   ![](assets/chlimage_1.png)

>[!CAUTION]
>
><p>Use of the Intershop server requires a separate Intershop license.</p> 