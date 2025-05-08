---
uid: Connector_help_Haivision_Manager
---

# Haivision Manager

The Haivision Manager connector facilitates integration with Haivision's video streaming and media management solutions. It allows users to monitor, control, and automate workflows involving Haivision devices and services. The data source provides information about video streams, device health, and configuration settings, enabling efficient media management in broadcast, corporate, and live event environments. This integration ensures centralized access to critical operational data, streamlining video delivery processes.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 4.1.0              |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

### Initialization

Additional configuration is necessary for a newly created Haivision Manager element. Specifically, an **API key** must be configured to enable communication with the Haivision data source. This key allows the connector to authenticate requests and access the required information from the Haivision system. Ensure the API key is obtained from your Haivision platform and entered in the appropriate parameter field on the **General** page of the element.

## How to use

The connector displays Haivision Manager data. API calls are used to retrieve the device information.

On the **General** page of this connector, you can configure the API key to enable communication with the device.

Via the right-click menu of the SDI, NDI, and IP Outputs tables on the **Outputs** page, you can manage the live stream from a connected field unit, using the Play Stream and Stop Stream options.
