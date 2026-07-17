---
uid: Connector_help_Telenor_EPM_MAM_Offloader
---

# Telenor EPM MAM Offloader

## About

With the **Telenor EPM MAM Offloader** connector, the MAM telemetry forwarded by **Telenor EPM MAM Consumer** elements and the playback session data stored in Parquet files can be collected, pushed into an OpenSearch database, and made available for Kafka forwarding.

## Key Features

- **MAM message offloading**: Buffers the JSON events forwarded by the MAM Consumer elements and periodically writes them to dedicated OpenSearch data streams using bulk requests.
- **Playback sessions offloading**: Reads playback session Parquet files from network shares, offloads OTT sessions to OpenSearch, and archives the processed files.
- **Kafka forwarding**: Exposes ready-to-produce JSON payloads in volatile tables so that MAM events and playback sessions can be forwarded to Kafka topics.
- **Real-time statistics**: Easily view statistics related to the offloading process (rate of messages per type, offload duration, connection status, etc.).
- **Database configuration**: Configure the OpenSearch data stream names and limit how long each underlying index remains in the database through daily rollover and TTL-based cleanup.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Telenor_EPM_MAM_Offloader_Technical).

