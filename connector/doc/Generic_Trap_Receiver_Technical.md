---
uid: Connector_help_Generic_Trap_Receiver_Technical
---

# Generic Trap Receiver

## About

The Generic Trap Receiver is used to capture and display all the traps for a specific IP address.

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connection device (default: *161*).

## Usage

### General

To capture traps, specify the IP addresses for which traps should be captured in the **Trap IP Sources** parameter, using a comma as separator. This page will then display an overview of the captured traps with their information (OID, Source IP, and Bindings) in the **Traps** table.

If you also want an information event to be created on the DMA every time a trap is received, enable the **Information Events** parameter.

Via the **Auto Clear** page button, you can access settings to clean up the Traps table.

### Lookup Configuration

On this page, you can use the **Lookup Table** to have incoming trap OIDs replaced with an alias name. For this purpose, the parameter **Lookup Table State** must be enabled.

With the **Add Raw Value** parameter, you can add an OID to the lookup table. The **Clear Table** button can be used to delete all the raw values from the lookup table, except for some well-known values.

### Filter Trap

On this page, you can configure traps to be filtered so that certain traps will not be received. Regular expressions are supported.

### Update Trap

This page allows you to set up rules so that specific traps can update traps with a specific OID and alarm reference. From version 1.0.1.17 onwards, basic regular expressions using "\*" are supported.

From version 1.0.1.24 onwards, with the **Binding Alarm Index**, you can set up rules that are a combination of columns. To do so, specify a backslash ("\\) followed by a comma-separated list of bindings. Also add a row with the same specific OID to the **Filter Trap** page.

### Heartbeat Trap

This page allows you to set up sending and receiving of heartbeat traps. These traps can be used to test and monitor the DataMiner SNMP forwarding function.

## Notes

When working with **SNMPv3** traps, please ensure that the *trapPort* attribute in the *SNMPv3* tag of the DataMiner.xml file is correctly set. This value should match the port number where SNMPv3 traps are expected to arrive. 
