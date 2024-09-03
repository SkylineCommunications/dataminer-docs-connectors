---
uid: Connector_help_TDF_Helios_Database_-_Operator
---

# TDF Helios Database - Operator

This connector is a child connector of the [TDF Helios Database](xref:Connector_help_TDF_Helios_Database) connector. It is used to control the automatic provisioning done for each operator.

## Configuration

The element using this connector is automatically created by the parent connector.

### Filter configuration

Assuming everything was correctly assigned in the parent element, the only configuration needed within the element is on the **Filters** page. On that page, you can define four types of filters: **Item de Catalogue**, **Site Code**, **Service Client Code**, and **PNO Code**. Note that all these fields are columns in the Queries tables of the parent element.

To add a filter, fill in the **Register New Item** parameter for the specific type. Once you have added the filter, the item will appear in the respective **Registry** Table.

To enable or disable a filter based on the **Registry** table, the **State** parameter needs to be defined accordingly.

The combination of filters will be evaluated using an OR condition.

### View configuration

Before you use the element, make sure the DMS has the following static views structure:

- TDF

  - 01 - TNT

    - 01 - Métropole

      - **Departments Views** with the following names :"01", "02", "03", "04", "05", "06", "07", "08", "09", "10", "11", "12", "13", "14", "15", "16", "17", "18", "19", "21", "22", "23", "24", "25", "26", "27", "28", "29", "30", "31", "32", "33", "34", "35", "36", "37", "38", "39", "40", "41", "42", "43", "44", "45", "46", "47", "48", "49", "50", "51", "52", "53", "54", "55", "56", "57", "58", "59", "60", "61", "62", "63", "64", "65", "66", "67", "68", "69", "70", "71", "72", "73", "74", "75", "76", "77", "78", "79", "80", "81", "82", "83", "84", "85", "86", "87", "88", "89", "90", "91", "92", "93", "94", "95", "2A", "2B".

    - 02 - Outremer

      - **Departments Views** with the following names: "971", "972", "973", "974", "975", "985", "986", "987", "988".

    - 03 -Sites Tiers

  - 02 - France 3

    - 01 - F3 CAT

      - F3 CAT-Elements

    - 02 - F3 eDLiveR

      - F3 eDliveR-Elements

    - 03 - F3 FTR VAISE CDE

      - F3 FTR VAISE CDE-Elements

  - 98 - Common

  - 99 - Skyline

### Property configuration

Before you use the element, make sure that at least one element in the system has the **Addresse IP** custom property filled.

## How to use

When you have defined the filters, you can use the pages **Views & Services Provisioning** and **Elements Provisioning** to provision the views and services and to provision the elements to be added to those view and services, respectively.

Click the **Refresh** button to make the connector read all the information present in the queries tables and filter it with the defined filters. In the **Unstaged Changes** tables, you will then see the creation/update changes that are present in the tables related to the actual views, services, and elements present in the DMS.

Based on these unstaged changes, you can select a few or all the changes to be staged by clicking the button **Stage** or **Stage all Changes**. The changes will then pass to the **Staged Changes** table. Click **Apply Changes** to create or update the views, services, or elements accordingly.

All the views, services, and elements that have been created or updated will be shown on the **Statistics** page.

## Notes

When no filter is defined, refreshing the **Unstaged Changes** tables can take a long time. We therefore recommend that you always add filters before starting the refresh.

You can cancel the refreshing of the **Unstaged Changes** table at any moment with the **Cancel** button.
