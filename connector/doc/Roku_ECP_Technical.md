---
uid: Connector_help_Roku_ECP_Technical
---

# Rohde Schwarz ETX-T

## About

The Rohde Schwarz ETX-T connector provides comprehensive control and monitoring capabilities for a range of RF and MPEG parameters. It enables users to access detailed system information, including uptime, serial number, and firmware version, while offering a clear overview of ongoing test statuses. The connector allows precise configuration of MPEG limits, RF frequency settings, and critical thresholds such as BER, MER, and SFN parameters.

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

### General Page

On the **General** page, system information is readily available, including key details such as the device's uptime, serial number, firmware version, and location.

### MPEG-2 TS Overview Page

This page features a table that provides a summary of the current tests and their states.

### MPEG Limits Settings Page

The **MPEG Limits Settings** page allows the configuration of MPEG-related parameters, including the PAT (Program Association Table) distance minimum and maximum, as well as similar settings for CAT (Conditional Access Table), PMT (Program Map Table), BAT (Bouquet Association Table), SDT (Service Description Table), and EIT (Event Information Table).

### RF Overview Page

The **RF Overview** page presents key performance parameters, including the BER (Bit Error Rate) before Viterbi, BER before RS (Reed-Solomon), MER (Modulation Error Ratio) value, MPEG lock state, and several other important metrics.

### RF Frequency Info Page

The **RF Frequency Info** page displays detailed frequency information, including the center frequency, bandwidth, modulation type, transmission mode, and other relevant parameters.

### RF Settings Page

The **RF Settings** page enables the configuration of key parameters such as carrier range, SFN (Single Frequency Network) tolerance time, and SFN tolerance level.

### RF Frequency Settings Page

The **Frequency Settings** page provides configuration options for various thresholds, including MER, BER before Reed-Solomon, and BER before Viterbi. It also allows the adjustment of several relay settings, such as relay level, relay MER, and SFN parameters, along with other miscellaneous frequency settings.
