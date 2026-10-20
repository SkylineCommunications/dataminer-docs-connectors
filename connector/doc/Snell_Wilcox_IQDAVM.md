---
uid: Connector_help_Snell_Wilcox_IQDAVM
---

# Snell Wilcox IQDAVM

## About

The IQDAVM card accepts a serial 4:2:2 input to provide a maximum of four equalized and re-clocked outputs, three monitoring composite outputs and four embedded audio analog outputs.

The card can be inserted in a Snell & Wilcox IQ-Modular framework, fitting up to 16 modules (3RU) with full redundancy in a hot-swappable flexible architecture. This framework also allows the monitoring of all its cards by SNMP or the vendor-specific RollCall protocol, which is used by this connector for all communication.

Device features include:

- Up to four re-clocked serial 4:2:2 outputs
- Three monitoring composite PAL/NTSC/PAL-N outputs
- Four analog audio outputs or 2 stereo pairs
- Balanced audio output level adjustable +12 dBu to +24 dBu for 0 dB FS input (-D version)
- Unbalanced audio output level adjustable 1 Volt pk-pk to 4.5 Volts pk-pk into \>50 k ohm, for 0 dB FS input (-B version)
- Audio selection from any embedded channel pair
- 20-bit digital-to-analog audio conversion, -95 dB THD+N typical (Full Scale)
- Audio polarity invert
- Embedded audio presence indication
- On screen display of audio level and status (-M versions only)
- Non-audio ancillary data presence indication
- EDH error detection and reporting
- Test signal generator (Color Bars/Black and - 20 dBFS Tone/Silence)
- Automatic 525/625 line detection and no valid signal indication
- Card edge and RollCall remote control

Ranges

- 1.0.0.X
- 2.0.0.X (Event based updates)

The ranges are not compatible with each other.

> [!NOTE]
> When monitoring this card using range 2.0.0.X, you will find an extra record "DataMiner" in the RollCall application of the vendor. One such record will appear for each element monitoring a card.

## Configuration

### Connections

This connector uses a **serial** connection and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The polling IP of the device. (This is the IQ-Modular framework.)
- **IP port**: The IP port of the device. The default value is *2050*.
- **Bus address**: Indicates the slot and port where the IQDAVM card can be found. The format of the bus address is `UU.PP`, where UU should be replaced by the unit address and PP should be replaced by the Port. Both values should be hex encoded. Example: `15.0A`.

> [!NOTE]
> If you have installed the "RollCall Control Panel" software (by Snell & Wilcox) and have the interface of the card open, then the full address should be visible under the tab "Connected Units". This could look like "0000:11:01". You need the "11:01" but should replace the semicolon with a dot "." to "11.01". (Note also that the network address should always be "0000" because the connector does not support communication over bridges.)

### Initialization

The connector needs no configuration except for the card address, which needs to be configured in the **bus address** field in the element wizard. If the value cannot be parsed as a valid slot number, the connector will automatically and immediately stop after startup. This ensures that no commands (and especially sets) can be sent to a random device.

The log file will contain a message indicating that the connector failed to parse the bus address, along with the expected format of the address.

## How to Use

### General

In the first column are a set of parameters showing a quick view of the unit status. These parameters can also be found on other pages where there will also be a setter available. This setter is removed on the General page so all parameters are shown in a compact way, reducing the need to scroll down to see these parameters.

In the second column, the **Display** parameter shows the content of the LCD screen on the device. The **Software Version**, **Serial No** and **Build No** are also shown.

Two buttons are available to **restart** or **preset** the unit. These buttons will ask for confirmation when clicked.

Finally, the **Headroom** parameter allows you to configure the gain.

### Outputs

On this page, you can find for both analog outputs (A and B) the settings for **Gain**, **Polarity**, **Extract**, and **Default Audio.**

### Setup

This page contains most of the configuration parameters, including:

- **Pattern**
- **0db FS Level**
- **Standard**
- **VBI Pass**
- **Pedestal On**
- **Chroma Bandwidth**
- **Tone Frequency**
- **Default Video**
- **Stats** (**Show** and **Reset Stats** Button)
- **Input Loss** indicator
- **Embedded Audio**
- **EDH Presence**
- **EDH Error sec**

### RollTrack And Logging

On the left, this page displays the RollTrack parameters, and on the right a parameter **Setup: Logging: Standard** which can *enable* or *disable* the logging.

### Connection Info

On this page, some extra parameters can be found about the connection. Most will have no importance to the operators, except during setup of elements or for finding connection problems.

The two most important parameters are **Session Status** and **Card User Name**. Shortly after startup, the session status should be set to *Connected* and never change again. If no session can be established after startup, the status will remain *Not Initialized*, and if a connection had been established but was broken by the device, the value should change to *Disconnected*.

> [!NOTE]
> It is possible that the device will go in timeout while the **Session Status** remains *Connected*. This would indicate that no response was received on messages sent to the device. However, that does not necessarily mean that the session itself would be closed by the device. The session will only be closed if, during a period of network problems, messages from the card (containing parameter updates) are lost (and thus not acknowledged.) In that case, the connector will detect this when the device becomes accessible again and shortly afterwards set the **Session Status** to *Disconnected,* until a new session is established.

Another important parameter is the **Force Poll** button, which will refresh all parameters. This is the only real "polling" mechanism in the connector. All other parameter updates are event-driven. This polling otherwise only happens after a new session is established, which can be after element startup, or when the session was disconnected by the device.

The last important parameter is the **Card User Name**. This parameter contains the name that is also displayed in the software from Snell & Wilcox to identify the cards.

The other parameters, **Unit Address** and **Unit Port**, contain respectively the unit and port parsed from the elements bus address.

The parameters **Local Session Nr** and **Assigned Session Nr** are usually only used to identify the traffic between the element and the card during network analysis. Any non-zero **Assigned Session Nr** indicates that the **Session Status** is *Connected*. The Local Session Nr is always the combination of the unit address and port of the monitored card.

## Notes

The element will automatically stop if the bus address could not be parsed. This should prevents sets to a random element (or broadcasted to all elements). If the element was stopped for this reason, the log file will contain a message to indicate this.

It is possible to monitor the same card using the vendor-supplied RollCall application. In their software, you will see an extra node "DataMiner" for each element that is monitoring a card.
