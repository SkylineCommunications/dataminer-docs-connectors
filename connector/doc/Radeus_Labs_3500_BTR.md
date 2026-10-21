---
uid: Connector_help_Radeus_Labs_3500_BTR
description: "The Radeus Labs 3500 BTR connector monitors and controls the Radeus Labs Model 3500 Beacon Tracking Receiver over RS-232, RS-485, or Ethernet."
---

# Radeus Labs 3500 BTR

## About

The **Radeus Labs 3500 BTR** connector monitors and controls the Radeus Labs Model 3500 Beacon Tracking Receiver (BTR). A beacon tracking receiver locks on to a satellite beacon or another narrow carrier and outputs a DC voltage proportional to the received signal level. Antenna control units use this voltage to keep the antenna peaked on the satellite.

The connector shows the received signal level, the carrier lock, and the automatic frequency control (AFC) status of the receiver, and lets operators tune the receive frequency, the reference level, the RF input, and the tracking and filter settings. It supports the L-band, C-band, and Ku-band models of the receiver.

The connector communicates with the receiver through its remote monitoring and control port, using RS-232, RS-485 multidrop, or the built-in Ethernet port.

## Key Features

- **Beacon level and lock monitoring**: The connector shows the signal strength voltage, the carrier lock, and the AFC status, and raises alarms when the receiver loses lock or the AFC leaves its normal range.

- **Remote tuning**: Operators can set the receive frequency and the reference level from DataMiner. The connector checks the values against the frequency band of the receiver before it sends them.

- **Accu-Trac monitoring and control**: The connector shows the Accu-Trac state and the current frequency offset, and lets operators configure the search width and delay.

- **Receiver configuration**: The 5G filter mode, FFT AFC, FFT low-pass filter bandwidth, analog output slope, FFT pre-detection bandwidth, and RF input can be viewed and changed remotely.

- **Device error reporting**: Command errors returned by the receiver are shown with a timestamp, so operators can see why a change was rejected.

- **Multidrop support**: Several receivers can share one RS-485 bus, with each element addressing its own unit.

## Use Cases

### Detecting Loss of the Satellite Beacon

**Challenge**: When the receiver loses the beacon, the antenna control unit can no longer track the satellite, and the link degrades without a clear cause.

**Solution**: The connector polls the carrier lock and the AFC status every 10 seconds and raises an alarm as soon as the lock fails or the AFC reports an alarm.

**Benefit**: Operators are warned immediately and can act before the antenna drifts off the satellite.

### Retuning the Receiver Remotely

**Challenge**: Moving an antenna to another satellite or beacon requires a new receive frequency and reference level, which normally means a visit to the front panel.

**Solution**: Operators set the frequency, reference level, and RF input from DataMiner. The connector reads the settings back, so the displayed values always reflect the receiver.

**Benefit**: Faster satellite changes and less travel to remote sites.

### Trending the Received Beacon Level

**Challenge**: Rain fade, antenna misalignment, and equipment faults all show up as changes in the received beacon level, but they are hard to spot without history.

**Solution**: The signal strength voltage and the Accu-Trac offset can be trended and alarmed in DataMiner.

**Benefit**: Operators can correlate level drops with weather and maintenance, and spot slow degradation early.

## Technical Reference

### Prerequisites

- **DataMiner 10.4.0** or higher is required for range 1.0.0.x of the connector.

- **A serial connection to the receiver** is needed. This can be the Ethernet port of the receiver, or the RS-232 or RS-485 port connected through a serial-to-IP converter or a serial port of the DataMiner Agent.

- **The active M&C port** selected on the front panel of the receiver must be the port that DataMiner is connected to, because only the active port responds. The receiver should be in **Remote** mode to be controlled from DataMiner.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Radeus_Labs_3500_BTR_Technical).
