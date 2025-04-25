---
uid: Connector_help_Work_Microwave_AX60_Series_Modulator_Technical
---

# Work Microwave AX60 Series Modulator

## About

The AX60 Series Modulator is designed to support high-speed IP connectivity and advanced modulation schemes up to 256APSK. It provides robust and flexible data transmission capabilities, making it suitable for a wide range of applications, including governmental, IP networking, and space communications. The modulator supports both native network operation and data streaming over IP, ensuring seamless integration into modern communication systems.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

Once initialized, the element will display the **Modulator Configuration**, **Single TS Configuration**, **Single TS Input**, **Carrier ID**, **Data Interface**, **System Monitor**, **Temperatures**, **Modulator**, and **ACM** pages with their respective KPIs, many of which can be configured.
