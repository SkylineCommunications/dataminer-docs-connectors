---
uid: Connector_help_Eutelsat_TAOS_Manager
---

# Eutelsat TAOS Manager

Each DataMiner element created with the Eutelsat TAOS Manager connector represents a satellite. These elements collect telemetry from Generic Flexible Payload (GFP) equipment. GFP equipment is built for the Ku-band Fixed Satellite Service (FSS) relying on geostationary satellites positioned at approximately 36,000 kilometers above the equator. It includes the following items:

- Agile Integrated Down-converter Assembly (AIDA), which converts the frequency of all signals received by the satellite to the required transmit frequency.
- Routing And Switching Equipment (RASE), a solid-state switch matrix that allows connectivity between any pair of satellite uplink and downlink beams.
- Single Channel Agile Converter Equipment (SCACE), a variable bandwidth frequency converter that adjusts the transponder center frequency, gain, and bandwidth.
- Microwave Power Module (MPM), which amplifies the required transmit signal prior to retransmission.

The element will connect to two external databases (main and backup) to collect telemetry data. It will display the data from the database that is most up to date.

A unique feature of this connector is that users can define alarm thresholds directly through the element, which will update the alarm template XML files.

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

Additional configuration of parameters is necessary in a newly created element. On the **Setup** page, you will need to configure the **Satellite ID**, as well as the addresses, user names, and passwords for the **main and backup databases**.

## How to use

If neither the main database nor the backup database are accessible, the connector will go through the list of redundant databases to try to assign a new main or a new backup.

Every 20 seconds, the main and backup databases are read using a single MySQL query. The content of the backup database is compared to the content of the main database. If a parameter is present in both databases, the value with the latest update time is forwarded to the tables on the pages SCACE, AIDA, ..., BFN. This action should not take longer than 14 minutes.

If the action to read both databases and process their content takes 14 minutes, the extra thread will be interrupted, and a message will be printed in the element log file.

The element will indicate a timeout if both main and backup databases are not accessible. The **General Overview** table is cleared if the element indicates a timeout.

### Configuration Page

A manual database read can be triggered from here as well as a manual alarm template sync.

The **Association Table** can be exported to a CSV file. At the bottom of this page, you can add and remove unit IDs.

### Setup Page

If the main or the backup database is not accessible, the connector will try to access one of the redundant databases. The redundant databases are shown in the **Database** table.

With the **Disable Force Retrieval** parameter you can instruct the connector to take the two databases into account. This parameter can also be configured to take only the main database or only the backup database into account.

### Full Load Page

A manual database read can be triggered from here.
