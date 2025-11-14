---
uid: Connector_help_Mediaproxy_Logserver_Technical
---

# Mediaproxy Logserver

The Mediaproxy Logserver connector monitors and controls the activity of the Mediaproxy LogServer, a hardware and software platform used for broadcast compliance logging, monitoring, and content verification.

The connector provides full visibility into system performance, channel states, event data, and extract information via both SNMP traps and REST/Push APIs. It ensures continuous monitoring of service status, trap activity, and event-driven notifications in real time.

The connector is Cassandra-compliant and integrates seamlessly with DataMiner 10.3.0 or higher.

## About

### Version Info

| Range                | Key Features                  | Based On     | System Impact     |
|----------------------|-------------------------------|--------------|-------------------|
| 1.0.0.x              | Initial version.              | -            | -                 |
| 1.0.1.x              | REST API communication added. | -            | -                 |
| 1.0.2.x              | Added push  API.              | -            | -                 |
| 1.0.3.x [SLC Main]   | Traps table turned volatile.  | -            | -                 |

### Product Info

| Range     | Supported Firmware          |
|-----------|-----------------------------|
| 1.0.0.x   | -                           |
| 1.0.1.x   | Mediaproxy LogServer API v1 |
| 1.0.2.x   | Mediaproxy LogServer API v1 |
| 1.0.3.x   | Mediaproxy LogServer API v1 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |
| 1.0.2.x   | No                  | Yes                     | -                     | -                       |
| 1.0.3.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP connection

This connector uses an SNMP connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: Set this to "any".

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

Used for REST API communication to retrieve system and channel information.

- **IP address/host**: The polling IP of the device.
- **IP port**: Default: *443*.
- **Bus address**: Default: *bypassproxy.*

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: Set this to "any".
  - **IP port**: Set this to "any".

Push API:

- When setting up the push API URLs on the device, be sure to use the following formats:

  - **http://\<ip of device\>/events** for event messages.
  - **http://\<ip of device\>/dpi** for DPI/SCTE messages.
  - **http://\<ip of device\>/nave** for NAVE event messages.
  - **http://\<ip of device\>/captions** for closed caption messages.
  - **http://\<ip of device\>/eas** for EAS messages.

### Initialization

Set the Authentication Token on the General page. This token is required for REST API and Push API communication.

## Usage

The Mediaproxy Logserver connector provides a comprehensive view of the system’s operational state through several main data pages:

- **General**: Allows you to configure essential communication settings such as the authentication token, device IP, and trap IP sources.
- **Channels**: Displays channel information retrieved from the REST API, including identifiers, names, and analysis parameters.
- **System Status** / **Channel Status**: These pages provide real-time monitoring of both overall system health and individual channel conditions, with status indicators for video, audio, captions, and service accessibility.
- **Transport Stream Monitor** / **OTT Stream Monitor**: These pages show detailed metrics for stream quality and availability
- **Traps**: Displays all SNMP trap activity, timeout configurations, and receiver status.
- **Events** / **Extracts**: These pages display detailed event and extract information retrieved via REST and Push APIs, enabling you to track event types, subtypes, and their current states.
- **Push API Status**: Summarizes the status and timeout information for all configured push message types, ensuring that all real-time data flows are active and responsive.
