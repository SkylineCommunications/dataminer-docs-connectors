---
uid: Connector_help_Dell_M1000e_Collector
---

# Dell M1000e Collector - Dell M1000e Remote

The **Dell M1000e Collector** connector communicates with multiple external **Dell Poweredge** devices and collecs basic device indicators.

This connector communicates using SNMPv2. It allows the monitoring and trending of all statuses and readings from remote **Dell M1000e** devices. It can optionally export each Dell M1000e device as a virtual element.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## How to use

On the **Configuration** page, set the **File Import Path**, **import** the CSV file with all the Dell M1000e device information, and set **Polling Status** to *Enabled*.
