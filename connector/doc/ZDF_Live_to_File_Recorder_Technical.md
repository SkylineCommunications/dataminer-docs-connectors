---
uid: Connector_help_ZDF_Live_to_File_Recorder_Technical
---

# ZDF Live to File Recorder

## About

The Live to File Recorder connector provides monitoring capabilities for the L2F Master and L2F Recorder systems. It allows you to monitor the hardware availability, recorder/master process status, and recording status verification.

## Configuration

### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- IP address/host: IP address/host on which recorders are hosted.
- IP port: IP Port of recorders.

## How to Use

When creating the element, the user must specify the **IP address/host** and **Port** where the recorders are hosted. Once the element is created with the correct host and port, information about all recorders will be displayed in the tables