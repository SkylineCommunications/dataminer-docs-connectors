---
uid: Connector_help_Evertz_7703DA-RFA
---

# Evertz 7703DA-RFA

## About

This connector monitors the Evertz 7703DA-RFA card, which is part of a splitter series that provides amplification, slope compensation, and distribution of RF signals from 40 MHz to 3 GHz. They handle any RF input modulation format and provide 4, 8, or 16 isolated outputs for further signal distribution.

Data is polled via SNMP.

> [!NOTE]
> When you configure a DataMiner element using this connector, set the **Bus Address** to the slot number that the device occupies in the frame.

## Key Features

- **RF input control**: Control and monitor the RF input power and low/high thresholds.
- **LNB control**: Control and monitor the LNB current, voltage, and low/high thresholds.
- **Polling configuration**: Adjust all available groups' polling time to as little as 10 seconds.

## Use Case

- **Challenge**: Evertz 7703DA-RFA is polling too slowly when the Evertz General Platform connector is used.
- **Solution**: Deploy the Evertz 7703DA-RFA connector.
- **Benefit**: Ability to monitor the Evertz 7703DA-RFA card without depending on the parent connector, with the possibility to control how often the various groups will be polled.
