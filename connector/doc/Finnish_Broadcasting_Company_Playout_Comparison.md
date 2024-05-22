---
uid: Connector_help_Finnish_Broadcasting_Company_Playout_Comparison
---

# Finnish Broadcasting Company Playout Comparison

The Finnish Broadcasting Company Playout Comparison connector enables comparison of planned (MediaGenix WhatsOn/Plasma) vs. actual (TAG MV Probe) DVB components on air.

This connector retrieves data from the MediaGenix WhatsOn/Plasma and TAG MV Probe element.

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

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

After creating an element, you have to specify the TAG and Plasma element IDs on the General page in order to enable the polling of data.

## How to use

You can find all information about the tables on the corresponding pages. On the General page, you can specify the TAG and Plasma element IDs.
