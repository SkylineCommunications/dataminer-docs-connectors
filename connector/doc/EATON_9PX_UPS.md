---
uid: Connector_help_EATON_9PX_UPS
---

# EATON 9PX UPS

This connector is used to monitor the EATON 9PX UPS device.

The Eaton 9PX is an online UPS featuring ABM technology, which extends battery service life up to 50 percent. It is used in IT, edge networks, healthcare, universities, K-12, industrial automation and harsh electrical environments.

## About

### Version Info

| Range                | Key Features                                                                                                                                                                                                                                              | Based on             | System Impact |
|----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|---------------|
| 1.0.0.x [SLC Main]   | Initial version                                                                                                                                                                                                                                            | -                    | -             |
| 1.1.0.x [Main]       | Gives operators direct control over the UPS's battery protection behavior, early-warning visibility into environment probe connectivity, control over the audible alarm, and richer, more readable alarm reporting.                                    | 1.0.0.x [SLC Main]   | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|-------------------------|
| 1.0.0.x   | 01.22.6523              |
| 1.1.0.x   | 01.22.6523              |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.1.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

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

This connector gives you a complete picture of your Eaton 9PX UPS at a glance — system and battery health, power input/output, bypass status, environmental conditions (temperature and humidity), and digital inputs — all from a single dashboard.

Beyond monitoring, you can also keep a close eye on alarms and fine-tune key device settings remotely, without needing to walk up to the unit.

### Take control of your battery's protection settings

Stay ahead of power issues with full visibility and control over the thresholds that protect your battery's lifespan and your equipment's uptime:

- **Battery Capacity Threshold**: Decide exactly how low the battery charge can go before the UPS shuts down to protect it from over-discharge.
- **Battery Time Remaining Threshold**: Set the runtime cutoff (in seconds) that triggers a low-battery warning, so you get the heads-up you need, when you need it.
- **Battery Safe Restart Threshold**: Make sure your UPS only powers back on once the battery has recovered to a safe charge level, protecting your equipment from repeated power cycling.

These settings are fully adjustable from the connector's Battery Thresholds page.

### Never miss a disconnected sensor

If the connection between the UPS and its Environment Monitoring Probe (EMP) drops, your temperature and humidity readings could silently go stale — without this update, you'd have no way of knowing. Now, the connector clearly reports whether the EMP is communicating normally, has lost communication, or is in an unknown state, so you can act before it becomes a problem.

### Configure the audible alarm to suit your environment

Whether you want the UPS buzzer always on, silenced while running on battery, or completely off, you're now in control — directly from DataMiner:

- **Enabled**: the audible alarm sounds for every alarm condition.
- **Disabled On Battery**: the alarm stays quiet while the UPS is running on battery power.
- **Disabled Always**: the alarm is permanently muted.

### Clearer insight into your output status

The Output Status parameter now also reports *Powered - No Continuity*, giving you a precise picture when the output is powered but the continuity feature is turned off.

### Richer, more readable alarms

The active alarms table now translates even more alarm conditions into clear, human-readable descriptions — covering charger voltage issues, short circuits, emergency switch-offs, missing batteries, thermal overloads, input wiring faults, lost battery communication, on buck/boost/high-efficiency operation, and degraded mode — so you immediately understand what's happening, without needing to decode raw OIDs.
