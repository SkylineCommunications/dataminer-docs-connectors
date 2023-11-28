---
uid: Connector_help_Skyline_MDC_Service_Monitoring
---

# Skyline MDC Service Monitoring

This connector can be used to monitor and manage Media Data Center (MDC) related services.
The Manager element can be configured to scan Encoding elements for their service configuration and it will spin up accompanying DataMiner services for each service found on the encoders.

Currently Supported for:
  - East-West
    - Harmonic VOS
  - North-South
    - Kubernetes Manager
    - Linux Platform
    - Huawei IBMC
    - HP ILO

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x \[SLC Main\] | Initial version. | \-           | \-                |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | \-                    | \-                      |

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

To configure new encoder elements that need to be include in the service monitoring:
  - Navigate to the *General* Page
    - Right-click in the Monitoring Configuration Table and select *Add Item...*
      - Main Element: select the encoding element you wish to include for monitoring (E.G. *VOS Cluster 1*)
      - Configuration Platform Element: select the underlying orchestration platform element corresponding to the main element which was selected. (E.G. *Kubernetes Manager Cluster 1*)
      - Services view: the view where the DataMiner service will be stored under (E.G. *Services VOS Cluster 1*)
      - Hardware Type: type of underlying hardware, used to filter the correct data for the service (E.G. *HP ILO*)


### Redundancy

There is no redundancy defined.

## How to use

After the **Initialization Step** (see above), an element using this protocol can collect the service information and start creating DataMiner Services.

You will also be able to monitor which services are under control of the manager element on the *Monitored Services* page.
