---
uid: Connector_help_Eutelsat_TAOS_Manager
---

# Eutelsat TAOS Manager

Each DataMiner element created with the Eutelsat TAOS Manager connector represents a satellite. These elements collect telemetry from Generic Flexible Payload (GFP) equipment. GFP equipment is built for the Ku-band Fixed Satellite Service (FSS) relying on geostationary satellites positioned at approximately 36,000 kilometers above the equator. It includes the following items:

- Agile Integrated Down-converter Assembly (AIDA), which converts the frequency of all signals received by the satellite to the required transmit frequency.
- Routing And Switching Equipment (RASE), a solid-state switch matrix that allows connectivity between any pair of satellite uplink and downlink beams.
- Single Channel Agile Converter Equipment (SCACE), a variable bandwidth frequency converter that adjusts the transponder center frequency, gain, and bandwidth.
- Microwave Power Module (MPM), which amplifies the required transmit signal prior to retransmission.

The element will connect to four external databases to collect telemetry data. Next to the regular CMRS main and backup databases, the SCC Gateway main and backup databases are also queried. The connector will compare the data and show the telemetry from the database that is most up to date.

A unique feature of this connector is that users can define alarm thresholds directly through the element, which will update the alarm template XML files.

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

Additional configuration of parameters is necessary in a newly created element. On the **Setup** page, you will need to configure the **Satellite ID**, as well as the addresses, user names, and passwords for the **Main and Backup Database** and the **SCC Gateway Main and Backup Database**.

Redundant databases can be configured in the **Database** table by right-clicking inside the table > Add Database > and completing the form. Every field on the form must be filled in to be able to save the configuration. The context menu also provides a Remove Database button to clean old or unused databases.

## How to use

If neither the main database nor the backup database are accessible, the connector will go through the list of redundant databases to try to assign a new main or a new backup.

Every 20 seconds, the main and backup databases are read using a single MySQL query. The content of the backup database is compared to the content of the main database. If a parameter is present in both databases, the value with the latest update time is forwarded to the tables on the pages SCACE, AIDA, ..., BFN. This action should not take longer than 14 minutes.

If the action to read both databases and process their content takes 14 minutes, the extra thread will be interrupted, and a message will be printed in the element log file.

The element will indicate a timeout if both main and backup databases are not accessible. The **General Overview** table is cleared if the element indicates a timeout.

Please don't expect the Stream Viewer to show something. All traffic towards the databases is starting from inside a QAction (C# code). As a result we cannot make use of the Stream Viewer.

### General Overview Page

A healthy element should show the fields **_SCC_HEARTBEAT** and **_SCC_TM_STATUS** inside the **General Overview** table.

Greyed out standalone parameters indicate that not every database is successfully queried. Please check the Force Retrieval page to see if the element settings are correct.

### Force Retrieval Page

With the **Force Retrieval** parameter set to Disabled you can instruct the connector to take the four databases into account. This parameter can also be configured to take only the main database or only the backup database into account.

It is also possible to configure a duration in minutes to limit the time the force retrieval will occur.

### SCACE - BFN Pages

The **Source DB** column which is part of every table shown on these pages will indicate if the field is coming from the CMRS main or backup database, or from the SCC Gateway main or backup database. The logic that defines wheter the field should be taken from CMRS or SCC Gateway is hardcoded inside the connector. This logic cannot be changed at runtime.

### Configuration Page

A manual database read can be triggered from here as well as a manual alarm template sync.

The Import CSV File dropdown is empty by default. To make the options available, press the **Refresh List** button.

The **Association Table** can be exported to a CSV file which will be stored in the C:\Skyline DataMiner\Documents\Eutelsat TAOS Manager directory.

At the bottom of this page, you can add and remove unit IDs.

### Setup Page

If the main or the backup database is not accessible, the connector will try to access one of the redundant databases. The redundant databases are shown in the **Database** table.

### Full Load Page

The **Full Load** tables show all available fields. These tables don't use the Association Table to limit their content. In here you will find SCACE fields next to MPN fields and BFN fields.

A manual database read can be triggered from here.
