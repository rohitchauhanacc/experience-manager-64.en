---
title: Rich Text Editor
seo-title: Rich Text Editor
description: The Rich Text Editor is a basic building block for inputting textual content into AEM.
seo-description: The Rich Text Editor is a basic building block for inputting textual content into AEM.
uuid: 42001071-f7a7-475d-8aab-a8054303db68
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: adc697e1-4a1c-4985-8690-79ed77736fec
exl-id: 44cd0092-de40-4a72-a682-1e8f5906b2e5
---
# Rich Text Editor{#rich-text-editor}

The Rich Text Editor is a basic building block for inputting textual content into AEM. It forms the basis of various components, including:

* Text
* Text Image
* Table

## Rich Text Editor {#rich-text-editor-2}

The WYSIWYG editing dialog provides a wide range of functionality:

![cq55_rte_basicchars](assets/cq55_rte_basicchars.png)

>[!NOTE]
>
>The features available can be configured for individual projects, so might vary for your installation.

## In-Place Editing {#in-place-editing}

In addition to the dialog based Rich Text Editing mode, AEM also provides the in-place editing mode, which allows direct editing of the text as it is displayed in the layout of the page.

Click twice on a paragraph (a slow double-click) to enter the inplace editing mode (the component border will now be orange).

You will be able to directly edit the text on the page, instead of inside a dialog window. Just make your changes and they will be automatically saved.

![cq55_rte_inlineediting](assets/cq55_rte_inlineediting.png)

>[!NOTE]
>
>If you have the content finder open, a toolbar with the RTE formatting options will be shown at the top of the tab (as above).
>
>If the content finder is not open then the toolbar will not be shown.

Currently, the Inplace Editing mode is enabled for page elements generated by the **Text** and **Title** components.

>[!NOTE]
>
>The **Title** component is designed to contain a short text without linebreaks. When editing a title in Inplace Editing Mode, entering a linebreak will open a new **Text** component below the title.

## Features of the Rich Text Editor {#features-of-the-rich-text-editor}

The Rich Text Editor provides a range of featues, these [depend on the configuration](/help/sites-administering/rich-text-editor.md) of the individual component. The features are available for both the touch-optimized and classic UI.

### Basic Character Formats {#basic-character-formats}

![](do-not-localize/cq55_rte_basicchars.png)

Here you can apply formatting to characters you have selected (highlighted); some options also have short-cut keys:

* Bold (Ctrl-B)  
* Italic (Ctrl-I)  
* Underline (Ctrl-U)  
* Subscript
* Superscript

![cq55_rte_basicchars_use](assets/cq55_rte_basicchars_use.png)

All operate as a toggle, so reselection will remove the format.

### Predefined Styles and Formats {#predefined-styles-and-formats}

![cq55_rte_stylesparagraph](assets/cq55_rte_stylesparagraph.png)

Your installation can include predefined styles and formats. These are available with the **Style** and **Format** drop down lists and can be applied to text that you have selected.

A style can be applied to a specific string (a style correlates to CSS):

![cq55_rte_styles_use](assets/cq55_rte_styles_use.png)

Whereas a format is applied to the entire text paragraph (a format is HTML-based):

![cq55_rte_paragraph_use](assets/cq55_rte_paragraph_use.png)

A specific format can only be changed (the default is **Paragraph**).

A style can be removed; place the cursor within the text to which the style has been applied and click on the remove icon:

>[!CAUTION]
>
>Do not actually reselect any of the text to which the style has been applied or the icon will be deactivated.

### Cut, Copy, Paste {#cut-copy-paste}

![](do-not-localize/cq55_rte_cutcopypaste.png)

The standard functions of **Cut** and **Copy** are available. Several flavors of **Paste** are provided to cater for differing formats.

* Cut (**Ctrl-X**)
* Copy (**Ctrl-C**)
* Paste 

  This is the default paste mechanism (**Ctrl-V**) for the component; when installed out-of-the-box this is configured to be "Paste from Word".  

* Paste as Text 

  Strips all styles and formatting to paste only the plain text.  

* Paste from Word 

  This pastes the content as HTML (with some necessary reformatting).

### Undo, Redo {#undo-redo}

![](do-not-localize/cq55_rte_undoredo.png)

AEM keeps a record of your last 50 actions in the current component, held in chronological order. These actions can be undone (and then redone) in strict order, if required.

>[!CAUTION]
>
>The history is only held for the current edit session. It is restarted each time you open the component for editing.

>[!NOTE]
>
>Fifty is the default number of tasks. This may be different for your installation.

### Alignment {#alignment}

![](do-not-localize/cq55_rte_alignment.png)

Your text can be either left, center or right aligned.

![cq55_rte_alignment_use](assets/cq55_rte_alignment_use.png) 

### Indentation {#indentation}

![](do-not-localize/cq55_rte_indent.png)

The indentation of a paragraph can be increased, or decreased. The selected paragraph will be indented, any new text entered will retain the current level of indentation.

![cq55_rte_indent_use](assets/cq55_rte_indent_use.png) 

### Lists {#lists}

![](do-not-localize/cq55_rte_lists.png)

Both bulleted and numbered lists can be created within your text. Either select the list type and start typing or highlight the text to be converted. In both cases a line-feed will start a new list item.

Nested lists can be achieved by indenting one or more list items.

The style of a list can be changed by simply positioning the cursor within the list, then selecting the other style. A sublist can also have a different style to the containing list. This can be applied once the sublist has been created (by indentation).

![cq55_rte_lists_use](assets/cq55_rte_lists_use.png) 

### Links {#links}

![](do-not-localize/cq55_rte_links.png)

A link to an URL (either within your website or an external location) is generated by highlighting the required text then clicking the **Hyperlink** icon:

![](do-not-localize/chlimage_1-12.png)

A dialog will allow you to specify the target URL; also whether it should be opened in a new window.

![cq55_rte_link_use](assets/cq55_rte_link_use.png)

You can:

* type in a URI directly  
* use the site map to select a page within your website
* enter the URI, then append the target anchor; e.g. `www.TargetUri.org#AnchorName`
* enter an anchor only (to reference "the current page"); e.g. `#anchor`
* search for a page in the content finder, then drag and drop the page icon into the Hyperlink dialog

>[!NOTE]
>
>The URI can be prepended with any of the protocols configured for your installation. In a standard installation these are `https://`, `ftp://`, and `mailto:`. Protocols not configured for your installation will be rejected and marked as invalid.
>

To break the link position the cursor anywhere within the link text and click the **Unlink** icon:

![](do-not-localize/chlimage_1-13.png) 

### Anchors {#anchors}

![](do-not-localize/cq55_rte_anchor.png)

An anchor can be created anywhere within the text by either positioning the cursor, or selecting some text. Then click on the **Anchor** icon to open the dialog.

Enter the name of the anchor then click **OK** to save.

![cq55_rte_anchor_use](assets/cq55_rte_anchor_use.png)

The anchor is shown when the component is being edited and can now be used within a target for links.

![chlimage_1-145](assets/chlimage_1-145.png) 

### Find and Replace {#find-and-replace}

![](do-not-localize/cq55_rte_findreplace.png)

AEM provides both a **Find** and a **Replace** (find and replace) function.

Both have a **Find next** button to search the open component for the text specified. You can also specify whether you need the case (upper/lower) to be matched.

The search will always start from the current cursor position within the text. When the end of the component is reached a message will inform you that the next search operation will start from the top.

![cq55_rte_find_use](assets/cq55_rte_find_use.png)

The **Replace** option allows you to **Find**, then **Replace** an individual instance with the specified text, or to **Replace all** instances in the current component.

![cq55_rte_findreplace_use](assets/cq55_rte_findreplace_use.png) 

### Images {#images}

Images can be dragged from the content finder to add them to the text.

![cq55_rte_image_use](assets/cq55_rte_image_use.png)

>[!NOTE]
>
>AEM also offers specialized components for more detailed image configuration. For example the **Image** and **Text Image** components are available.

### Spelling Checker {#spelling-checker}

![](do-not-localize/cq55_rte_spellchecker.png)

The spelling checker will check all the text in the current component.

Any incorrect spellings will be highlighted:

![cq55_rte_spellchecker_use](assets/cq55_rte_spellchecker_use.png)

>[!NOTE]
>
>The spelling checker will operate in the language of the website by taking either the language property of the subtree or extracting the language from the URL. For example the `en` branch will be checked for English and the `de` branch for German.

### Tables {#tables}

Tables are available both:

* As the **Table** component

  ![chlimage_1-146](assets/chlimage_1-146.png)

* From within the **Text** component

  ![](do-not-localize/chlimage_1-14.png)

  >[!NOTE]
  >
  >Although tables are available in the RTE, it is recommended to use the **Table** component when creating tables.

In both the **Text** and **Table** components table functionality is available via the context menu (usually the right-mouse-button) clicked within the table; for example:

![cq55_rte_tablemenu](assets/cq55_rte_tablemenu.png)

>[!NOTE]
>
>In the **Table** component, a specialized toolbar is also available, including various standard rich text editor functions, together with a subset of the table-specific functions.

The table specific functions are:

<table> 
 <tbody> 
  <tr> 
   <td><a href="#table-properties">Table Properties</a><br /> </td> 
  </tr> 
  <tr> 
   <td><a href="#cell-properties">Cell Properties<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#add-or-delete-rows">Add or Delete Rows<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#add-or-delete-columns">Add or Delete Columns<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#selecting-entire-rows-or-columns">Selecting Entire Rows or Columns<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#merge-cells">Merge Cells<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#split-cells">Split Cells<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#creating-nested-tables">Nested Tables</a></td> 
  </tr> 
  <tr> 
   <td><a href="#remove-table">Remove Table</a> </td> 
  </tr> 
 </tbody> 
</table>

#### Table Properties {#table-properties}

![cq55_rte_tableproperties_icon](assets/cq55_rte_tableproperties_icon.png)

The basic properties of the table can be configured, before clicking **OK** to save:

![cq55_rte_tableproperties_dialog](assets/cq55_rte_tableproperties_dialog.png)

* **Width** 

  The total width of the table.  

* **Height** 

  The total height of the table.  

* **Border** 

  The size of the table border.  

* **Cell padding** 

  This defines the white space between the cell content and its borders.  

* **Cell spacing** 

  This defines the distance between the cells.

>[!NOTE]
>
>**Width**, **Height** and certain cell properties can be defined in either:  
>
>* pixels  
>* percentages

>[!CAUTION]
>
>Adobe strongly recommends that you define a **Width** for your table.

#### Cell Properties {#cell-properties}

![cq55_rte_cellproperties_icon](assets/cq55_rte_cellproperties_icon.png)

The properties of a specific cell, or series of cells, can be configured:

![cq55_rte_cellproperties_dialog](assets/cq55_rte_cellproperties_dialog.png)

* **Width** 
* **Height** 
* **Horizontal Align** - Left, Center or Right  
* **Vertical Align** - Top, Middle, Bottom or Baseline  
* **Cell type** - Data or Header  
* **Apply to:**
    * Single cell
    * Entire row
    * Entire column

#### Add or Delete Rows {#add-or-delete-rows}

![cq55_rte_rows](assets/cq55_rte_rows.png)

Rows can be added either above or below the current row.

The current row can also be deleted.

#### Add or Delete Columns {#add-or-delete-columns}

![cq55_rte_columns](assets/cq55_rte_columns.png)

Columns can be added either to the left or right of the current column.

The current column can also be deleted.

#### Selecting Entire Rows or Columns {#selecting-entire-rows-or-columns}

![chlimage_1-147](assets/chlimage_1-147.png)

Selects the entire current row or column. Specific actions (e.g. merge) are then available.

#### Merge Cells {#merge-cells}

![cq55_rte_cellmerge](assets/cq55_rte_cellmerge.png) ![cq55_rte_cellmerge-1](assets/cq55_rte_cellmerge-1.png)

* If you have selected a group of cells you can merge these into one.
* If you have have only one cell selected then you can merge it with the cell to either the right or below.

#### Split Cells {#split-cells}

![cq55_rte_cellsplit](assets/cq55_rte_cellsplit.png)

Select a single cell to split it:

* Splitting a cell horizontally will generate a new cell to the right of the current cell, within the current column.
* Splitting a cell vertically will generate a new cell underneath the current cell, but within the current row.

#### Creating Nested Tables {#creating-nested-tables}

![chlimage_1-148](assets/chlimage_1-148.png)

Creating a nested table will create a new, self-contained table within the current cell.

>[!NOTE]
>
>Certain additional behavior is browser dependent:
>
>* Windows IE: Use Ctrl+primary-mouse-button-click (usually left) to select multiple cells.
>* Firefox: Drag the mouse to select a cell range.
>

#### Remove Table {#remove-table}

![cq55_rte_removetable](assets/cq55_rte_removetable.png)

This will remove the table from within the **Text** component.

### Special Characters {#special-characters}

![](do-not-localize/cq55_rte_specialchars.png)

Special characters can be made available to your rich text editor; these might vary according to your installation.

![cq55_rte_specialchars_use](assets/cq55_rte_specialchars_use.png)

Use mouseover to see a magnified version of the character, then click for it to be included at the current location in your text.

### Source Editing Mode {#source-editing-mode}

![](do-not-localize/cq55_rte_sourceedit.png)

The source editing mode allows you to see and edit the underlying HTML of the component.

So the text:

![cq55_rte_sourcemode_1](assets/cq55_rte_sourcemode_1.png)

Will looks as follows in source mode (often the source is much longer, so you will have to scroll):

![cq55_rte_sourcemode_2](assets/cq55_rte_sourcemode_2.png)

>[!CAUTION]
>
>When leaving source mode, AEM makes certain validation checks (for example, ensuring that the text is correctly contained/nested in blocks). This can result in changes to your edits.
