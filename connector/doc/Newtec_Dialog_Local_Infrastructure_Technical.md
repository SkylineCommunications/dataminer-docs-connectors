---
uid: Connector_help_Newtec_Dialog_Local_Infrastructure_Technical
---

# Newtec Dialog Local Infrastructure

Newtec Dialog Local Infrastructure is software that monitors numerous PDU device parameters of a network.

This connector allows you to monitor PDU devices on different hosts. It uses the Zabbix API and HTTP polling to quickly get the latest information from the device. The Zabbix API is a web-based API that is shipped as part of the web frontend. It uses the JSON-RPC 2.0 protocol. This connector will export different connectors based on the retrieved hosts from the API. For more information on the device, refer to <https://www.zabbix.com/documentation/3.0/manual/api>.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

To be able to retrieve data from the API, specify a **Username** and **Password** on the **Authentication** page.

## How to use

The **Configure DVEs** page button opens a subpage where DVEs can be configured.

On the **General** page, the **API Endpoint/URL** needed to connect to the device can be configured. On the **Authentication** page, you can set the **Username** and **Password** that are used to retrieve data from the API.

To activate the PDU tracking, the only host group that needs to be enabled is the "pdu" host group. You can find this on the **Hosts** page in the **Hosts Group** table.
