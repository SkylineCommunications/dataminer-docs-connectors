---
uid: Connector_help_DAC_System_PMB_and_RDS_Monitor_Technical
description: "Learn how to configure and use the DAC System PMB and RDS Monitor connector: SNMP and HTTP connections, sensors, ATS rules, IOU, RF Hawkeye, and FM receiver."
---

# DAC System PMB and RDS Monitor

## About

The DAC System PMB (Power Meter Broadcast) is a data logger that collects RF power measurements from the connected junction boxes, sensors, and detectors monitoring a transmitter antenna system, and that can also drive RF Hawkeye arcing analyzers, ATS rules, and I/O units.

This connector retrieves the data logger information via SNMP, and polls the companion FM receiver via its HTTP API to retrieve RDS data and the audio level of the tuned FM frequencies.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

- **IP address/host**: The polling IP of the PMB data logger.
- **IP port**: The IP port of the device, by default *161*.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

#### HTTP Connection - RDS

This connector uses an HTTP connection to the FM receiver and requires the following input during element creation:

- **IP address/host**: The IP address or host name of the FM receiver HTTP API.
- **IP port**: The IP port of the FM receiver, by default *80*.
- **Bus address**: *ByPassProxy*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### Polling

The connector uses different polling timers:

| Polling frequency | Polled data |
| --- | --- |
| Every 5 seconds | Audio level |
| Every 10 seconds | ATS rules, IOU, and RF Hawkeye tables |
| Every 30 seconds | FM receiver RDS data |
| Every minute | Junction box, sensor, open alarm, and detector tables |
| Every hour | General data logger information |

### General Page

This page shows the **Name**, **Type**, and **Site Name** of the data logger, the **Alarm Power Supply Failure** status, and the **Open Warnings Count** and **Open Alarms Count** reported by the device. These two counters are the first indicators to check when something is wrong at the site.

The page buttons give access to the following subpages:

- **Junction Box**: For each connected junction box, the **Temperature** and **Humidity**, as well as the **No Response** and **Hardware Mismatch** flags, with the **Timestamp** of the last measurement.
- **Sensors**: For each RF sensor, the forward power (**PTX**), reflected power (**PRX**), **Return Loss**, and **VSWR**, together with the degraded and failure flags that the data logger raises for return loss, transmit level, current, temperature, and humidity. The **Monitoring Point** column indicates whether the sensor is enabled on the device. The **Last Measurement** column shows when the data logger performed the measurement.
- **Alarms**: The alarms currently open on the data logger, with their **Source**, their **Threshold**, the **Value** that triggered them, the **Current Value**, and the number of **Occurrences**.
- **Detector**: The **Status**, **PTX**, **PRX**, **Return Loss**, and **VSWR** per detector.

### ATS Rules Page

This page lists the Automatic Transmitter Switching rules configured on the data logger, with their **Condition**, **Action**, and current **State** (*Active* or *Inactive*). A rule that becomes active indicates that the data logger has switched or is about to switch the transmitter chain.

### IOU Page

This page shows the connected I/O units with their **Serial Number** and **IPv4 Address**, and the state of each of the 12 **relays**, 12 **universal inputs**, and 4 **dry contacts** (13 to 16), as well as the value of each of the 16 **analog inputs**. Use it to verify external contacts such as door, mains, or cooling signals that are wired into the IOU.

### Hawkeye Page

This page shows one row per RF Hawkeye processing unit, with the **PU Model**, serial numbers, software and hardware versions, **IP Address**, **RF Status**, **Output PW**, **TX Power**, and the **Total Length** and **Horizontal Path Length** of the monitored transmission line.

The RF Hawkeye analysis can be configured from this table:

- **Enable Arcing Analysis** and **Enable Degradation** switch the two detection modes on or off.
- **Warning Threshold**, **Alarm Threshold**, **Thresholds Unit**, and **Threshold Mode** define when the device raises a warning or an alarm.
- **Left Window**, **Right Window**, and **Observation Period** define the section of the line and the time span that are analyzed.
- **Alert Start** and **Alert End** define the period during which alerts are generated.
- The **Arcing Last Min/Hour/Day/Week/Month Warning** and **Alarm** columns show the number of arcing events per period and can be used to follow the trend of a degrading line.

> [!NOTE]
> Changing these settings writes them to the device. Make sure that the **PW Monitoring Pair**, **TX Site Name**, and **Antenna Name** columns identify the right unit before you change a threshold.

### FM Receiver Page

This page shows one row per tuned FM frequency, with the **Frequency MHz**, the RDS **PI** code, **PS Name**, **PTY**, and **RT** (radio text), the RDS **BLER** (block error rate, where -1 means not available), and the **Audio Level** in dBFS.

The **Audio Level** column comes with default silence detection thresholds (warning at -35 dBFS, minor at -40 dBFS, major at -50 dBFS, and critical at -60 dBFS). The raise and clear delays that avoid false alarms on short pauses are configured in the DataMiner alarm template.

### Web Interface Page

This page embeds the web interface of the data logger, which you can use for settings that are not exposed by the connector.
