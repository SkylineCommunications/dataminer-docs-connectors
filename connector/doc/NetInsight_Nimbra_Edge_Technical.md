---
uid: Connector_help_NetInsight_Nimbra_Edge_Technical
---

# NetInsight Nimbra Edge

## About

The **NetInsight Nimbra Edge** connector integrates the Nimbra Edge platform with the DataMiner System, enabling operators to monitor and control video delivery workflows over the internet. It supports dynamic discovery and management of appliances, inputs/outputs, and group assignments, as well as flow visualization.

This connector uses RESTful HTTP(S) APIs for communication and supports inter-application interactions through FLE (Flow Logic Engine).

It includes the following features:

- Discovery and real-time monitoring of:
  - Appliances
  - Inputs and outputs (UDP, RIST, RTP, RTMP, ZIXI, SRT)
  - TS and TR 101 290 metrics
  - Ports, Services, Users, Regions
- Group Assignment functionality
- Flow Engineering interface with provisioned/incoming/outgoing flow topology
- Create/Edit/Delete inputs and outputs via context menus or Automation scripts
- Alarm monitoring with duplicate filtering
- Login handling via token-based authentication

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *80*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

## Initialization

When you have created the element, fill in the following parameters:

- **API Username**: The username for accessing the Nimbra Edge API.
- **API Password**: The password associated with the API user.

When you have entered these credentials, click the **Login** button to authenticate.

The **API Login Status** parameter will confirm if the login succeeded.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

This connector uses the HTTP RESTful API to communicate with the device/platform. The traffic can be seen in the **Stream Viewer**.

The **General** page shows an overview of the system in a tree view. The root nodes display the appliances. By expanding an appliance, you can drill down to its inputs and outputs.

More detailed information on all the components in the system can be found on the various pages that are implemented in the connector.

## Notes

Inputs, Outputs and Alarms display keys are customizable via the drop down on that page.
