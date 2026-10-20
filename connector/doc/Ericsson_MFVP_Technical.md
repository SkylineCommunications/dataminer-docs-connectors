---
uid: Connector_help_Ericsson_MFVP_Technical
description: "Set up the Ericsson MFVP connector in DataMiner, including REST API connections, credentials, polling, and video service, server, and alarm monitoring."
---

# Ericsson MFVP

The Ericsson MFVP is a DataMiner connector for the MediaKind Controller MediaFirst Video Processing System (MFVP), a software-based, multi-application media processing platform for the content distribution market.

The MediaKind Controller manages multiple MediaKind subproducts, such as:

- MKP: MediaKind Packaging
- MKEL: MediaKind Encoding Live
- MKSP: MediaKind Stream Processor (Multiplexer)
- MDT: MediaKind Development ToolKit (Orchestration Purposes)

This connector is featured in the **Media Data Center (MDC)** project. Apart from monitoring, it can also be used to orchestrate a live encoding service joining the transcoding service and the containerized service (which supports the transcoding service) in a single DataMiner service. This feature requires **DataMiner Service & Resource Management (SRM).**

The connector is capable of fully monitoring the Ericsson MediaFirst Video Processing System, including **alarms**, **services**, **servers**, and the main system **statistics**. It uses multiple REST Web APIs to send and receive data to and from the system using the JSON and XML formats.

## Configuration

### Connections - Range 1.1.0.x

This connector uses two HTTP connections and requires the following input during element creation.

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: 30001).

MDT API (HTTPS):

- **IP Address/Host**: The polling IP or URL of the destination.
- **IP Port**: The IP port of the destination (default: 80).

### Connections - Range 1.2.0.x

This connector uses two HTTPS connections and requires the following input during element creation.

HTTPS CONNECTION:

- **IP address/host**: `https://<IP of the destination>`.
- **IP port**: The IP port of the destination (default: 30001).

HTTPS Connection - MDT API:

- **IP address/host**: `https://<IP of the destination>`.
- **IP port**: The IP port of the destination (default: 443).

For both connections to work, you will also need to go to the element's **Features** page and specify the **username and password** for each connection.

> [!NOTE]
> The ports may vary depending on the implementation.

### Connections - Ranges 1.2.1.x and 1.3.0.x

This connector uses five HTTPS connections and requires the following input during element creation.

HTTPS CONNECTION:

- **IP address/host**: `https://<IP of the destination>`.
- **IP port**: The IP port of the destination (default: 30001).

HTTPS Connection - MDT, STATS, CONFIG, and SOURCE APIs:

- **IP address/host**: `https://<IP of the destination>`.
- **IP port**: The IP port of the destination (default: 443).

For all connections to work, you will also need to go to the element's **Features** page and specify the **username and password** for each connection. The credentials used for the MDT API are also used for the STATS, CONFIG, and SOURCE connections.

> [!NOTE]
> The ports may vary depending on the implementation.

### Initialization - Range 1.1.0.x

After element creation, go to the **Features** page and enable or disable the different features according to your preference.

If you encounter any issues after the element has been configured, check whether the **API Versions** parameter on the Features page matches the **supported firmware**.

### Initialization - Range 1.2.0.x

After element creation, go to the **Features** page and set the **username and password** for both API groups.

This system implementation covers two different HTTPS interfaces with different access credentials.

- The **HTTPS CONNECTION** using the **General API Credentials** has the following default credentials:

  - Username: *admin*
  - Password: *admin*

- The **HTTPS Connection - MDT API** using the **MDT API Credentials** has the following default credentials:

  - Username: *mdt-admin*
  - Password: *changeme*

> [!NOTE]
> If the element is properly authenticated, but Stream Viewer still shows **400 HTTP Bad Request** errors, **use range 1.1.0.x** instead. In this situation, an update action on behalf of the vendor is needed.

### Initialization - Range 1.2.1.x and 1.3.0.x

After element creation, go to the **Features** page and set the username and password for all three API groups.

This system implementation covers two different HTTPS interfaces with different access credentials.

- The **HTTPS CONNECTION** using the **General API Credentials** has the following default credentials:

  - Username: *admin*
  - Password: *admin*

- The **HTTPS Connection - MDT API** using the **MDT API Credentials** has the following default credentials:

  - Username: *mdt-admin*
  - Password: *changeme*

- The **HTTPS Connection - STATS** using the **STATS Credentials** has the following default credentials:

  - Username: *mdt-admin*
  - Password: *changeme*

> [!NOTE]
> If the element is properly authenticated, but Stream Viewer still shows **400 HTTP Bad Request** errors, **use range 1.1.0.x** instead. In this situation, an update action on behalf of the vendor is needed.

## Usage

### General

This page displays the **Services** table, including parameters such as the service name, type, state, and assigned servers.

Each service can be started and stopped individually via the buttons in the **Operations** columns.

A service can also be deleted via the **Delete** button. After pressing the button, you will need to confirm the deletion in a pop-up window.

### Live Encoding Services Overview

This page displays a tree control that provides a structured overview of the service components.

### Live Encoding Inputs

This page displays the following tables:

- **Inputs**: Lists the different live encoding service inputs.
- **Source Configuration**: Lists the different sources per input and their configuration details.

It also contains page buttons to the following subpages:

- **Input Video Streams**: Lists the different live encoding service input video streams.
- **Input Audio Streams**: Lists the different live encoding service input audio streams.
- **Programs**: Lists the programs available in a live encoding service.
- **Elementary Streams:** Lists the elementary streams available in a live encoding service.
- **Input Subtitle Streams**: Lists the different live encoding service input subtitle streams.
- **Input Metadata Streams**: Lists the different live encoding service input metadata streams, such as SCTE35, AIT Metadata and Teletext.

### Live Encoding Processings

This page displays the following tables:

- **Processing**: Lists the different live encoding service processing instances.
- **Occultations**: Lists the different occultations per processing instance and their main statistics.

It also contains page buttons to the following subpages:

- **Video Processings**: Includes detailed information about the processing video streams.
- **Audio Processings**: Includes detailed information about the processing audio streams.
- **Subtitle Processings**: Includes detailed information about the processing subtitle streams.
- **Metadata Processings**: Includes detailed information about the processing metadata streams.
- **Encodings**: Lists the different encoded video and audio streams as well as the configuration that is applied to them.

### Live Encoding Outputs

This page displays the following tables:

- **Outputs**: Lists the different live encoding service outputs and their main statistics.
- **Transport Streams**: Lists the different transport streams per output and their main statistics.

It also contains a page button to the **Output Streams** subpage, which contains detailed information about the output streams.

### Live Encoding Service Statistics

This page contains statistics for all services. In the **Input Monitoring** table, the incoming source statistics are displayed.

The page also contains page buttons to the following subpages:

- **Media Info**: Contains tables regarding video and audio input statistics.
- **Outputs Statistics**: Contains the Output Statistics table, which displays the bitrate of each output generated by each service.

### Live Packaging DVRs

This page displays the following tables:

- **Live Packaging Dvrs:** Lists generic configuration for live packaging services.
- **Live Packaging Dvrs Publishing Points:** Lists all publishing points for live packaging services.

### Live Packaging Statistics

This page displays the following tables:

- **Packaging Inputs Statistics:** Lists the inputs per live packaging service and their main statistics.
- **Packaging Statistics**: Includes the main packaging statistics per live packaging service.

### Catalogs

This page displays all catalog service configuration data:

- **Catalog**: Lists generic configuration for catalog services.
- **Catalog Assets:** Maps all the packager services that are using catalog services.
- **Catalog Asset Publishing Status:** Displays the state of publishing actions.
- **Catalog Outputs:** Lists the catalog configured outputs.
- **Catalog Output Manifests:** Lists the catalog output manifests.

### Multiplexer Input Redundancy

This page contains data for all multiplexer services that have input redundancy features configured.

### Multiplexer Statistics

This page contains all statistics related to multiplexer services, including the multiplexer service input statistics.

### Servers Overview

This page displays a tree control that provides a structured overview of the server components.

### Servers

This page displays the following tables:

- **Servers**: Lists the server nodes in the system.
- **Software**: Lists the software installed and running on each server.
- **Connectors**: Lists all connectors installed and running on the controller server.
- **Deployment Packages**: Lists the available deployment packages to be used on the **Server Deployment Subpage** (only available if the controller supports the MediaKind subproduct **MDT** and the **MDT API Credentials are set up** properly on the Features page)

It also contains page buttons to the following subpages:

- **Memory & CPU**: Includes detailed information about the server memory and CPU statistics.
- **Input & Output**: Includes detailed information about the server data input and data output traffic statistics.
- **Disks**: Includes detailed information about the server disk statistics.
- **Network**: Includes detailed information about the server network statistics.
- **Server Deployment**: Allows you to create a deployment in the configured cluster manager. Requires Ericsson MDT API.

### Redundancy

This page displays the following tables:

- **Failover Groups:** Lists all the failover groups.
- **Failover Groups Servers:** Lists all the failover server groups.

### Features

On this page, you can configure the credentials for both the **HTTP connection** and the **HTTPS connection - MDT API**.

- The **HTTP connection** uses the **General API Credentials**.
- The **HTTPS Connection - MDT API** uses the **MDT API Credentials.**

This page also allows you to enable or disable polling for specific components.

In addition, it displays the API versions that should be compatible with the selected device branch.

### Alarms

This page displays the **Alarms** table, which includes parameters such as the alarm ID, severity, description, and impacted servers and services.

It also contains a page button to the **History Alarms** subpage, which displays detailed information about past alarms.

### Web Interface

This page displays the web interface of the device. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
