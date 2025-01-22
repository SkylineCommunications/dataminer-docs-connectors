---
uid: Connector_help_Eutelsat_TAOS_Manager
---

# Eutelsat TAOS Manager

Each DataMiner element that was created based on the Eutelsat TAOS Manager connector represents a satellite. These elements collect telemetry from Generic Flexible Payload (GFP) equipment. GFP equipment was built for Ku-band Fixed Satellite Service (FSS) relying on geostationary satellites positioned at approximately 36,000 kilometers above the equator. It includes the following items:
- Agile Integrated Down-converter Assembly (AIDA) that converts the frequency of all signals received by the satellite to the required transmit frequency.
- Routing And Switching Equipment (RASE), a sold-state switch matrix which allows connectivity between any pair of satellite uplink and downlink beams.
- Single Channel Agile Converter Equipment (SCACE), a variable bandwidth frequency converter which adjusts the transponder center frequency, gain and bandwidth.
- Microwave Power Module (MPM) to amplify the required transmit signal prior to retransmission.

The element will connect to two external databases (main and backup) to collect telemetry data. It will display the data from the database which is most up-to-date. 

A unique feature of this connector is that users are able to define alarm threshold directly through the element, which will update the alarm template xml files.

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

Additional configuration of parameters is necessary in a newly created element. The Satellite ID needs to be configured on the Setup page. Next to this, the main and backup databases need to be configured. The addresses, user names and passwords need to be entered on the **Setup** page.

### Redundancy

No redundancy is defined in the connector.

## How to use

If neither the main database or the backup database are not accessible, the connector will go through the list of redundant databases to try to assign a new main or a new backup.

Every 20 seconds, the main and backup databases are read using a single MySQL query. The content of the backup database is compared to the content of the main database. If a parameter is present in both databases, the value with the latest Update Time is forwarded to the tables on the pages SCACE, AIDA, ..., BFN. This action should not take longer than 14 minutes.

If the action to read both databases and process their content takes 14 minutes, the extra thread will be interrupted and a message will be printed in the element log file.

The element will indicate timeout if both main and backup databases are not accessible. The **General Overview** table is cleared if the element indicates timeout.

### Configuration Page

A manual database read can be triggered from here as well as a manual alarm template sync.

The **Association Table** can be exported to a CSV file. Adding and removing Unit IDs can be done from the bottom of this page.

### Setup Page

If the main or the backup database is not accessible, the connector will try to access one of the redundant databases. The redundant databases are shown in the **Database** table.

A **Disable Force Retrieval** parameter instructs to take the two databases into account. This parameter can also be configured to only take the main one into account or only the backup.

### Full Load Page

A manual database read can be triggered from here.