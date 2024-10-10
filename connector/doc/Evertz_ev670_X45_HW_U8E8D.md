---
uid: Connector_help_Evertz_ev670_X45_HW_U8E8D
---

# Evertz ev670-X45-HW U8E8D

The purpose of this SNMP connector is to monitor the Evertz EV670-X45-HW device.

## About

The Evertz ev670-X45-HW U8E8D can have up to 18 Outputs

### Version Info

| Range                                  | Description                                                         | DCF Integration | Cassandra Compliant |
|----------------------------------------|---------------------------------------------------------------------|-----------------|---------------------|
| 1.0.0.x                    | Initial version                                                     | Yes             | No                  |


## Configuration

### Connections

#### SNMP main connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device. The default value is *public*.
- **Set community string**: The community string used when setting values from the device. The default value is *private*.
- **Number of retries**: 0

## Usage

### General



