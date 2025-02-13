---
uid: Connector_help_Control_By_Web_X-600M_Technical
---

# Control By Web X-600M

This connector retrieves the state and performs minor control functions of Control By Web modules attached to the X-600M.

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (fixed value: *80*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

#### SNMP Traps Connection

This connector uses a Simple Network Management Protocol (SNMP) connection to receive traps and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *162*).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

If the device has **Dashboard and I/O Password Protection** enabled, then the username and password must be inserted on the **General** page.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

Once a valid username and password have been specified, content is retrieved and shown in the tables.

Some control of the relays is available, and data is displayed depending on how the X-600M is configured for each Control By Web device.

Note: Configuration of the names can break the handling of data, so we highly recommend using the default names of each KPI.
