---
uid: Connector_help_Warner_Bros_Discovery_DAZN_Live_Stream_API
---

# Warner Bros Discovery DAZN Live Stream API

The Warner Bros Discovery Sports DAZN Live Stream API connector can be used to ingest and display the DAZN Live feeds (<https://docs.daznservices.com/docs/live/index.html>).

## Key Features

- **Real-time overview**: View all planned live feeds and detect missing data in one go with the DAZN Live Stream API connector.
- **Planning**: Ingested live feeds will be automatically migrated to MediaOps jobs to trigger the workflows and orchestration per feed automatically.

## Use Cases

### Automatic Orchestration and Monitoring of the DAZN Live Feeds

**Challenge:** All defined and planned DAZN Live feeds need to be orchestrated on the related Ateme Titan encoders to run the actual events, and the live feeds have to be linked to MediaOps workflows.

**Solution:** The connector ingests, manages, and links the DAZN Live feeds with the MediaOps workflows in an automated manner.

**Benefit:** Automatic MediaOps events are handled for anything and everything available from the DAZN API.

## Technical Info

### Prerequisites

- **DAZN API permissions** are needed to retrieve and ingest the data.
- **Network access** to the DAZN API is essential, including IP address and UDP port (default: 443).

> [!NOTE]
> For in-depth information on configuring and using the DataMiner connector, refer to the [Technical help page](xref:Connector_help_Warner_Bros_Discovery_DAZN_Live_Stream_API_Technical).

