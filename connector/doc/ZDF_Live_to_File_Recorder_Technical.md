---
uid: Connector_help_ZDF_Live_to_File_Recorder_Technical
---

# ZDF Live to File Recorder

Live to File Recorder Connector provides monitoring capabilities for the L2F Master and L2F Recorder systems. It enables to query and evaluate the hardware availability, recorder/master process status, and recording status verification.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- IP address/host: IP address/host on which recorders are hosted.
- IP port: IP Port of recorders.