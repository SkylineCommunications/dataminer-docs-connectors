---
uid: Connector_help_Hessischer_Rundfunk_ABR_Audio_Monitoring_Service_Technical
---

# Hessischer Rundfunk ABR Audio Monitoring Service

The **ABR Audio Monitoring Service** is a customer specific protocol created and designed as an enhanced service protocol. On creation of a service, the protocol can be used to create an enhanced element to monitor and aggregate the overall audio alarm status.

Individual alarm statusses are available as:
- Encoding Bitrate Status
- Probe Download Status.

## About

### Version Info

|Range                  |Features                                                    |Based on  |System Impact  |
|-----------------------|------------------------------------------------------------|----------|---------------|
|1.0.0.x [SLC Main]     |Initial version: Monitor the overall channel status         |-         |-              |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     | - (Applicable for all related services)         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### Service Connection

For more information on how to apply this service protocol to create an enhanced service element, please refer to our Documentation on [Applying Service Template](https://docs.dataminer.services/user-guide/Basic_Functionality/Services/Service_templates/Applying_service_templates.html).

## How to use

You can find all the information you need to monitor the overall channel status on the General data page.

## Notes

This enhanced service protocol was designed for a specific project and is not expected to be reused in general.
