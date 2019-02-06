---
title: Editing Launches
seo-title: Editing Launches
description: After creating a launch for your page (or set of pages) you can edit the content in the launch copy of the page(s). 
seo-description: After creating a launch for your page (or set of pages) you can edit the content in the launch copy of the page(s). 
uuid: a4b0c0a8-f37f-4bbd-b942-2020cdc409c1
contentOwner: Alison Heimoz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: c9bf2e83-5602-45cf-9f5d-5f5ab6e300d5
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
index: y
internal: n
snippet: y
---

# Editing Launches{#editing-launches}

## Editing Launch Pages {#editing-launch-pages}

When a launch has been created for a page (or set of pages) you can edit the content in the launch copy of the page(s).

1. Access the [Launch from References (Sites console)](../../../sites/authoring/using/launches.md#launchesinreferencessitesconsole) to show the available actions.
1. Select **Go to the page** to open the page for editing.

### Editing Launch Pages Subject to a Live Copy {#editing-launch-pages-subject-to-a-live-copy}

If your launch is based upon a [live copy](../../../sites/administering/using/msm.md) then you will:

* see lock symbols (small padlocks) when you edit a component (content and/or properties).
* see the **Live Copy** tab in **Page Properties**

A livecopy is used to synchronize content *from* the source branch *to* your launch branch (to keep your launch up-to-date with changes made in the source).

You can make changes in the same way as you can edit a standard live copy; for example:

* Clicking on a closed padlock will break this synchronization and allow you to make new updates to the content in your launch. Once unlocked (open padlock) your changes will not be overwritten by any changes made at the same location within the source branch.
* **Suspend** (and **Resume**) inheritance for a specific page.

See [Changing Live Copy Content](../../../sites/administering/using/msm-livecopy.md#changinglivecopycontent) for further information.

## Comparing a Launch Page to its Source Page {#comparing-a-launch-page-to-its-source-page}

To track the changes you have made, you can view the launch in **References** and compare the launch page with its source page:

1. In the **Sites** console, [navigate to the source page of your launch and select it](../../../sites/authoring/using/basic-handling.md#viewingandselectingyourresources).
1. Open the ** [References](../../../sites/authoring/using/basic-handling.md#references)** panel and select **Launches**.
1. Select your specific launch then **Compare to Source**:

   ![](assets/chlimage_1-118.png)

1. The two pages (launch and source) will be opened side-by-side.

   For full information about using this feature see [Page Diff](../../../sites/authoring/using/page-diff.md).

## Changing the Source Pages Used {#changing-the-source-pages-used}

At any time you can either add or remove pages to/from the range of source pages for a launch:

1. Access and select the launch from either:

    * the [Launches console](../../../sites/authoring/using/launches.md#thelaunchesconsole):

        * Select **Edit**.

    * [References (Sites console)](../../../sites/authoring/using/launches.md#launchesinreferencessitesconsole) to show the available actions:

        * Select **Edit Launch**.

   The source pages will be shown.

1. Make your required changes, then confirm with **Save**.

   >[!NOTE]
   >
   >To add pages to a launch they must be below a common language root; i.e. within a single site.

## Editing a Launch Configuration {#editing-a-launch-configuration}

At any time you can edit the properties for a launch:

1. Access and select the launch from either:

    * the [Launches console](../../../sites/authoring/using/launches.md#thelaunchesconsole):

        * Select **Properties**.

    * [References (Sites console)](../../../sites/authoring/using/launches.md#launchesinreferencessitesconsole) to show the available actions:

        * Select **Edit Properties**.

   The details will be shown.

1. Make your required changes, then confirm with **Save**.

   See [Launches - the Order of Events](../../../sites/authoring/using/launches.md#main-pars-title-6) for information about the purpose and interaction of the **Launch Date** and **Production Ready** fields.

## Discovering the Launch Status of a Page {#discovering-the-launch-status-of-a-page}

The status is shown when you select a specific launch from the references tab (see [Launches in References (Sites Console)](../../../sites/authoring/using/launches.md#launchesinreferencessitesconsole)).

![](assets/chlimage_1-119.png)
