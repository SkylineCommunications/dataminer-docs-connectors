---
uid: Connector_help_Evertz_TR-4800E_Technical
description: "Configure the Evertz TR-4800E connector in DataMiner: connection setup, GPI and GPO tables, tally control, and scheduled tally automation."
---

# Evertz TR-4800E

## About

This connector monitors and controls an Evertz TR-4800E tally router with the Quartz protocol over TCP/IP. It polls the status of the general-purpose inputs (GPIs) and outputs (GPOs), processes unsolicited tally updates sent by the device, and sends commands to switch GPO tallies on or off.

The base unit has 32 GPIs and 48 GPOs. With the +BP16 option, 16 extra front-panel GPIOs are available, for up to 64 inputs and 64 outputs.

## Configuration

### Connections

#### Serial Connection - Main

This connector uses a smart-serial connection over TCP/IP and requires the following input during element creation:

- Interface connection:

  - **IP address/host**: The IP address of the TR-4800E.
  - **IP port**: The Quartz control port of the device, by default *9676*.
  - **Bus address**: Not required.

### Initialization

On the **General** page, set **General Purpose Inputs** and **General Purpose Outputs** to the number of GPIs and GPOs of the device (1 to 64, by default *64*). The **Inputs** and **Outputs** tables are created based on these values.

### Automation Scripts

Automation scripts can switch tallies by setting the parameters below on the element. In all formats, the ports are the GPO numbers, separated by a pipe character (`|`).

| Parameter | Effect | Format |
|--|--|--|
| **StartTallyAutomation** (95) | Switches the ports on immediately. | `1\|2\|3` or `[time]_1\|2\|3` |
| **StopTallyAutomation** (96) | Switches the ports off immediately. | `1\|2\|3` or `[time]_1\|2\|3` |
| **Add Info to command table** (9201) | Schedules an ON command. | `[time]_1\|2\|3` |
| **Add Info to command table OFF** (9202) | Schedules an OFF command. | `[time]_1\|2\|3` |

- For parameters 95 and 96, an optional time prefix followed by an underscore is ignored, and the command is sent immediately.
- For parameters 9201 and 9202, the time is required. Use a format that the DataMiner Agent can always parse, for example *2026-11-19 14:00:00_1|2|3*. Commands with an invalid time are rejected and logged in the element log file.

## How to Use

### General

The **General** page shows the number of GPIs and GPOs, and the **Command Table** with the scheduled tally commands.

### Inputs

The **GPI Inputs** table shows the status (*On* or *Off*) of each input. You can change the **Name** of each input.

GPI status is polled every 5 minutes, and is also updated as soon as the device sends an unsolicited update. If a polling cycle takes longer than 2 minutes, it is restarted automatically.

### Outputs

The **GPI Outputs** table shows the status of each output. Use the **Status** toggle button to switch an output tally on or off. You can change the **Name** of each output.

### Scheduled commands

Commands added through parameters 9201 and 9202 appear in the **Command Table** with the scheduled **Time**, the **Command** (the ports), the **Command Action** (*ON* or *OFF*), and **Sent**:

- *No*: The command has not been executed yet.
- *Yes*: The command was executed.
- *Fail*: The command could not be executed.

While the table contains commands, the connector checks it every 300 ms. A command is executed when its scheduled time is reached (up to 10 seconds late). Commands with an invalid time are removed immediately. Every minute, executed commands and commands that are more than 2 minutes overdue are removed from the table. When the table is empty, the check stops until a new command is added.

### Debug

- **Custom Command**: Sends a raw Quartz command to the device. Enter the full command, including the leading period (for example *.MA001,002*). A carriage return is added automatically.
- **Clear Commands**: Removes all entries from the Command Table.
