---
uid: Connector_help_ServiceNow_Incident_Manager_Technical
---

# ServiceNow Incident Manager

## About

The **ServiceNow Incident Manager** connector acts as a bridge between the internal ticketing application and ServiceNow.  
It automatically creates incidents in ServiceNow whenever new tickets are generated in the ticketing system and keeps both platforms synchronized by applying updates made on the ServiceNow side back to the ticketing application.  

This ensures a consistent and up-to-date view of all incidents across both systems, without requiring manual intervention.

## Configuration

### Connections

#### HTTP Connection – Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The ServiceNow incident table endpoint URL (e.g. `https://{instance}.service-now.com/api/now/table/incident`).
- **IP port**: The port of the destination (e.g. `443`).

### Initialization

After configuring the ServiceNow incident table URL, the following parameters must be set on the **General** page:

- **User Name** – The ServiceNow user name associated with the instance  
- **Password** – The corresponding password for the ServiceNow user

## How to Use

**Configure the Connection**  
   Ensure the HTTP connection is correctly set up with the ServiceNow instance URL, user name, and password.  
   Once configured, the connector will automatically authenticate with ServiceNow.

**Automatic Ticket Creation**  
   When a new ticket is created in the internal ticketing application, the connector automatically sends the corresponding incident data to ServiceNow.  
   A new record will appear in the *Incident Table* of your ServiceNow instance.

**Automatic Ticket Updates**  
   If an incident is updated in ServiceNow (for example, its state or priority), the connector detects these updates and applies them back to the internal ticketing system.

**Alarm Property Synchronization**  
   To ensure alarm details are properly tracked, make sure the following properties exist in your system:  
       - **Incident Status**
       - **Incident Number**

   These fields are automatically updated by the connector based on changes from ServiceNow.
