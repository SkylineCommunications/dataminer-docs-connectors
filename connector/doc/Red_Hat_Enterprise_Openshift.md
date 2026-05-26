---
uid: Connector_help_Red_Hat_Enterprise_OpenShift
---

# Red Hat Enterprise OpenShift

## About

Red Hat Enterprise OpenShift allows full management of enterprise Kubernetes deployments. This connector monitors the entire north–south infrastructure, from containers to PODs and nodes. It also includes real-time statistics of the main elements.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP address of the device.
- **IP port**: The IP port of the device (default: *6443*).
- **Device address**: The device address (default: *ByPassProxy*).

To set up the connection, after element creation, enter a valid bearer token on the **General** page. If the token is valid, the Authorization State will change to *Authorized*.

#### HTTP Connection - Alerts App

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP address of the device (should refer to the Alertmanager endpoint).
- **IP port**: The IP port of the device (default: *443*).
- **Device address**: The device address (default: *ByPassProxy*).

The same authorization applies to this connection as the main HTTP connection. Specifying the **Token** on the **General** page is sufficient.

## How to Use

### General

The **General** page contains the main connection data. OpenShift uses the OAuth authentication method, based on bearer tokens. The provided token should be retrieved from a Service Account secret in OpenShift that does not expire. If other secrets are used, it is required to manually enter the newly generated secret each day; otherwise, the element will go into timeout and into the *Unauthorized* state.  
You can also verify the authorization state here, which reflects the login status. Using the refresh data button, you can manually trigger immediate polling of all data.

### Alerts

The OpenShift cluster exposes an Alertmanager endpoint to manage all active alerts in the system. An overview of all alerts, including their severity, reason, linked POD, and linked node, can be consulted here.

### Namespaces

The namespaces list, originating from Kubernetes, is displayed on this page. This includes the namespace name, labels, status, age, creation timestamp, resource version, and self-link.

### Nodes

This page contains a list of nodes and full node statistics. From each node, you can navigate to the respective conditions, statistics, and PODs.

### PODs

This page contains a list of PODs and full POD statistics. For every POD, you can view containers, conditions, volumes, events, and more.

### Services

This page displays all services, organized per namespace and node.

### Labels

An overview of all available labels per node and POD.
