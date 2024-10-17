---
uid: Connector_help_Shelly_Pro_1PM
---

# Shelly Pro 1PM

This connector allows you to monitor and control the Shelly Pro 1PM one-phase, 1-channel relay supporting up to 16A.
Equipped with an integrated power meter, Shelly Pro 1PM allows you to measure the precise power consumption of all automated lights or heavier appliances. Different types of actions, scenarios, and schedules can be set to sync your environment to your daily activities or business needs. Additionally, Shelly Pro 1PM has scripting functionalities for custom automation scenes based on external data or various occurrences.

## About

### Version Info

| Range                | Features             | Based on     | System Impact     |
|----------------------|----------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Relay control.       | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 1.0.8                  |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *80*)]
  - **Device address**: [The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.]

### Initialization

No additional configuration is needed.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### Relay

On this page you can monitor and control the inputs and relay configuration.

### Status

This page allows you to monitor the energy, power, voltage, current and temperature and to configure limits.