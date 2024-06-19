---
uid: Connector_help_Ciena_8114
---

# Ciena 8114

This connector monitors the activity of the Ciena 8114 router and the relevant data retrieved from it. The Ciena 8114 is an IP/optical service aggregation router. This router provides aggregation to efficiently fill higher capacity links within both the metro access and aggregation tiers, minimizing the number of router assets required in the core.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | saos-06-14-00-0337     |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Creation

#### SNMP Connection – Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## Usage

The element created with this connector mainly contains pages where the **system**, **modules**, **sensors**, and **interfaces** are monitored. You can activate alarm monitoring on any parameter to be kept aware of its status.
