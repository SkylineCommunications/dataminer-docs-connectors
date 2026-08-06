---
uid: Connector_help_Generic_Trap_Receiver_Technical
---

# Generic Trap Receiver

## About

The Generic Trap Receiver is used to capture and display all the traps for a specific IP address.

## Configuration

### Connections

#### SNMP Main Connection

This connector uses an SNMP protocol connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The IP address where the traps should be received.

  > [!NOTE]
  > The IP address defined in the SNMP connection will be set by default in the parameter **Trap IP Sources**. The IP address defined in the parameter can be set to a different IP address if required (see [Trap IP Sources](#trap-ip-sources)). Updated values on the parameter **Trap IP Sources** will not be synchronized with the one defined in the SNMP connection.

SNMP Settings:

- **Port number**: The port of the connection device (default: *161*).

  > [!IMPORTANT]
  > Although the port can be configured in the element settings, this will not change the port used by the DataMiner Agent to receive SNMP traps. The default port for SNMP traps is *162*. If a different port is needed, make sure to change the `trapPort` attribute in the `SNMPv1`, `SNMPv2`, or `SNMPv3` tag of the *DataMiner.xml* file (depending on which SNMP protocol version is used). For details, refer to [Changing SNMP agent ports](https://aka.dataminer.services/changing-snmp-agent-ports).

## Usage

### General Page

#### Trap IP Sources

To capture traps, specify the IP address(es) for which traps should be captured in the **Trap IP Sources** parameter. Multiple IP addresses can be specified using a comma as separator. Additionally, wildcards can be used to specify a range of IP addresses. For example, `192.168.1.*` will capture traps from all IP addresses in the `192.168.1.x` range.

#### Traps Table and Traps Number

The **Traps** table will display an overview of the captured traps with their information (OID, Source IP, and Bindings).

>[!NOTE]
>
> - Connector range 1.0.1.x defines a column in the **Traps** table for each binding. Currently, up to 20 bindings are supported.
> - Connector range 1.0.2.x bindings are stored in a different table (see **Trap Bindings** table). This allows more than 20 bindings if needed.

The **Traps Number** parameter will show the number of traps in the table.

> [!TIP]
> To have an overview of the number of traps received over time, enabling trending on the Traps Number parameter is recommended.

#### Information Events

If you want an information event to be created on the DMA every time a trap is received, enable the **Information Events** parameter (included in connector range 1.0.1.x).

#### Auto Clear

The **Auto Clear** page button shows settings that allow the cleaning of the Traps table based on the number of traps or the age of the traps.

#### Trap Table Naming Suffix

This setting can be used to define the content of the display key of the **Traps** table. By default, the key is set as follows:

```text
Incremental Counter: Source IP Address: OID
```

- **Incremental counter**: Internal counter that is incremented for each new trap received. This makes it possible to have a unique key for every trap, even if they have the same source IP and OID.
- **Source IP Address**: The IP address from which the trap was received.
- **OID**: The OID of the trap.

To update the display key, you can use the index (0-based) of the column between curly brackets. For example, if you want to include the source IP address and the first binding in the display key, you can set the parameter as follows:

```text
{3}-{5}
```

`{3}` corresponds to the source IP address column, and `{5}` corresponds to the first binding column. The separator between the columns can be defined as desired (in this example, a hyphen is used).

> [!NOTE]
> The display key will always contain the incremental counter as the first column to ensure that each trap has a unique key.
>
> For example, if the naming suffix parameter is set to `{3}-{5}`, the actual display key will be set as follows:
>
> ```text
> {0}:{3}-{5}
> ```

### Lookup Configuration Page

On this page, you can use the **Lookup Table** to replace the incoming trap OID with a custom description. For this purpose, the parameter **Lookup Table State** must be enabled.

By default, the lookup table contains some pre-defined OIDs (from SNMPv2-MIB), but you can add more OIDs as needed.

Using the **Add Raw Value** button, you can add an OID to the lookup table. The **Clear Table** button can be used to delete all custom values added from the lookup table, except the pre-defined values.

### Filter Trap Page

On this page, you can configure traps to be filtered so that certain traps will not be received.

Filter rules can be added with [manual provisioning](#manual-provisioning) or [automatic provisioning](#automatic-provisioning).

#### Manual Provisioning

By right-clicking in the **Trap OID Filter Trap** table, you can add a new filter rule.

- **Trap IP Source**: The source IP address for which the trap should be filtered. You can use wildcards to specify a range of IP addresses. For example, `192.168.1.*` will filter traps from all IP addresses in the `192.168.1.x` range.

  > [!NOTE]
  > Make sure that the IP address (or address range) is defined in the **Trap IP Sources** parameter, otherwise the filter rule will not be applied.

- **Trap OID Filter**: The OID of the trap that should be filtered. You can use wildcards to specify a range of OIDs. For example, `1.3.6.*` will filter all traps with an OID starting with `1.3.6`.
- **State**: The state of the filter rule, which can be either enabled or disabled (default: *enabled*). Only enabled filter rules will be applied.
- **Delete**: The delete button can be used to delete a filter rule.

> [!NOTE]
> Filters are applied from top to bottom.

#### Automatic Provisioning

The parameters available via the **Filter Provisioning** page button allow you to provision filter rules based on a CSV file.

- The parameter **Trap OID Filter Format** defines the format of the CSV file, which should include the following columns:

  ```text
  Trap IP Source; Trap OID Filter
  ```

  This format is hardcoded in the connector and cannot be changed. The **Trap OID Filter Format** parameter is only used to display the expected format of the CSV file.

  Below an example of the content of the CSV file:

  ```text
  Trap IP Source; Trap OID Filter
  192.168.1.1;1.3.6.1.4.1.8813.1.1.2.3.2
  ```

- The **Export** button can be used to export the filter rules currently available in the table to a CSV file. The exported file will follow the format defined in the parameter **Trap OID Filter Format**.

  Before exporting the filters to a file, you must define a file name in the parameter **File Name**.

  - If the file already exists, the exported filter rules will be overwritten in the file (previous rules will be deleted).
  - If the file does not exist yet, a new file will be created with the exported filter rules.

  > [!TIP]
  > - It is not necessary to create the file beforehand.
  > - You do not need to specify the file path, only the file name. The file will be created in the protocol folder `Generic Trap Receiver`.

- The **Import** button can be used to import filter rules from a CSV file. To import filter rules, you first need to upload the file to the protocol folder `Generic Trap Receiver` (see [Documents](https://aka.dataminer.services/About_the_Documents_module)). The CSV file must follow the format defined in the parameter **Trap OID Filter Format**.

  - In the parameter **File Name**, select the file with the filter rules to import. If the file is not available, you can click the **Refresh** button to update the list of available files.
  - If the file does not exist or if the content of the file does not follow the expected format, an error message will be logged and no filter rules will be imported.
  - If the file exists and the content follows the expected format, the filter rules in the file will be added to the table. The existing filter rules in the table will be deleted before the new ones are imported.

The parameter **Trap OID Provisioning Import Report** can be used to track the result of the filter rules import. The parameter will show the number of rules successfully imported, the number of rules that failed to be imported, and a message with details about the errors encountered during the import.

### Update Trap Page

This page allows you to set up rules so that specific traps can update traps with a specific OID and alarm reference.

> [!NOTE]
>
> - From version 1.0.1.17 onwards, basic regular expressions using "\*" are supported.
> - From version 1.0.1.24 onwards, with the **Binding Alarm Index**, you can set up rules that are a combination of columns. To do so, specify a backslash ("\\") followed by a comma-separated list of bindings. Also add a row with the same specific OID to the **Filter Trap** page.

Similar to filter traps, update rules can be added with [manual provisioning](#manual-provisioning-1) or [automatic provisioning](#automatic-provisioning-1).

#### Manual Provisioning

By right-clicking in the **Trap OID Update** table, you can add a new update rule.

- **Trap OID Updated**: The OID of the trap that should be updated. Regular expressions are supported.
- **Trap OID Updating**: The OID of the trap that should update the trap defined in the previous column. Regular expressions are supported.
- **Binding Alarm Index**: The bindings that will be used.

#### Automatic Provisioning

The parameters available via the **Update Provisioning** page button allow you to provision update rules based on a CSV file.

- The parameter **Trap Update File Format** defines the format of the CSV file, which should include the following columns:

  ```text
  Trap OID Updated; Trap OID Updating; Binding Alarm Index
  ```

  - **Trap OID Updated**: The OID of the trap (available in the Trap table) that should be updated.
  - **Trap OID Updating**: The OID of the trap that should update the first trap.
  - **Binding Alarm Index**: The binding that should be used to link these two traps. In the example below, the value of the first binding will be used as alarm reference.

  For example:

  ```text
  Trap OID Updated;Trap OID Updating;Binding Alarm Index
  1.3.6.1.4.1.8813.1.1.2.3.2;1.3.6.1.4.1.8813.1.1.2.3.3;/1
  ```

  This format is **hard-coded** in the connector and cannot be changed. The **Trap Update File Format** parameter is only used to display the expected format of the CSV file.

- The **Export** button can be used to export the update rules currently available in the table to a CSV file. The exported file will follow the format defined in the parameter **Trap Update File Format**.

  Before exporting the update rules to a file, you must define a file name in the parameter **Update File Name**.

  - If the file already exists, the exported update rules will be overwritten in the file (previous rules will be deleted).
  - If the file does not exist yet, a new file will be created with the exported update rules.

  > [!TIP]
  > - It is not necessary to create the file beforehand.
  > - You do not need to specify the file path, only the file name. The file will be created in the protocol folder `Generic Trap Receiver`.

- The **Import** button can be used to import update rules from a CSV file. To import update rules, you first need to upload the file to the protocol folder `Generic Trap Receiver` (see [Documents](https://aka.dataminer.services/About_the_Documents_module)). The CSV file must follow the format defined in the parameter **Trap Update File Format**.

  - In the parameter **File Name**, select the file with the update rules to import. If the file is not available, you can click the **Refresh** button to update the list of available files.
  - If the file does not exist or if the content of the file does not follow the expected format, an error message will be logged and no update rules will be imported.
  - If the file exists and the content follows the expected format, the update rules in the file will be added to the table. The existing update rules in the table will be deleted before the new ones are imported.

The parameter **Provisioning Import Report** can be used to track the result of the provisioning rules import. The parameter will show the number of rules successfully imported, the number of rules that failed to be imported, and a message with details of the errors encountered during the import.

### Heartbeat Trap Page

This page allows you to set up the sending and receiving of heartbeat traps. These traps can be used to test and monitor the DataMiner SNMP forwarding function.

#### Receive Heartbeat Trap

By default, this function is disabled. To enable it, set the parameter **Heartbeat OID** to the OID of the trap that should be used as heartbeat trap.

Once this is enabled, the parameter **Time Since Last Heartbeat** will show the time since the last heartbeat trap was received. You can reset the counter of this parameter by clicking the **Reset** button.

#### Send Heartbeat Trap

By default, this function is disabled. To enable it, set the parameter **Heartbeat Interval** to the required interval for sending the heartbeat trap.

The parameter **Next Heartbeat Counter** will show the time until the next heartbeat trap is sent. You can manually send a trap by clicking the **Send Heartbeat** button.

> [!NOTE]
> The *Send Heartbeat Trap* function is currently under revision and might not work as expected. If you want to use this function, please [contact DataMiner Support](https://aka.dataminer.services/contacting-tech-support) to check the current status of this feature.
