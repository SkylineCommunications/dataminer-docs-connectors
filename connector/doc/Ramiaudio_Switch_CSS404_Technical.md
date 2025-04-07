---
uid: Connector_help_Ramiaudio_Switch_CSS404_Technical
---

# Ramiaudio Switch CSS404

## About

The Ramiaudio Watchdog CSS404 is designed for continuous monitoring of mono or stereo analog or digital audio signals. This connector controls the inputs, listens for traps from the device, and reads the status and errors of the device.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### General Page

The General page displays general information, such as the **Name** and **Version**.

> [!NOTE]
> To set the **System Date Time**, use the format **dd/MM/yyyy HH:mm:ss**.

Below the parameters, you can find the following buttons:

- **System Reset**: Reboots the device.
- **Refresh Device Info**: Polls the **Name**, **Version**, **Date**, **Serial Number**, **System Date Time**, and **Device Label** immediately.
- **Set Main & Auto Switch**: Sets the **Active Input** to *Main*, and then sets the **Switch Mode** to *Auto*.
- **Set Switch Mode**: Changes the **Switch Mode** of the device to either *Manual* or *Auto*.
- **Force Active Input**: Changes the **Switch Mode** to *Manual*, and then sets the **Active Input** to either *Backup* or *Main*.
- **Force SD**: Forces the **Switch Input** to *SD Card*, if the **SD Card** parameter is *Available*.
- **Refresh All**: Polls every parameter in the connector again.

### System Page

The System page contains controls and status information for the various inputs or parts of the device. The information in the table can be refreshed using the **Refresh** button.

Via a page button, you can access the **Input Status** table.

### Traps Page

The **Main Input**, **Backup Input**, **Active Physical Input**, **Active Input**, **Audio Output**, **Software Mode**, and **Power 1 & 2 Trap** states can be found on the Traps page. Each state is either *Invalid*, *Disabled*, or *Enabled*.

The **Trap Destinations** table is displayed via a page button.

### AES Error Page

This page contains the **Error AES Table**, with information such as the status of the **Validity** or **Confidence**.
