---
uid: Connector_help_Skyline_MDC_Service_Monitoring
---

# Skyline MDC Service Monitoring

This connector can be used to monitor and manage Media Data Center (MDC) related services.

The manager element can be configured to scan encoding elements for their service configuration. It will spin up accompanying DataMiner services for each service found on the encoders.

This connector is currently supported for:

- East-west:

  - Harmonic VOS

- North-south:

  - Kubernetes Manager
  - Linux Platform
  - Huawei IBMC
  - HP ILO

## About

### Version Info

| Range              | Key Features     | Based on    | System Impact    |
|--------------------|------------------|-------------|------------------|
| 1.0.0.x [SLC Main] | Initial version. | -           | -                |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

#### Connector Installation

To be able to create and monitor new services with this connector, one or more service templates must be installed on the DataMiner System. Please verify that the service templates have been successfully installed with the connector package and are accessible through Cube.

The Cube module **Service Templates** should contain at least the templates **VOS IPTV** and **VOS OTT**.

#### Service Monitoring Initialization

To configure new encoder elements that need to be included in the service monitoring:

1. Create an element running the **Skyline MDC Service Monitoring** connector (if no element running this connector exists yet).

1. Navigate to the **General** page.

1. Right-click in the **Monitoring Configuration Table** and select **Add Item**.

1. Configure the following settings for the item:

   - **Main Element**: Select the encoding element you wish to include for monitoring (e.g. *VOS Cluster 1*).

   - **Configuration Platform Element**: Select the underlying orchestration platform element corresponding to the main element you selected (e.g. *Kubernetes Manager Cluster 1*).

   - **Services View**: Specify the view where the DataMiner service will be located (e.g. *Services VOS Cluster 1*).

   - **Hardware Type**: Specify the type of underlying hardware. This is used to filter the correct data for the service (e.g. *HP ILO*).

## How to use

After you have [initialized the element](#initialization), it can collect the service information and start creating DataMiner services.

On the **Monitored Services** page, you can monitor which services are under control of the manager element.
