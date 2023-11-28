---
uid: Connector_help_TDF_Helios_Database_-_Operator
---

# TDF Helios Database - Operator

This connector is a child connector of the [TDF Helios Database](xref:Connector_help_TDF_Helios_Database) connector. It is used to control the automatic provisioning done for each operator.

## Configuration

The element using this connector is automatically created by the parent connector.

Assuming everything was correctly assigned in the parent element, the only configuration needed is on the **Filters** page. On that page, you can define four types of filters: **Item de Catalogue**, **Site Code**, **Service Client Code**, and **PNO Code**. Note that all these fields are columns in the Queries tables of the parent element.

To add a filter, fill in the **Register New Item** parameter for the specific type. Once you have added the filter, the item will appear in the respective **Registry** Table.

To enable or disable a filter based on the **Registry** table, the **State** parameter needs to be defined accordingly.

The combination of filters will be evaluated using an OR condition.

## How to use

When you have defined the filters, you can use the pages **Views & Services Provisioning** and **Elements Provisioning** to provision the views and services and to provision the elements to be added to those view and services, respectively.

Click the **Refresh** button to make the connector read all the information present in the queries tables and filter it with the defined filters. In the **Unstaged Changes** tables, you will then see the creation/update changes that are present in the tables related to the actual views, services, and elements present in the DMS.

Based on these unstaged changes, you can select a few or all the changes to be staged by clicking the button **Stage** or **Stage all Changes**. The changes will then pass to the **Staged Changes** table. Click **Apply Changes** to create or update the views, services, or elements accordingly.

All the views, services, and elements that have been created or updated will be shown on the **Statistics** page.

## Notes

When no filter is defined, refreshing the **Unstaged Changes** tables can take a long time. We therefore recommend that you always add filters before starting the refresh.

You can cancel the refreshing of the **Unstaged Changes** table at any moment with the **Cancel** button.
