---
uid: Connector_help_Sony_CNA-2
---

# Sony CNA-2

Sony CNA-2 is a camera control network adaptor that is able to monitor, configure and control your Sony system cameras anywhere with Network. 
It is able to run productions to get the most out of your system cameras and visualize grouping functions and settings for SR-Live and Networked Live.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>System Camera management</li><li>Webhook listening capabilities</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |v1.0820        |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *443*)]
  - **Device address**: [The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.]

### Initialization

In the **Communication Settings** page, you will need to provide a username and a password to login in to the device.

#### Webhook Listener

This connector uses a HTTP listener and requires the following configuration inside the element:

WEBHOOK LISTENER:

  - **Webhook IP**: [The IP where the webhooks will be listened.]
  - **Webhook port**: [The port where the webhooks will be listened. (default: *50000*, needs to be opened in the firewall)]

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

This connector uses REST API calls to communicate with the device.

It has two communication modes, GMCS and MCS. 
In GMCS mode, you can configure up to 10 different domains with 3 tables each, one for CCU device information, one for CCU Assignment information, and one for RCP Assignment information.
The domains can be enabled/disabled in the *GMCS Communication Settings* table in the **Communication Settings** page.
This will also impact if that domain is polled and displayed or not.

When in MCS mode, you will only have access to one domain with the same 3 tables.

For both modes, a matrix for CCU Assignments and another for RCP Assignments is available.

The Webhook communication is responsible for receiving updates on connections made, so it is important to make sure that you provide valid Webhook connection parameters.
An incorrect configuration will lead to tables and matrices only being updated every 15 minutes.
Please also make sure that the Webhook port is opened in the Firewall. If not, no Webhook communication will be received.