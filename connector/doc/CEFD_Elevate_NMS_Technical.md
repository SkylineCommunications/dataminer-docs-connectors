---
uid: Connector_help_CEFD_Elevate_NMS_Technical
---

# CEFD Elevate NMS

## About

The CEFD Elevate NMS connector integrates with Comtech’s ELEVATE platform to monitor and manage VSAT network infrastructure. The ELEVATE platform is a software-defined solution that supports both MF-TDMA and H-DNA waveforms, enabling flexible and dynamic switching between transmission modes. It allows the deployment of scalable and customizable private VSAT networks, supporting complex topologies and hybrid satellite bandwidth configurations. This connector retrieves operational data from the ELEVATE system, providing visibility into key performance and configuration parameters within the DataMiner environment.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

> [!NOTE]
> It is important to specify whether the connection uses **HTTP** or **HTTPS**, as different devices may only support one of these protocols. Selecting the correct protocol ensures proper communication and prevents connection failures.

### Initialization

When you have created the element, you will need to provide a username and password on the General page. When this is done, the connector will generate an authentication token, which is used for all subsequent communication with the system. If the authentication is successful, a confirmation message is displayed, and a polling timer is started to initiate regular data polling.

## How to Use

The connector communicates with the Elevate API using JSON over HTTP to retrieve and display monitoring data within DataMiner.

- **General**: This is the main page, where you will need to enter the required credentials to allow authentication. There is a **Networks Filter** subpage that allows filtering of network data, enabling you to exclude specific networks from being displayed. **Polling Configuration** provides control over the polling behavior of the connector, including defining the polling interval and optionally disabling specific API calls.

- **Networks**: This section provides an overview of available networks as well as detailed performance metrics for monitoring their operational status.

- **Inroute Controllers**: This section provides detailed monitoring of inroute controllers, including performance metrics, detected faults, modulation and coding (Modcods) details, TDMA load distribution, and ACM (Adaptive Coding and Modulation) information.

- **Outroute Controllers**: This section provides detailed monitoring of outroute controllers, including performance metrics, detected faults, modulation and coding (Modcods) details, and ACM (Adaptive Coding and Modulation) information.

- **VNOs**: This section offers a summary of all Virtual Network Operators, with key status indicators, active sessions, and general health metrics for quick monitoring. The VNOs Performance section delivers detailed insights into each VNO's network performance, including traffic load, throughput, error rates, and trend analysis over time.

- **Stations**: This section provides an overview of station performance metrics, detected faults, and TDMA-related configuration and operational details.
