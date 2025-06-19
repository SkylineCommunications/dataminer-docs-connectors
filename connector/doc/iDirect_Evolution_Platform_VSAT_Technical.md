---
uid: Connector_help_iDirect_Evolution_Platform_VSAT_Technical
---

# iDirect Evolution Platform VSAT

## About

The iDirect Evolution Platform VSAT connector integrates iDirect NMS data into DataMiner. It retrieves terminal configuration, performance statistics, and event data from MySQL databases, enabling real-time monitoring across your VSAT network.

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any IP or hostname during element creation.

> [!NOTE]
> This is a virtual connector, so it does not produce traffic in the Stream Viewer.

## How to Use

### Configuration Page

This page allows you to manage the connector’s polling, cleanup, and provisioning settings.

- **Database Configuration**: Main table to define and manage all iDirect database connections.
  - **Server IP Address**: IP of the MySQL server.
  - **Username / Password**: Credentials for access.
  - **Type**: Configuration or Statistics.
  - **Polling**: Enable/disable and set polling interval.
  - **Hub ID**: Unique ID per iDirect NMS.
  - **NMS Name**: Logical name used for grouping/aggregation.

  > Each iDirect system typically includes one configuration database (`nms`) and one or more statistics/event databases (`nrd_archive`). Even if hosted on the same server, these must be entered separately.

- **DB Polling Config**: Configure which data types (Config, Statistics, Events) to poll and how often.
- **DB Polling Status**: Shows last polling times, execution results, and includes manual trigger buttons.
- **Auto Clear**: Manages how long events are retained before being cleaned up. Supports max age, count, and cleanup frequency.
- **VLAN Config**: Cleanup settings for VLAN event tables.
- **EPM Toggle**: Enables optional integration with Skyline EPM Platform VSAT GEO for provisioning and circuit tracking.

### Collector Setup Page

This page handles provisioning file processing, CMDB integration, and retention settings for removed entities.

#### CMDB File Integration

The connector exports and imports remote circuit metadata using CMDB-formatted files.

- **Exported File Format**: `DMAID_ElementID_CC.xml`
- **Imported File Format**: `DMAID_ElementID_CP.json`
- **File Path**: Set the directory where files will be written to or read from.
- **Directory Type**: Choose between Local or Remote directories.
- **Processing Interval**: Define how often the system checks for new files.

> The imported CMDB data populates the **Circuit Overview** table, allowing DataMiner to display detailed circuit-level information, including location, device types, service plans, and interfaces.

##### Example: Exported CC File (XML)

```xml
<circuits>
  <circuit>
    <circuitId>S0000000001</circuitId>
    <circuitAlias>ExampleCircuit001</circuitAlias>
    <status>Active</status>
    <espCustomerName>Sample Customer</espCustomerName>
    <espLocationName>samplelocation</espLocationName>
  </circuit>
</circuits>
```

##### Example: Imported CP File (JSON)

```json
{
  "circuits": [
    {
      "circuitId": "S0000000001",
      "circuitAlias": "ExampleCircuit001",
      "status": "Active",
      "customerName": "Sample Customer",
      "espCustomerShortName": "sample",
      "espLocationName": "samplelocation",
      "devices": [
        {
          "deviceType": "Modem",
          "model": "X7",
          "serialNumber": "123456789",
          "interfaces": [
            {
              "interfaceType": "eth0",
              "ipAddress": "192.168.1.10",
              "vlan": 10
            }
          ]
        }
      ]
    }
  ]
}
```

#### ID File Settings (EPM Integration)

If EPM integration is enabled:

- **ID File Import / Export**: Manages CSV-based provisioning files for assigning unique IDs to entities.
- **ID File Path**: Set the remote directory used by the Skyline EPM Platform VSAT GEO.

#### Entity Removal

- **Entity Removal Path**: Directory where removed entity records are stored.
- **Retention Settings**: Configure how long removed entries are kept before cleanup.
- **Automatic Cleanup**: Optionally enabled; entities are deleted after the configured retention period.
- **Manual Cleanup**: Use the **Remove All** button to immediately clear removed entries.

> [!NOTE]
> The data polled from the configured databases is displayed across multiple tables in the element, including Remotes, Circuits, Hub Networks, Linecards, and Events.
