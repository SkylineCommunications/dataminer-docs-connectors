---
uid: Connector_help_SEE_Telecom_eAcsys_2Rx_Us
---

# SEE Telecom eAcsys 2Rx Us

SEE Telecom eAcsys 2Rx Us is a key connector of the Headend used as a HFC Upstream Receiver (Successor of Acsys). The integrated eAcsys platform is used for the segmentation of the CATV network.

## About

SEE Telecom eAcsys 2Rx US contains general data regarding the Unit and that is located on the **General** page of the connector. The user also has access to Optical and Radio-Frequency Module. The Receiver specific KPIs can be monitored on each of these pages and also the user can easily Normalize Receiver Optical Input power on the **Optical** page and also change the Receiver Attenuator on the **RF** page. On the **Switch** page, the user can switch the Receiver Control Switch (CTL) values between Open and Closed for both Rx A and Rx B. 

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.1.0.x [SLC Main] | <ul><li>Bus addresses adapted to allow addressses above 9</li><li>Convertion of Optical Power modified</li><li>Layout modified</li><li>Normalization fixed</li><li>Connector available on Repo Manager</li><li>Unnecessary parameters removed and fast timer interval reduced</li></ul>         |1.0.0.X|-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.1.0.x     |1.1       |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.1.0.x    |No       |Yes         |-         |-   |

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: 10.210.64.11
- **IP port**: 161
- **Bus address**: 12

SNMP Settings:

- **Get community string**: user
- **Set community string**: private


### Initialization

No additional configuration of parameters is needed

### Redundancy

There is no redundancy defined.

## How to use

The **General** page contains basic information regarding the Unit. These include the following:
<div style="display: flex; flex-direction: row; gap: 128px">
<div>
<h1>Identification</h1>
<ul>
<li>Name</li>
<li>Type</li>
<li>Serial Number</li>
<li>Software, Hardware and BIOS Version</li>
<li>Rack and Slot Number</li>
</ul>
</div>
<div>
<h1>Statistics</h1>
<ul>
<li>Uptime</li>
<li>Temperature</li>
</ul>
</div>
</div>

On the **Optical** page of this connector, the user has the overview of Rx KPIs (both Rx A and Rx B). The KPIs include:
<ul><li>Status</li><li>Optical Input Power</li><li>Wavelength</li></ul>

Under this page, the user has has access to two more pages **Normalize Rx A** and **Normalize Rx B**. On these pages, the user can normalize the Optical Input Power of Rx A and Rx B respectively.

The **RF** page contains details for both Rx A and Rx B regarding the Radio-Frequency Module
Here the user can read and modify the value of the Attenuator for both Rx A and Rx B. 
Also here the user can see the information regarding the Automatic Level Control (ALC)

The last page **Switch** contains the Unit Mode, which can take two values:
<ul>
<li>Redundant</li>
<li>Segmented</li>
</ul>

On this page the user can read and change the Receiver Control Switch (CTL) for both Rx A and Rx B. It can be one of these two values:
<ul>
<li>Open</li>
<li>Closed</li>
</ul>

All of this data is retrieved using **SNMPv1**