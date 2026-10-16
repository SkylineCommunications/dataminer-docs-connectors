---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_Origin_Service_Technical
description: Configure and use the Origin Service connector in DataMiner, including service creation, alarm monitoring, and configuration sharing.
---

# Vodafone Kabel Deutschland GmbH Origin Service

## About

The Vodafone Kabel Deutschland GmbH Origin Service connector is an enhanced service connector that collects service metadata, element status, and active alarms. Its service aggregation use case is *Origin*.

The connector sends aggregated service information to subscribed [Active Service Configuration Platform](xref:Connector_help_Vodafone_Kabel_Deutschland_GmbH_Active_Service_Configuration_Platform) elements.

## Configuration

### Connections

This connector is a service protocol. To create a service using this protocol:

1. In DataMiner Cube, right-click a view in the Surveyor and select **Create service**.
2. Specify the name for the service.
3. Open the advanced options and select *Vodafone Kabel Deutschland GmbH Origin Service* as the service protocol, using the latest or production version.
4. Go to the **parameters** tab and include the elements and services you want to monitor.

### Initialization

For centralized configuration monitoring, the connector discovers elements using the production version of the **Vodafone Kabel Deutschland GmbH Active Service Configuration Platform** connector and registers them in the **Subscribed Manager Table**.

Changes to **DataMiner Service Lifecycle**, **Service CID**, and **Tenant** update the aggregated service information and notify subscribed managers.

## How to Use

### General Page

The **General** page displays the service name and metadata:

- **Service Aggregation Use Case**: Identifies the service as *Origin*.
- **DataMiner Service Lifecycle**: Indicates the service lifecycle status.
- **Service CID**: Identifies the service CID.
- **Tenant**: Identifies the tenant associated with the service.
- **Reservation GUID**: Identifies the associated reservation.

### Service Active Configuration Page

The **Service Active Configuration** page displays the **Aggregated Service JSON**, **Last Service Configuration Update UTC Time**, and **Subscribed Manager Table**.

The aggregated data includes the service use case, element references, service properties, tenant, lifecycle status, and service CID.

To reload service properties and notify subscribed managers, click **Refresh Service Properties**.

### Alarms Page

The **Alarms** page displays **Service Severity** and the **Active Service Alarms** table.

Set **Monitor Active Alarms** to *Enabled* to retrieve and display active alarms.

### Elements Page

The **Elements** page displays the **Service Element Status** table. It lists element names and IDs, element states, alarm severities, parent service information, and alarm counts by severity.

Set **Debug Logging** to *Enabled* to investigate service monitoring and data retrieval.
