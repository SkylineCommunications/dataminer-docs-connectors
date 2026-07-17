---
uid: Connector_help_Telenor_EPM_MAM_Offloader_Technical
---

# Telenor EPM MAM Offloader

## About

In the Telenor DMS, the **Telenor EPM MAM Consumer** elements receive messages from a RabbitMQ server. Some of those messages must be saved in an OpenSearch database. To achieve this, the consumer elements push the messages towards the **Telenor EPM MAM Offloader** element using parameter sets. The offloader element buffers those messages and then sends them periodically to OpenSearch using bulk requests.

In addition to the MAM messages, the connector processes playback session data. It reads Parquet files produced for playback sessions from network shares, offloads the OTT sessions to OpenSearch, and archives the processed files.

For both pipelines, the connector also exposes the processed records as ready-to-produce JSON payloads in volatile tables, so that MAM events and playback sessions can be forwarded to Kafka topics.

The connector therefore runs two independent offloading pipelines:

- **MAM messages**: A buffer accumulates the incoming JSON events. On a short interval, the buffer is drained, each event is parsed and dispatched based on its type, and the results are bulk-written to the matching OpenSearch data stream. Supported message types include error, activity, diagnostics, ContentWise, application system event, change setting, player statistics, EDID, execute action, screen view, open landing page, and playback events.
- **Playback sessions**: On a longer interval, the connector reads the available Parquet files, deserializes them to playback session records, offloads the OTT sessions to OpenSearch, stores all sessions in a volatile table for Kafka forwarding, and moves the processed files to the archive location.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

On the *General* page, the OpenSearch database and playback session file settings must be filled in:

- **User Name**: The OpenSearch user name.
- **Password**: The OpenSearch password.
- **Nodes**: This table lists the nodes in the OpenSearch database. You can add a node by right-clicking the table and selecting **Add Node**.
- **Parquet PBS Files Folder Paths**: The network share paths where the playback session Parquet files are located.
- **Network Path Username**: The user name used to access the network shares that contain the Parquet files.
- **Network Path Password**: The password used to access the network shares that contain the Parquet files.

## How to Use

### Configuration

On the **Configuration** page, you can view statistics related to the number of messages processed, including the offload rate per message type and the offload duration. You can also change the name of the data streams used for indexing each message type, as well as the bulk request size and the offload period.

### Playback Sessions Offloading

On the **Playback Sessions Offloading** page, you can configure the offloading of the playback session Parquet files:

- **Playback Session Index**: The name of the OpenSearch data stream used to store the OTT playback sessions.
- **Playback Sessions TTL**: The number of days a playback session index must remain in the database.
- **Playback Sessions Rate** and **Playback Sessions Offload Duration**: Statistics about the last playback session offload run.

The **Playback Sessions** page shows the volatile table that holds the serialized playback session records, ready to be produced to Kafka.

### Kafka Forwarding Tables

Several volatile tables expose the processed events as ready-to-produce JSON payloads for Kafka producers. Each of these tables is shown on its own page: **Execute Action**, **Screen View**, **Open Landing Page**, **Application Start**, **Application Stop**, and **Playback Events**.

### Rollover

The **Rollover** page displays a table showing all the underlying indexes used by the selected data streams and the number of documents they contain. For each data stream, a new index is created every day around midnight by means of a rollover request. With the **Index TTL** parameter, you can indicate for how many days an index must remain in the database. Indexes older than the configured TTL are deleted automatically.

## Notes

- All OpenSearch data streams use `timeStamp` (camelCase) as the timestamp field, and documents are written using bulk create operations.
- Only playback sessions with an OTT service type are offloaded to OpenSearch; all sessions are stored in the Kafka forwarding table.
- Processed Parquet files are moved from the source folder to the archive folder once offloaded.
