---
uid: Connector_help_Evertz_Scorpion_18_MIO-DD4-3G
---

# Evertz Scorpion 18 MIO-DD4-3G

The Evertz SCORPION 18 MIO-DD4-3G is a dual-slot module designed for the SCORPION 18 media processing platform. It provides advanced data de-embedding and signal monitoring capabilities from 3G/HD-SDI video streams. The DataMiner connector for the MIO-DD4-3G enables seamless SNMP-based monitoring and management, allowing operators to supervise system health, de-embedded data, and alarm conditions in real time.
## Key Features

- SNMP-based monitoring: Leverages SNMP to communicate with the MIO-DD4-3G module, enabling efficient data retrieval and control.

- Data de-embedding: Supports configuration and de-embedding state control for up to 3 serial data streams as well as display and monitoring of the resulting SCTE104 data.
    ![Serial Output](~/connector/images/Evertz_Scorpion_18_MIO-DD4-3G_Serial_GPI.png)

- GPO configuration and status: Supports configuration of up to 8 GPOs by defining GPO source, polarity, delay and hold duration. For each GPO, the conenctor provides a status indicator specifying whether or not the GPO is actived or not.
    ![GPO](~/connector/images/Evertz_Scorpion_18_MIO-DD4-3G_GPO_Controls.png)
    ![GPO](~/connector\images\Evertz_Scorpion_18_MIO-DD4-3G_GPO_Status.png)


- Alarm integration: Enables real-time alarm generation in DataMiner for performance metrics including Device Temperature, GPIO Faults, GPO Status, and various monitored SCTE104 parameters.

## Use Cases

### Centralized Monitoring for Live Production

**Challenge**: A live broadcast control room needs visibility into multiple SCORPION MIO-DD4-3G modules for proactive signal and data flow monitoring.

**Solution**: The DataMiner connector centralizes SNMP monitoring of all deployed modules, giving operators access to real-time status, GPO states, and de-embedded data activity.

**Benefit**: Enhances operational awareness and enables faster response to signal anomalies or embedded data issues.

### Automated GPO Monitoring

**Challenge**: A broadcaster needs to monitor the DD4 module's GPO triggers intended for ad insertions to ensure that SCTE104 messages are being detected and handled appropriately.   

**Solution**: With the MIO-DD4-3G connector, DataMiner alarms can be generated when GPOs unexpectedly become inactive.

**Benefit**: Enables proactive monitoring for GPO based workflows to increase operational up-time on the conencted systems.

## Technical info

> [!NOTE]
> For in-depth information on configuring and using the DataMiner connector for Evertz Scorpion 18 MIO-DD4-3G, refer to the [Technical help page](xref:Connector_help_Evertz_Scorpion_18_MIO-DD4-3G_Technical).
