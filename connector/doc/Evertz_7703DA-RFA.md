---
uid: Connector_help_Evertz_7703DA-RFA
---

# Evertz 7703DA-RFA

## About

This connector monitors the Evertz 7703DA-RFA card, which is part of a splitter series that provides amplification, slope compensation and distribution of RF Signals from 40MHz to 3GHz. They handle any RF input modulation format and provide 4, 8 or 16 isolated outputs for further signal distribution.

Data is polled via SNMP.

## Key Features

- **RF Input Control**: Control/monitor the RF Input Power and Low/High Thresholds.
- **LNB Control**: Control/monitor the LNB Current, Voltage, and Low/High Thresholds.
- **Polling Configuration**: Adjust all available groups' polling time from as little as 10s.

## Use Case

- **Challenge**: Evertz 7703DA-RFA is polling too slowly in the Evertz General Platform connector
- **Solution**: Deploy the Evertz 7703DA-RFA connector.
- **Benefit**: 
    - Can now monitor the Evertz 7703DA-RFA card without depending on the parent connector, can now control how often to poll the various groups.
   
 [!NOTE]
> For this connector to poll correctly, you must configure the **Bus Address** as the slot number that it occupies in the frame.
