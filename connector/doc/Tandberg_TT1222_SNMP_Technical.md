---
uid: Connector_help_Tandberg_TT1222_SNMP_Technical
description: "Learn how to use the Tandberg TT1222 SNMP connector, including the SNMP connection, the TrapServer setting, and the trap-driven alarms."
---

# Tandberg TT1222 SNMP

## About

The Tandberg TT1222 is an MPEG-2 standard definition integrated receiver decoder (IRD) that receives DVB satellite (QPSK) or ASI transport streams and decodes the selected service to analog or SDI video with analog or digital audio.

This connector monitors the device through **SNMP traps**. The TT1222 sends a trap whenever the state of its input lock, video decoding, audio decoding, data channel, or bit error rate changes, and the connector maps each trap to a dedicated alarm on the element. The only value that is actively polled is the **TrapServer** IP address of the device.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **Device address**: Not required.

SNMP Settings:

- **IP port**: The IP port of the device, by default *161*.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

The alarms of this connector are only raised or cleared when the device sends a trap. After creating the element, make sure the TT1222 sends its traps to the DataMiner Agent that hosts the element:

1. Open the **General** page of the element.
1. Check the **TrapServer** parameter, which shows the trap destination currently configured on the device.
1. If it does not point to the DataMiner Agent, set it to the IP address of the DataMiner Agent. The connector writes the new address to the device over SNMP.

Until a trap has been received, the element shows no alarms for the trap-driven conditions, even if the device is already in error.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### General Page

This page shows the **TrapServer** parameter, which is polled approximately once per minute. If it shows an address other than the DataMiner Agent, traps are being sent elsewhere and no alarms will be raised on the element.

### Trap-Driven Alarms

The trap conditions are not displayed as parameters on a page. They are raised as alarms on the element, which you can follow in the Alarm Console. Six conditions are monitored:

- **No Input Lock Status**: The decoder has lost, or regained, lock on its satellite or ASI input.
- **Video Status**: A video decoding error has occurred or been cleared.
- **Audio 1 Status** and **Audio 2 Status**: An error has occurred or been cleared on the first or second audio decoder.
- **Data Status**: An error has occurred or been cleared on the data channel.
- **BER Status**: The bit error rate has crossed, or returned below, the threshold configured on the device.

The severity of each alarm follows the severity level that the TT1222 includes in the trap (Normal, Information, Warning, Minor, Major, or Critical). As a result, an alarm is cleared when the device sends the corresponding trap with a *Normal* severity, not by polling. If a device was already in error before the element was created, the alarm will only appear after the device sends its next trap for that condition.

### Web Interface Page

This page embeds the web interface of the device, which you can use for settings that are not exposed by the connector.

## Notes

- This connector does not poll the reception, video, or audio parameters of the device. Monitoring relies entirely on the traps sent by the TT1222.
- The DataMiner Agent must be able to receive SNMP traps from the device (UDP port 162 by default).
