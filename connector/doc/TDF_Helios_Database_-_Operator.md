---
uid: Connector_help_TDF_Helios_Database_-_Operator
---

# TDF Helios Database - Operator
This connector is the child connector of the [TDF Helios Database](xref:Connector_help_TDF_Helios_Database) and as the funtion of control all the automatic provisioning being done for each operator.

## Configuration
 The only configuration needed, assuming everything was correctly assigned on the parent element, is defined on the **Filters** page.
 In this page it is possible to define four types of filters **Item de Catalogue**, **Site Code**, **Service Client Code** and **PNO Code** (all these fields are columns on the Queries tables present on the parent element).
 To add one filter it is needed to fill the **Register New Item** parameter for the specific type, once added the item will appear on the respective **Registry** Table.
 To enable or disable the filter based on the **Registry** table the **State** paremeter needs to be defined accordingly.
 These combination of filters will be then evaluated under an OR condition.
 
## How to use

Once the filters defined we have two pages **Views & Services Provisioning** and **Elements Provisioning**, one to provision the views and services and other to provision the elements to be added to those folders and services.
Once the button **Refresh** is pressed the connector will read all the information present on the queries tables and filter it with the filters previously defined.
It will then show on the **Unstaged Changes** Tables the Creation/Update changes that are present on those tables regarding the actual Views, services and Elements present on the DMS.
Based on these unstaged changes it is possible to select a few or all the changes to be staged simply clicking on the button **Stage** or** Stage all Changes**.
The changes will then pass to the **Staged Changes** table and by pressing the button **Apply Changes**, these Views, Services or Elements will be created or updated accordingly.

All the Views, Services and Element created or updated will be shown on the **Statistics** page.

## Notes
When no filter is defined the refreshing of the **Unstaged Changes** tables can be a process that takes many time , it is advised to always add filters before starting the refresh. 
It is possible to cancel the refreshing of the **Unstaged Changes** Table at any moment pressing the **Cancel** Button.
