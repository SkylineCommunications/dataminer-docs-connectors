---
uid: Connector_help_Electrosys_TL6F5K
---

# Electrosys TL6F5K

The Electrosys TL6F5K is a liquid-cooled solid state transmitter for digital broadcasting (DVB-T2), operating in a frequency range from 470 to 870 MHz.

This connector monitors the activity of the **TX transmitter** via SNMP.

## About

### Version Info

| Range              | Key Features     | Based on     | System Impact     |
|--------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main] | Initial version  | -            | -                 |

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

## How to use

The element consists of the following data pages:

- **General**: Displays general transmitter information, including measurements from the TX transmitter, such as Forward Status, TX Forward Power, etc.
- **System Information**: A subpage of the general page that provides general information about the transmitter system, including System Name, System Description, etc.
- **TX Control**: Displays control status information for the transmitter, such as Power Set, RF, Operational Mode, etc.
- **Dual Drive**: Displays status information for Exciter A and Exciter B in the transmitter.
- **Cooling**: Displays the status information for the cooling systems in the transmitter, including Water Temperature, Heat Exchange, Pump System, etc.
- **CAN Bus Connection**: Contains a table displaying the connection status for the CAN bus in the transmitter.
