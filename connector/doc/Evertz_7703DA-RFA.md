---
uid: Connector_help_Evertz_7703DA-RFA
---

# Evertz 7703DA-RFA

## About

This connector monitors the Evertz 7703DA-RFA card, which is part of a splitter series that provides amplification, slope compensation and distribution of RF Signals from 40MHz to 3GHz. They handle any RF input modulation format and provide 4, 8 or 16 isolated outputs for further signal distribution.

Data is polled via SNMP.

## Key Features

- **Wide Frequency Range**: Supports RF signals from 40 MHz to 3 GHz, ideal for L-Band, 70/140 MHz IF, and off-air DTV signals.
- **Multiple Output Configurations**: Available in 1x4, 1x8, and 1x16 configurations, providing isolated outputs for flexible signal distribution.

## Use Case

- **Challenge**: A satellite uplink facility needs to distribute L-Band signals (950–2150 MHz) from a single source to multiple modulators and monitoring systems. The long cable runs introduce signal loss and slope distortion, risking degraded signal quality and synchronization issues.
- **Solution**: Deploy the Evertz 7703DA-RFA connector.
- **Benefit**: 
    - Signal Integrity: Maintains consistent signal levels across all outputs, even over long cable runs.
    - Operational Efficiency: Eliminates the need for multiple passive splitters and amplifiers.
    - Scalability: Easily expands signal distribution as more equipment is added.
   
 [!NOTE]
> For this connector to poll correctly, you must configure the **Bus Address** as the slot number that it occupies in the frame.
