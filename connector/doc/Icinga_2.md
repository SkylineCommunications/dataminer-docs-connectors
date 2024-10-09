---
uid: Connector_help_Icinga_2
---

# Icinga 2

The Icinga 2 platform can poll all the information from an Icinga monitoring system to help monitor network devices, servers, applications, and services, ensuring they are running smoothly and efficiently.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination. **Default port: 443.**

## How to use

On the **Configuration** page, you can configure the following parameters:

- **Entity Import Directory**: Directory where the element will import the devices information from EPM.

- **Entity Export Directory**: Directory from which the element will export the devices inventory information to EPM.

- **System Username**: Username used to retrieve files from a remote directory.

- **System Password**: Password used to retrieve files from a remote directory.
