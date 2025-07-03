---
uid: Connector_help_Generic_Ember+_Technical
---

# Generic Ember+

## About

The **Ember+** protocol has been designed to allow the communication between two endpoints, one being the data provider and the other being the consumer. The data provider usually is a piece of hardware that offers a set of controllable parameters, while the consumer may be a control or monitoring system that provides access to these parameters and allows users to control them.

The **Generic Ember+** connector, which is the consumer, is designed to allow monitoring of parameters that are provided via the Ember+ protocol irrespective of the specific device type.

## Configuration

### Connections

#### IP Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host:** The polling IP or URL of the destination.
  - **IP port:** The IP port of the destination (default: 9000).

## How to use

This connector retrieves and presents all the parameters that are available in the Ember+ tree structure of the device.

All the information that can be useful for monitoring can be found in a tree view on the **General** data page and in a table on the **Overview** page.

On the **Configuration** subpage of the Overview page, you can configure whether the label should be included in or excluded from the display key of the **Parameters** table. Note that this is applicable for nodes that have a parameter with a "label" identifier.
