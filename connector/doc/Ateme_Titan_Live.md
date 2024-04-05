---
uid: Connector_help_Ateme_Titan_Live
---

# Ateme Titan Live

With this connector, you can gather and view information from the device **Ateme Titan Live**. It also allows you to configure the device.

## About

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|--|--|--|--|
| 1.0.0.x | Initial version. | No | Yes |
| 2.0.0.x | - Connector updated according to new MIB (version 3.4).<br>- A DVE is now added for each entry of the Device table. | No | Yes |
| 3.0.0.x | Added HTTP API features. | No | Yes |
| 4.0.0.x | Implemented the full HTTP API. | No | Yes |
| 4.0.1.x |  | No | Yes |
| 4.0.2.x |  | Yes |  |
| 4.0.3.x | - Corrections to service output logic.<br>- New primary key format for all output tables. | Yes | Yes |
| 4.0.4.x | Primary key of trap table changed. Display key unchanged. | Yes | Yes |
| 4.0.5.x | DCF rework to create internal connection for services from input (both SDI and IP) to output | Yes | Yes |
| 4.0.6.x [Main range] | - Fixed column parameter descriptions according to the guidelines.<br>- Added exception values for NTP parameters. | Yes | Yes |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | -                           |
| 3.0.0.x          | -                           |
| 4.0.0.x          | 4.1.10.5                    |
| 4.0.1.x          | 4.1.10.5                    |
| 4.0.2.x          | 4.1.10.5                    |
| 4.0.3.x          | 4.1.10.5                    |
| 4.0.4.x          | 4.1.10.5                    |
| 4.0.5.x          | 4.1.10.5                    |
| 4.0.6.x          | 4.1.10.5                    |

## Configuration

### Connections

From connector range 4.0.0.x onwards, only an HTTP connection is used.

#### SNMP Connection (Prior to Range 4.0.0.x)

**SNMP Connection:**

- **IP Address/host**: The polling IP of the device, e.g. 10.24.4.138

**SNMP Settings:**

- **Port number**: the port of the connected device, default 161
- **Get community string**: the community string in order to read from the device. The default value is public.
- **Set community string**: the community string in order to set to the device. The default value is private.

#### HTTP Connection

- **IP address/host**: The polling IP or URL of the destination, e.g: http://10.24.4.138
- **IP port**: The IP port of the destination.
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy.*

### Initialization (Range 4.0.0.x)

To use this connector, on the **Security Settings** page, first set a **Username** and a **Password** to authenticate all HTTP sessions.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use - Ranges Prior to 4.0.0.x

This connector will create a DVE for each device attached to the main device.

### General Page

This page displays a table with the blades present on the device.

### Device Page (DVE)

This page will show general information about the device, e.g. **Device Name**, **Device State**, **Device Output URL**, etc.

### Service (DVE)

This page displays information regarding the service provided by this device, e.g. **Service Name**, **Service State**, etc.

### Blade (DVE)

This page shows information about the blade to which the device is connected, e.g. **Blade Name**, **Blade Serial Number**, etc.

## Usage - Range 4.0.0.x

From version 4.0.0.7 onwards, it is possible to export each service as a DVE. This can be configured on the **Services** page.

### General Page

This page displays general information about the device, e.g. Device Name, Firmware Version, CPU Load, Memory Usage, etc.

### SDI Cards Page

This page displays a table with SDI cards information (card name, status, FPGA ID, FPGA version, Board ID, Board version), as well as a table containing SDI inputs information (card name, input number, has signal, video format, mode).

### Services Page

This page displays the Services table. This table displays the service name, service status, streaming status, input information, and output. You can also stop, delete, or start a single service or all services.

From version 4.0.0.8 onwards, a **Manage** button is available for the services, which starts a wizard that allows you to configure some parameters for a service. The wizard uses the Automation script *Ateme_Titan_Live_Manage_Service*.

From version 4.0.0.2 onwards, you can change the format of the SDI input port name. For legacy reasons, this cannot be changed automatically. The old format is `sdi-card-x Input y`; the new format is `sdi-card-x/y`.

### Services Overview Page (Version 4.0.0.2 or Higher)

This page contains a graphical overview of the transport stream structure, with the audio, video, and data streams.

It contains a link to the **Service Tables** subpage.

### Service Tables (Version 4.0.0.2 or Higher)

This page contains the tables that are also shown in a tree control: **Services**, **Output Transport Streams**, **Output Audio Parameters**, **Output Video Parameters**, and **Output Data Parameters**.

- The **Services** table contains information such as the **Status**, the **Streaming Status**, **Input Type**, **Output**, and **Video Format**.

- The **Output Transport Streams** table is an internal table that is only used to link a profile to the streams that are part of that profile.

- The **Output Audio Parameters** table contains information about each output audio stream, such as the **Codec**, the **Bitrate**, and the **Sample Rate**.

- The **Output Video Parameters** table contains information about each output video stream, such as the **Codec**, the **Bitrate**, and the **Framerate**.

- The **Output Data Parameters** table contains information about each output data stream, such as the **Codec**.

In version 4.0.2.1, **Service Tables** is renamed to **Services Output Tables**.

### Service Input Tables (Version 4.0.2.1 or higher)

This page contains the tables that can be used to reconfigure the settings of the IP inputs services: Active Input, TS Smoothing, TS Sync Loss Failover and Timeout, Sync Bytes Erros Failover, PAT Failover and Maximum time between 2 PAT, PMT Failover and Maximum time between 2 PMT, PID Errors Failover and Maximum time between 2 PID, Continuity Failover, Timeframe and Threshold.

### Hardware Monitoring Page

This page displays the CPU temperature, the power supply status, and a table with all the fan information.

### Main Services Status Page

This page displays a table with the status of all main services (NTP, SDI, syslog, VCA, SNMPD, etc.).

### Alarms Page

This page displays a table with alarms. With the Filter Alarms Status toggle button, you can switch between showing all alarms or only open alarms.

### System Configuration Page

On this page, you can configure the time, SNMP, and Syslog.

### Network Configuration Page

On this page, you can configure the device network. The page has four tables: Physical Interfaces, Routes, VLANs, and Statmux Pool.

### Alarms Configuration Page

On this page, you can configure the alarms.

### Security Settings

This page allows you to enter a username and password to authenticate all HTTP sessions. To be able to use all sets, you need to authenticate with the API user.

### Encoding Page (Version 4.0.0.8 or Higher)

This page displays the services available on the device, divided over the TS Services and Encoding Services tables.
