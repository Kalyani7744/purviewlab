# Module 03 - Search & Browse

## Introduction

Once sources have been registered and scanned, the underlying data catalog will begin to populate with assets that represent real-world objects (e.g. a table in an Azure SQL Database, a Power BI report, etc.) The surfacing of these assets via Microsoft Purview's search experience helps empower data consumers to find data assets that matters to them.

In this module, you'll learn to edit technical metadata by adding definitions and classifications to data attributes, such as tables and columns. You'll learn to assign technical ownership by linking technical attributes to contact persons. You'll learn to use classifications to mark data. All these activities, such as categorizing data, will help you to better manage your data

## Objectives

* Search the catalog by keyword.
* Browse the catalog by source.
* Update an existing asset.
* Perform a bulk edit operation.

## Table of Contents

1. [Search Catalog](#1-search-catalog)
2. [Update an Asset](#2-update-an-asset)
3. [Browse Assets](#3-browse-assets)
4. [Bulk Edit](#4-bulk-edit)

## 1. Search Catalog

1. Open the **Microsoft Purview Governance Portal**, navigate to **Data Catalog** > **Home**, type the asterisk character (**\***) into the search bar, and hit **Enter**.

    ![Search Wildcard](../images/module03/lab2-purview05.png)

2. Filter the search results by **Classification** (e.g. **Country/Region**) and click the hyperlinked asset name to view the details (e.g. `QueriesByState`).

    ![Filter by Classification](../images/module03/lab3-purview01.png)


> **Did you know?**
>
> While the **Microsoft Purview Governance Portal** is provided as the default user experience, customers and partners can interface with the underlying platform using the [Microsoft Purview REST API](https://docs.microsoft.com/rest/api/purview/). The openness of the platform enables the possibility of integrating Microsoft Purview with custom user interfaces as well as the ability to perform read/write operations programmatically.

## 2. Update an Asset

1. Click **Edit** to modify the asset details.

    ![Edit Asset](../images/module03/lab3-purview02.png)

2. Update the **Description** by copying and pasting the sample text below.

    ```
    This dataset was curated from the Bing search logs (desktop users only) over the period of Jan 1st, 2020 – (Current Month - 1). Only searches that were issued many times by multiple users were included. The dataset includes queries from all over the world that had an intent related to the Coronavirus or Covid-19. In some cases this intent is explicit in the query itself (e.g., “Coronavirus updates Seattle”), in other cases it is implicit , e.g. “Shelter in place”
    ```

    ![Update Description](../images/module03/lab3-purview03.png)

3. Assign a **Classification** named **World Cities** using the drop-down menu.

    ![Update Classification](../images/module03/m3tsk2stp3.png)

4. Navigate to the **Schema** tab and update the **Asset description** for each column using the sample text below.

    > **Did you know?**
    >
    > **Classifications** and **Glossary Terms** can be assigned at the asset level (e.g. a Table within a Database) as well as at the schema level (e.g. a Column within a Table Schema).

    ![Update Schema](../images/module03/m3tsk2stp4.png)

    **Date**
    ```
    Date on which the query was issued.
    ```
    **Query**
    ```
    The actual search query issued by user(s).
    ```
    **IsImplicitIntent**
    ```
    True if query did not mention covid or coronavirus or sarsncov2 (e.g, “Shelter in place”). False otherwise.
    ```
    **State**
    ```
    State from where the query was issued.
    ```
    **Country**
    ```
    Country from where the query was issued.
    ```
    **PopularityScore**
    ```
    Value between 1 and 100 inclusive. 1 indicates least popular query on the day/State/Country with Coronavirus intent, and 100 indicates the most popular query for the same geography on the same day.
    ```

5. Navigate to the **Contacts** tab and set the user named **odl_user <inject key="DeploymentID" enableCopy="false" />** to be an **Expert** and an **Owner**. Click **Save**.

    > **Did you know?**
    >
    > Assets can be related to two different types of contacts. **Experts** are often business process or subject matter experts. Where as **Owners** are often senior executives or business area owners that define governance or business processes over certain data areas.
    >
    > For assets in which you are tagged as a **Contact**, these will appear on the home screen (Data catalog), under **My items**.

    ![Update Contacts](../images/module03/prv26.png)

6. To see other assets within the same path, navigate to the **Related** tab.

    ![Related Assets](../images/module03/m3tsk2stp6.png)

## 3. Browse Assets

While the search experience is ideal for keyword based discovery, Purview Studio allows alternate methods of browsing assets (i.e. by collection OR by source type).

1. Open the **Microsoft Purview Governance Portal**, navigate to **Data Catalog** and click **Browse Assets**.

    ![Browse Assets](../images/module03/lab3-purview04.png)

2. Switch to the **By source type** tab and select a **source** `Azure Data Lake Storage Gen2`.

    ![ADLS Gen2](../images/module03/lab3-purview05.png)

3. Select an **account** named `pvlab{randomId}adls`.

    ![ADLS Gen2 Account](../images/module03/lab3-purview06.png)

4. Select a **container** with the name `raw`.

    ![ADLS Gen2 Container](../images/module03/lab3-purview07.png)

## 4. Bulk Edit

Microsoft Purview allows us to perform certain operations (add/replace/remove) against a subset of attributes (Expert, Owner, Term, Classification) in bulk directly within Purview Studio.


1. Open the **Microsoft Purview Governance Portal**, navigate to **Data Catalog** > **Home**, type the asterisk character (**\***) into the search bar, and hit **Enter**.

    ![Search Wildcard](../images/module03/lab3-purview04.png)

2. Hover your mouse over an item in the list to reveal the checkbox on the right-hand side. Select five items and click **View selected**.

    ![View Selected](../images/module03/m3tsk4stp2.png)

3. Click **Bulk edit**.

    ![Bulk Edit](../images/module03/m3-t4-step3.png)

4. Set the **Attribute** to `Owner`, set **Operation** to `Add`, select the user named **ODL_User <inject key="DeploymentID" enableCopy="false" />** , and click **Apply**.
 
    ![Apply Changes](../images/module03/03.15-bulk-apply.1.png)

5. Click **Deselect all and close**.

    ![Deselect](../images/module03/m3-t4-step5.png)

## Knowledge Check

[https://aka.ms/purviewlab/q03](https://aka.ms/purviewlab/q03)

1. There are a number of **attributes** that we can use to narrow our search results via the **filter pane**, which of the following is **not** available as a quick filter?

    A ) Source Type  
    B ) Classification  
    C ) Size  

2. Using the Microsoft Purview Governance Portal (UI), you can edit an asset and manually update an assets **Description**?

    A ) True  
    B ) False  

3. Using the Microsoft Purview Governance Portal (UI), you can edit an asset and manually add and remove **Classifications**?

    A ) True  
    B ) False  

4. Using the Microsoft Purview Governance Portal (UI), you can edit an asset and manually update an assets **Technical Properties** (e.g. qualifiedName, partitionCount, totalSizeBytes, etc)?

    A ) True  
    B ) False  

5. Assets in the catalog can be assigned contacts, which of the following is an **invalid contact type**?

    A ) Expert  
    B ) Owner  
    C ) Reader  
    
## Summary

This module provided an overview of how to search, browse, and update assets.
