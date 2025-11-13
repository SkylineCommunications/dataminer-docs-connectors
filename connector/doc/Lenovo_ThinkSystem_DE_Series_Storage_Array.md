---
uid: Connector_help_Lenovo_ThinkSystem_DE_Series_Storage_Array_Technical
---

# Lenovo ThinkSystem DE Series Storage Array

## About

The Lenovo ThinkSystem DE Series Storage Array is a family of enterprise-grade storage systems offering both hybrid and all-flash configurations. It is designed for demanding workloads such as analytics, technical computing, and large-scale virtualization.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *82*)]
  - **Device address**: [The bus address of the device. If the proxy server must be bypassed, specify *BypassProxy*.]

### Initialization

Credentials must be provided on the Security Page (General > Security).

*Note: If no credentials are required for the communication, **dummy** data must still be provided for the **Username** and **Password** fields in order to trigger the polling mechanism.*

After providing credentials, the connector will start polling the available **Storage Systems**. All available Storage Systems can be viewed on the General Page.

If only a single Storage System is available, the connector will automatically select it and start polling all related data.

If multiple Storage Systems are available, you must provide the desired Storage System ID in the **Storage System Polling ID** parameter located below the Storage Systems table on the General Page.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The connector uses a Poll Manager to dynamically poll the desired Storage System data (General > Poll Manager).

**Poll State** and **Poll Frequency** can be adjusted as needed.

*Note: In case of a communication issue, the connector includes an HTTP Debug Page where HTTP traffic can be reviewed. This page is hidden by default but can be enabled using the **Show HTTP Debug Page** parameter (General Page).*
---
uid: Connector_help_Lenovo_ThinkSystem_DE_Series_Storage_Array_Technical
---

# Lenovo ThinkSystem DE Series Storage Array

## About

The Lenovo ThinkSystem DE Series Storage Array is a family of enterprise-grade storage systems offering both hybrid and all-flash configurations. It is designed for demanding workloads such as analytics, technical computing, and large-scale virtualization.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *82*)]
  - **Device address**: [The bus address of the device. If the proxy server must be bypassed, specify *BypassProxy*.]

### Initialization

Credentials must be provided on the Security Page (General > Security).

*Note: If no credentials are required for the communication, **dummy** data must still be provided for the **Username** and **Password** fields in order to trigger the polling mechanism.*

After providing credentials, the connector will start polling the available **Storage Systems**. All available Storage Systems can be viewed on the General Page.

If only a single Storage System is available, the connector will automatically select it and start polling all related data.

If multiple Storage Systems are available, you must provide the desired Storage System ID in the **Storage System Polling ID** parameter located below the Storage Systems table on the General Page.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The connector uses a Poll Manager to dynamically poll the desired Storage System data (General > Poll Manager).

**Poll State** and **Poll Frequency** can be adjusted as needed.

*Note: In case of a communication issue, the connector includes an HTTP Debug Page where HTTP traffic can be reviewed. This page is hidden by default but can be enabled using the **Show HTTP Debug Page** parameter (General Page).*
