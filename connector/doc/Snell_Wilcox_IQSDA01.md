---
uid: Connector_help_Snell_Wilcox_IQSDA01
---

# Snell Wilcox IQSDA01

## About

The IQSDA01 card is an Intelligent Reclocking High-Performance HD-SDI/SD-SDI Distribution Amplifier. The device provides up to seven re-clocked outputs for HD-SDI 1.5 Gbit/s or 270 Mbit/s SD-SDI signals, four re-clocked outputs for DVB-ASI signals, or even non re-clocking distribution of wide band signals. Its 140m HD input equalization performance makes it a capable HD-SDI DA.

The IQSDA01 card can be inserted in a Snell & Wilcox IQ-Modular framework, fitting up to 16 modules (3RU) with full redundancy in a hot-swappable flexible architecture. This framework also allows the monitoring of all its cards by SNMP or the vendor-specific RollCall protocol, which is used by this connector for all communication.

Device features include:

- Intelligent HD-SDI and SD-SDI/DVB-ASI re-clocking distribution amplifier.

- Distributes DVB-ASI (outputs 1, 3, 5, 7) and other wide band signals.

- Equalizes up to 140 m at 1.5 Gbit/s and up to 350 m at 270 Mbit/s of Belden 1697A cable.

- Supported standards:

  - HD-SDI to SMPTE292M
  - SD-SDI to SMPTE259M-C
  - DVB-ASI

- RollCall monitoring

- 16 user configurable memories

## Configuration

### Connections

This connector uses a **serial** connection and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The polling IP of the device. (This is the IQ-Modular framework.)
- **IP port**: The IP port of the device. The default value is *2050*.
- **Bus address**: Indicates the slot and port where the IQSDA01 card can be found. The format of the bus address is `UU.PP`, where UU should be replaced by the unit address and PP should be replaced by the Port. Both values should be hex encoded. Example: `15.0A`.

> [!NOTE]
> If you have installed the "RollCall Control Panel" software (by Snell & Wilcox) and have the interface of the card open, then the full address should be visible under the tab "Connected Units". This could look like "0000:11:01". You need the "11:01" but should replace the semicolon with a dot "." to "11.01". (Note also that the network address should always be "0000" because the connector does not support communication over bridges.)

### Initialization

The connector needs no configuration except for the card address, which needs to be configured in the **bus address** field in the element wizard. If the value cannot be parsed as a valid slot number, the connector will automatically and immediately stop after startup. This ensures that no commands (and especially sets) can be sent to a random device.

The log file will contain a message indicating that the connector failed to parse the bus address, along with the expected format of the address.

## How to Use

### General

On this page, you can find some important parameters like **Auto** (Input), **Force STD**, and **Reclock Bypass**.

The page also contains page buttons that open the **Logging** and **Menu** pages, and there are two buttons to restart or reset the device.

The **Display** parameter will reflect the text on the front pannl of the device.

Finally, some version information is available, including **Software Version** and **Serial**.

### Memory

This page contains the parameters to configure the user-editable memory slot. Each slot has a **Save** and **Recall** button below it.

### Connection Info

On this page, some extra parameters can be found about the connection. Most will have no importance to the operators, except during setup of elements or for finding connection problems.

The two most important parameters are **Session Status** and **Card User Name**. Shortly after startup, the session status should be set to *Connected* and never change again. If no session can be established after startup, the status will remain *Not Initialized*, and if a connection had been established but was broken by the device, the value should change to *Disconnected*.

> [!NOTE]
> The **Session Status** refers to the logical connection instead of the physical connection. This means that it is possible that the device will go in timeout (physical connection lost) while the **Session Status** (logical) remains *Connected*. This would indicate that no response was received on messages sent to the device, though usually the logical session will also get disconnected when the physical connection is interrupted. In that case, the connector will detect this when the device becomes accessible again (= physical connection restored and device out of timeout state) and shortly afterwards set the **Session Status** to *Disconnected,* until a new session is established (which should take less than 15 seconds).

Another important parameter is the **Force Poll** button, which will refresh all parameters. This is the only real "polling" mechanism in the connector. All other parameter updates are event-driven. This polling otherwise only happens after a new session is established, which can be after element startup, or when the session was disconnected by the device.

The last important parameter is the **Card User Name**. This parameter contains the name that is also displayed in the software from Snell & Wilcox to identify the cards.

The other parameters, **Unit Address** and **Unit Port**, contain respectively the unit and port parsed from the elements bus address.

The parameters **Local Session Nr** and **Assigned Session Nr** are usually only used to identify the traffic between the element and the card during network analysis. Any non-zero **Assigned Session Nr** indicates that the **Session Status** is *Connected*. The Local Session Nr is always the combination of the unit address and port of the monitored card.

## Notes

The element will automatically stop if the bus address could not be parsed. This should prevents sets to a random element (or broadcasted to all elements). If the element was stopped for this reason, the log file will contain a message to indicate this.
