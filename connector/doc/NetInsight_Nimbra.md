---
uid: Connector_help_NetInsight_Nimbra
---

# NetInsight Nimbra

The **NetInsight Nimbra** connector allows the monitoring of Nimbra nodes.

With this connector, you can monitor and control the different interfaces of a node, and the current and previous configurations of the device. You can also monitor the TTPs, the channels going through the nodes, and the services starting from them.

Typically, this connector is used together with the **NetInsight Nimbra Application Manager** for the monitoring and controlling of the services between different Nimbra nodes.

> [!IMPORTANT]
> **From version 4.1.3.1 onwards, the unique identifier of the DCF interfaces will be replaced with the DTM name instead of the instance.** If the connector is updated from an older version to 4.1.3.1, the DCF connections could be duplicated and remain in the connector. Please update the connector using the latest *NetInsight Nimbra Package*, restart all elements using the connector, and then use the automation script *DCF Clean Nimbra Connections* to clean up the obsolete DCF links. Alternatively, you can manually install the automation script *DCF Clean Nimbra Connections* and execute it after updating to version 4.1.3.1.

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device (e.g. *192.168.1.6*).
- **Device address**: Not required.

SNMP Settings:

- **Port number**: The port of the connected device (e.g. *161*).
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element created with this connector consists of the following data pages:

- **General Status**: Displays general information such as the System Name, Node Route Metric or Current Timing Source.
- **General Alarms**: Contains the Chassis Alarms table.
- **General Configuration and Backup**: Provides information such as the Number of Configurations, Backup Operation or Backup Description.
- **ITS Interfaces**: Displays the ITS Interface Last Changed parameter and contains the ITS Interfaces Table.
- **ITS-in Services Configuration**: Displays the ITS in Last Changed parameter and contains the ITS-in Services Configuration Table.
- **ITS-out Services Configuration**: Displays the ITS out Last Changed parameter and contains the ITS-out TTP Table.
- **ITS JPEG 2000**: Displays the ITS JPEG 2000 table and contains a parameter that can be used to activate or deactivate polling.
- **ITS Alarm Status**: Displays the ITS In Alarm Status and ITS Out Alarm Status tables.
- **AIF Performance Monitoring**: Contains the AIF - Access Interfaces Monitoring table and allows you to activate or deactivate AIF Polling.
- **DCH Performance Monitoring**: Contains the DCH â€“ DTM Channels Monitoring table and allows you to activate or deactivate DCH Polling.
- **DTM Interfaces and Links**: Displays the DTM Link Last Changed parameter and contains the DTM Interfaces and DTM Links tables.
- **DTM Tx/Rx Statistics**: These pages display the DTM Interfaces - Tx and DTM Interfaces - Rx tables, respectively.
- **DTM DPP-IP Interfaces**: Displays the DTM DPP-IP Last Changed parameter and contains the DPP-IP Interfaces table.
- **DTM Alarms**: Displays the DTM Interfaces Alarm Status table.
- **DTM TIF Performance Monitoring**: Displays the TIF â€“ Trunk Interfaces Monitoring table and allows you to activate or deactivate DTM TIF Polling.
- **Eth Device and Interface**: Displays the Eth Devices Table and the Eth Interfaces and Alarms Table.
- **Eth-Ets Table**: Displays the Eth-Ets Group Last Change parameter and the Eth-Ets Table.
- **Eth-Ets RSTP and Queue Configuration**: Displays the Eth-Ets Group Last Change parameter, the Eth-Ets RSTP Table and the Eth-Ets If Queue Table.
- **Ets Services and Connection Configuration**: Displays the Eth-Ets Group Last Change parameter, the Ets Services and Alarms Table and the Ets T Connection Table.
- **VLAN Table**: Displays the Eth-Ets Group Last Change parameter and the Eth If VlanSets Table.
- **Forward Function**: Displays the Forwarding Group Last Change parameter, the Forward Function Table and the Forward RTSP Table.
- **Originating TTP Configuration**: Displays the Originating Configuration Last Change parameter and the Originating TTP Configuration Table.
- **Originating TTP Destination Configuration**: Displays the Originating TTP Destination Configuration Table.
- **Originating TTP Connection**: Displays the Originating Connection Last Change parameter and the Originating TTP Connection Table.
- **Originating TTP Channels Connection**: Displays the Originating Connection Last Change parameter and the Originating TTP Channels Connection Table.
- **Originating TTP Statistics**: Displays the Originating TTP Statistics Table.
- **Terminating TTP Connection**: Displays the Terminating Connection Last Change parameter and the Terminating TTP Connection Table.
- **Terminating TTP Channels Connection**: Displays the Terminating Connection Last Change parameter and the Terminating TTP Channels Connection Table.
- **Terminating TTP Statistics Table**: Displays the Terminating TTP Statistics Table.
- **Source Route Configuration**: Displays the Source Route Last Change parameter, the Source Route Table and the Source Route Hop Table.
- **Node Channels Table**: Displays the Node Channels Table.
- **Alarm**: Contains the Alarm Table and allows you to enable or disable alarm polling.
- **Embedded Web Server**: Provides access to the web interface of the device. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
