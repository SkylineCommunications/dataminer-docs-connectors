---
uid: Connector_help_Ericsson_MFVP
description: "Monitor Ericsson MFVP in DataMiner to trace live video workflows, track server health, and spot failover, packaging, and publishing issues."
---

# Ericsson MFVP

## About

The Ericsson MFVP connector gives you a single view of an Ericsson MediaFirst Video Processing (MFVP) platform, which is used to encode, package, and deliver live and on-demand video. It brings the health of the servers, the media workflows running on them, and the resulting alarms into DataMiner, so operations teams can follow the full delivery chain from source to published output.

## Key Features

- **End-to-end workflow visibility**: Follow each live channel from its inputs, through processing and encoding, to its outputs, so you can see where in the chain an issue occurs.

- **Server and service health**: Monitor the servers hosting your video services, including processor, memory, disk, and network load, and see which services run on which server.

- **Platform alarm integration**: Platform alarms and alarm history are presented in DataMiner next to the rest of your infrastructure, so there is no need to check a separate application.

- **Failover and redundancy awareness**: Keep track of failover groups and redundant multiplexer inputs, so you know whether your backup paths are ready when needed.

- **Packaging and catalog overview**: Check live packaging, DVR recording, catalogs, assets, and publishing status to confirm that content reaches your audience as expected.

## Use Cases

### Finding the Source of a Live Channel Problem

**Challenge**: When a live channel degrades, operators have to work out whether the cause is the incoming signal, the encoding, or the output, often across several screens.

**Solution**: The connector presents input, processing, encoding, and output status together, along with monitoring and statistics for each stage.

**Benefit**: Operators locate the faulty stage faster and reduce the time viewers are affected.

### Keeping Backup Paths Trustworthy

**Challenge**: Redundancy only helps if the backup is healthy. Issues on a standby server or input often go unnoticed until failover is triggered.

**Solution**: Failover groups, server status, and multiplexer input redundancy are monitored continuously and can raise alarms in DataMiner.

**Benefit**: Teams are warned about weakened redundancy in advance and can fix it before it affects the service.

## Technical Information

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Ericsson_MFVP_Technical).
