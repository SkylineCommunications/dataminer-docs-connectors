---
uid: Connector_help_Snell_Wilcox_IQAVDR
---

# Snell Wilcox IQAVDR

## About

The IQAVDR is a high-quality distribution amplifier card for composite or component video with adjustable gain and equalization and full remote control and status reporting. The IQAVDR provides up to ten equalized analog video outputs. Features include adjustable gain and equalization.

The IQAVDR card can be inserted in a Snell & Wilcox IQ-Modular framework, fitting up to 16 modules (3RU) with full redundancy in a hot swappable flexible architecture. This framework also allows the monitoring of all its cards by SNMP or the vendor-specific RollCall protocol, which is used by this connector for all communication.

## Configuration

### Connections

This connector uses a **serial** connection and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The polling IP of the device. (This is the IQ-Modular framework.)
- **IP port**: The IP port of the device. The default value is *2050*.
- **Bus address**: Indicates the slot and port where the IQAVDR card can be found. The format of the bus address is `UU.PP`, where UU should be replaced by the unit address and PP should be replaced by the Port. Both values should be hex encoded. Example: `15.0A`.

> [!NOTE]
> If you have installed the "RollCall Control Panel" software (by Snell & Wilcox) and have the interface of the card open, then the full address should be visible under the tab "Connected Units". This could look like "0000:11:01". You need the "11:01" but should replace the semicolon with a dot "." to "11.01". (Note also that the network address should always be "0000" because the connector does not support communication over bridges.)

### Initialization

The connector needs no configuration except for the card address, which needs to be configured in the **bus address** field in the element wizard. If the value cannot be parsed as a valid slot number, the connector will automatically and immediately stop after startup. This ensures that no commands (and especially sets) can be sent to a random device.

The log file will contain a message indicating that the connector failed to parse the bus address, along with the expected format of the address.

## How to Use

### General Page

Because there is only a limited set of parameters, most of them can be found on this page.

The **Display** parameter will reflect the text on the front panel of the device.

### Connection Info Page

On this page, some extra parameters can be found about the connection. Most will have no importance to the operators, except during setup of elements or for finding connection problems.

The two most important parameters are **Session Status** and **Card User Name**. Shortly after startup, the session status should be set to *Connected* and never change again. If no session can be established after startup, the status will remain *Not Initialized*, and if a connection had been established but was broken by the device, the value should change to *Disconnected*.

> [!NOTE]
> It is possible that the device will go in timeout while the **Session Status** remains *Connected*. This would indicate that no response was received on messages sent to the device. However, that does not necessarily mean that the session itself would be closed by the device. The session will only be closed if, during a period of network problems, messages from the card (containing parameter updates) are lost (and thus not acknowledged.) In that case, the connector will detect this when the device becomes accessible again and shortly afterwards set the **Session Status** to *Disconnected,* until a new session is established.

Another important parameter is the **Force Poll** button, which will refresh all parameters. This is the only real "polling" mechanism in the connector. All other parameter updates are event-driven. This polling otherwise only happens after a new session is established, which can be after element startup, or when the session was disconnected by the device.

The last important parameter is the **Card User Name**. This parameter contains the name that is also displayed in the software from Snell & Wilcox to identify the cards.

The other parameters, **Unit Address** and **Unit Port**, contain respectively the unit and port parsed from the elements bus address.

The parameters **Local Session Nr** and **Assigned Session Nr** are usually only used to identify the traffic from/to the card in a wireshark capture. The **Local Session Nr** equals the **Unit Port**, and a non-zero **Assigned Session Nr** indicates that the **Session Status** is *Connected*.

## Notes

The element will automatically stop if the bus address could not be parsed. This should prevents sets to a random element (or broadcasted to all elements). If the element was stopped for this reason, the log file will contain a message to indicate this.
