---
uid: Connector_help_Active_Power_CleanSource_XT_MMS_Technical
---

# Active Power CleanSource XT MMS

## About

The Active Power CleanSource XT MMS connector enables DataMiner integration and monitoring of Active Power's CleanSource XT Multi-Module System (MMS). Through SNMP, this connector retrieves operational and performance data from the device and all added modules.

## Configuration

### Connections

#### SNMP Connection

This connector uses an SNMPv3 connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The Babel Buster IP address (see [Notes](#notes)).

SNMP Settings:

- **Port number**: The port of the connected device, by default 161.
- **Security level**: The security level to use for SNMP communication (default: *authPriv*).
- **Authentication password**: The password used for authentication when the security level is set to *authNoPriv* or *authPriv*.
- **Encryption password**: The password used for encryption when the security level is set to *authPriv*.
- **Authentication protocol**: The authentication protocol to use when the security level is set to *authNoPriv* or *authPriv* (default: *SHA-512*).
- **Encryption protocol**: The encryption protocol to use when the security level is set to *authPriv* (default: *AES-256*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## Notes

For this connector to be able to poll data, a **Control Solutions Minnesota Babel Buster BB3-6101-V3 Modbus to SNMP Gateway** must be connected to the device and properly configured, and the connector must connect to the Babel Buster IP address.
