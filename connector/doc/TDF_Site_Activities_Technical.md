---
uid: Connector_help_TDF_Site_Activities_Technical
---

# TDF Site Activities

## About

The TDF Site Activities connector integrates with the ServiceNow API to provide real-time visibility into ticketing activities.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP.
- **IP port**: The IP port of the destination.
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

After element creation, configure the following parameters on the **Configuration** page:

- **User Name**: The ServiceNow login username.
- **Password**: The ServiceNow login password (stored as a secure string).
- **Proxy Server**: Optional proxy server address to route requests through.

## How to Use

The connector periodically polls the ServiceNow REST API for each data set. Polling intervals are configured on the **Polling Settings** page.

### Pages

- **Technician Presence on Site**: Displays technician presence records within a rolling 10-hour window. Data is retrieved from the `sn_openframe_time_sheet` ServiceNow table.
- **Incident Tickets**: Displays active incident tickets from the `incident` ServiceNow table. The subpage **Incident Tickets History** shows closed incidents. **Site Incident Overview** provides an aggregated incident count per IG code.
- **Plan Maintenance Tickets**: Shows scheduled maintenance tickets from the `sc_req_item` ServiceNow table within a rolling 10-hour window.
- **Technician Move on Site**: Shows technician move requests from the `u_intervention_step` ServiceNow table within a rolling 10-hour window.
- **Access Requests**: Displays today's access requests from the `sn_customerservice_access_request` ServiceNow table.
- **Site Notes**: Shows operational site notes from the `cmn_location` ServiceNow table.
- **Polling Settings**: Allows you to configure the polling interval and to enable or disable polling for each data set individually.
