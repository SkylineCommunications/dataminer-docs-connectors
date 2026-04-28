---
uid: Connector_help_Nokia_7750_SR_VSA_Technical
---

# Nokia 7750 SR VSA

## About

The Nokia 7750 SR VSA connector uses an SNMP connection to communicate with Nokia 7750 SR devices with Video Service Assurance (VSA) capabilities enabled. The connector retrieves TMNX Video Group (VDO GRP) parameters and centralizes this data for monitoring purposes.

The collected data provides visibility into video delivery services implemented through v-ISA (Video ISA), including performance and operational statistics related to video streaming.

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or hostname of the device.
- **IP port**: The SNMP port of the device.

SNMP Settings:

- **Get community string**: Used to retrieve data from the device (default: *public*).
- **Set community string**: Not used by this connector (default: *private*).

## How to Use

This connector is used for monitoring VSA (Video Service Assurance) functionality on Nokia 7750 SR devices. It provides visibility into video-related parameters through three main tables:

- **TMNX VDO GRP**: Displays general information about configured video groups.
- **TMNX VDO GRP SRC Statistics**: Displays statistics related to video source streams, including performance indicators.
- **TMNX VDO GRP MDA**: Displays information about the server state.

## Notes

- This connector is intended for **monitoring only** and does not support configuration or control actions. It is limited to TMNX VDO GRP-related parameters.
- VSA (v-ISA) must be enabled on the Nokia 7750 SR device for data to be available.
- Video processing is handled externally by ESA (Elastic Services Adapter) infrastructure.
- With larger datasets or high-frequency polling, performance may vary depending on device capabilities and SNMP response times.
