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

- **IP address/host**: The IP address where the traps should be received.

>[!NOTE]
> The IP address defined in the SNMP connection will be set in the parameter **Trap IP Sources** by default, but you can change it to any other IP address if needed (see [General](xref:Connector_help_Generic_Trap_Receiver_Technical#General), Trap IP Sources).

SNMP Settings:

- **Port number**: The port of the connection device (default: *161*).

>[!IMPORTANT]
> Although this setting can be configured, this will not change the port used by the DataMiner agent to retrieve parts. The default port for SNMP traps is *162*.
> In case a different port is needed, make sure to change the `trapPort` attribute in the `SNMPv1`, `SNMPv2`, or `SNMPv3` tag of the *DataMiner.xml* file (depending of the SNMP protocol version is used).
> More information in DataMiner Docs [DataMiner.xml](https://docs.dataminer.services/dataminer/Reference/Skyline_DataMiner_Folder/More_information_on_certain_files_and_folders/DataMiner_xml.html).

## Usage

### General

To capture traps, specify the IP address(es) for which traps should be captured in the **Trap IP Sources** parameter. Multiple IP addresses can be specified using a comma as separator. Additionally, wildcards can be used to specify a range of IP addresses. For example, `192.168.1.*` will capture traps from all IP addresses in the `192.168.1.x` range.

The **Traps** table will display an overview of the captured traps with their information (OID, Source IP, and Bindings).

>[!NOTE]
> - Connector range 1.0.1.x defines a column in the **Traps** table for each binding. Currenltly, up to 20 bindings are supported.
> - Connector range 1.0.2.x bindings are stored in a different table (see **Trap Bindings** table). This allows more than 20 bindings if needed.

The **Traps Number** will show the number of traps in the table.

>[!TIP]
> It is recommended to enable trending on this parameter to have an overview of the number of traps received over time.

If you also want an information event to be created on the DMA every time a trap is received, enable the **Information Events** parameter.

The **Auto Clear...** page button contain settings that allows to clean the table based on number of traps or age. 

Additionally, connector range 1.0.1.x includes the parameter **Information Events** that allows to create an information event on the DMA for every trap received. 

### Lookup Configuration

On this page, you can use the **Lookup Table** to have incoming trap OIDs replaced with an alias name. For this purpose, the parameter **Lookup Table State** must be enabled.

With the **Add Raw Value** parameter, you can add an OID to the lookup table. The **Clear Table** button can be used to delete all the raw values from the lookup table, except for some well-known values.

### Filter Trap

On this page, you can configure traps to be filtered so that certain traps will not be received.

There are two ways to add filter rules:

#### Manual Provisioning

By right-clicking in the **Trap OID Filter Trap** table, you can add a new filter rule.

- Trap IP Source: The source IP address for which the trap should be filtered. You can use wildcards to specify a range of IP addresses. For example, `192.168.1.*` will filter traps from all IP addresses in the `192.168.1.x` range.

>[!NOTE]
> Make sure that the IP address(es) are defined in the **Trap IP Sources** parameter, otherwise the filter rule will not be applied.

- Trap OID FIlter: The OID of the trap that should be filtered. You can use wildcards to specify a range of OIDs. For example, `1.3.6.*` will filter all traps with an OID starting with `1.3.6`.
- State: The state of the filter rule, which can be either enabled or disabled (default: *enabled*). Only enabled filter rules will be applied.
- Delete: The delete button can be used to delete a filter rule.

>[!NOTE]
> Filters will be applied from top to bottom.

#### Automatic Provisioning

The parameters available on the **Filter Provisioning...** page button offers the possibility to provision filter rules based on a CSV file.

- The parameter **Trap OID Filter Format** defines the format of the CSV file, which should include the following columns:

```text
Trap IP Source; Trap OID Filter
```

This format is harcoded in the connector and cannot be changed. The **Trap OID Filter Format** parameter is only used to display the expected format of the CSV file.

Below an example of the content of the CSV file:

```text
Trap IP Source; Trap OID Filter
192.168.1.1;1.3.6.1.4.1.8813.1.1.2.3.2
```

- The **Export** button can be used to export the filter rules currently in the table to a CSV file. The exported file will follow the format defined in the parameter **Trap OID Filter Format**.
Before to export the filters to a file, it is required to define a file name in the parameter **File Name**.
  - If the file already exists, the exported filter rules will be overwritten in the file (previous rules will be deleted).
  - If the file does not exist, a new file will be created with the exported filter rules.
    - It is not required to create the file beforehand.
    - It is not required to specify the file path, only the file name. The file will be created in the protocol folder `C:\Skyline DataMiner\Documents\Generic Trap Receiver`.

- The **Import** button can be used to import filter rules from a CSV file. To import filter rules, first it is required to upload the file to the protocol folder `C:\Skyline DataMiner\Documents\Generic Trap Receiver` (see Documents). The format of the CSV file must follow the format defined in the parameter **Trap OID Filter Format**.
  - In the parameter  **File Name**, select the file with the filter rules to import. If the file is not available, you can click on the **Refresh** button to update the list of available files.

  - If the file does not exist or if the content of the file does not follow the expected format, an error message will be logged and no filter rules will be imported.
  - If the file exists and the content follows the expected format, the filter rules in the file will be added to the table. The existing filter rules in the table will be deleted before importing the new ones.

### Update Trap

This page allows you to set up rules so that specific traps can update traps with a specific OID and alarm reference.

>[!NOTE]
> - From version 1.0.1.17 onwards, basic regular expressions using "\*" are supported.
> - From version 1.0.1.24 onwards, with the **Binding Alarm Index**, you can set up rules that are a combination of columns. To do so, specify a backslash ("\\) followed by a comma-separated list of bindings. Also add a row with the same specific OID to the **Filter Trap** page.

Similar to filter traps, there are two ways to add update rules:

#### Manual Provisioning

By right-clicking in the **Trap OID Update** table, you can add a new update rule.

- Trap OID Updated: The OID of the trap that should be updated. Regular expressions are supported.
- Trap OID Updating: The OID of the trap that should update the trap defined in the previous column. Regular expressions are supported.
- Binding Alarm Index: The bindings that will be used.

#### Automatic Provisioning

### Heartbeat Trap

This page allows you to set up sending and receiving of heartbeat traps. These traps can be used to test and monitor the DataMiner SNMP forwarding function.

## Notes

If you are using this connector with **SNMPv3** traps, make sure that the `trapPort` attribute in the `SNMPv3` tag of the *DataMiner.xml* file is correctly configured. This value should match the port number where SNMPv3 traps are expected to arrive.
