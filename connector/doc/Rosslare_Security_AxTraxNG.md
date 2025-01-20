---
uid: Connector_help_Rosslare_Security_AxTraxNG
---

# Rosslare Security AxTraxNG

AxTraxNG is a complete server-client software management that enables setting physical access control policy across organizations that is available in multiple languages and date formats. The server manages thousands of networked access control panels and system users. With Rosslare’s SDK tool AxTraxNG also leverages easy integration and deployment of various applications in security, safety, time and attendance and more.

This connector uses a HTTP connection to communicate with the device.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | ac215v04_08_23      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP.
- **IP port**: The IP port of the destination.

## How to use

The **General** page displays details about available networks in Networks table. General page contains  **Panels**, **Doors**, **Readers** and **Outpits** subpages. On each subpage user can find data in table related to that page.
On **Departments** page, user can find tables for each department. Each table contains users from specified department.
The **Cards** page displays table with all user cards on the server.
