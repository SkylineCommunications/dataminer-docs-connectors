---
uid: Connector_help_ServiceNow_Incident_Manager_Technical
---

# ServiceNow Incident Manager

## About

The **ServiceNow Incident Manager** connector acts as a bridge between the internal ticketing application and ServiceNow. It automatically creates incidents in ServiceNow whenever new tickets are generated in the ticketing system and keeps both platforms synchronized by applying updates made on the ServiceNow side back to the ticketing application.

This ensures a consistent and up-to-date view of all incidents across both systems, without requiring manual intervention.

## Configuration

### Connections

#### HTTP Connection – Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The ServiceNow incident table endpoint URL (e.g. `https://{instance}.service-now.com/api/now/table/incident`).
- **IP port**: The port of the destination (e.g. *443*).

### Initialization

After creating the element, open the **General** page and configure the **Authentication Approach** parameter. Depending on the selected option, an additional page will become available:

- **For Basic Authentication**, provide the ServiceNow **User Name** and **Password**.
- **For API Key Authentication**, enter the API Key.

### Required Properties

To make sure that incident details are correctly reflected in alarms, make sure the following properties exist in the system:

- Incident Status
- Incident Number
- Ticket ID

These fields will be automatically updated by the connector whenever necessary.

## How to Use

Once the connector has been correctly configured, it will automatically authenticate with ServiceNow.

When a new ticket is created in the internal ticketing application, the connector will automatically send the corresponding incident data to ServiceNow. A new record will appear in the **Incident Table** of your ServiceNow instance.

If an incident is updated in ServiceNow (for example, its state or priority), the connector will detect these updates and apply them back to the internal ticketing system.
