---
uid: Connector_help_DAC_System_PMB_and_RDS_Monitor
description: "Monitor the DAC System PMB data logger over SNMP and its FM receiver over HTTP: RF power sensors, RF Hawkeye, ATS rules, I/O units, and FM RDS."
---

# DAC System PMB and RDS Monitor

## About

The **DAC System PMB and RDS Monitor** connector integrates the DAC System PMB (Power Meter Broadcast) data logger into DataMiner over SNMP, and it polls the companion FM receiver over its HTTP API. The PMB continuously measures the forward and reflected RF power, return loss, and VSWR on transmitter feeders, combiners, and antennas, while the RF Hawkeye option detects arcing and line degradation in real time.

With this connector, transmitter site operators get a single view of the **RF power sensors, junction boxes, detectors, ATS rules, I/O units, RF Hawkeye analyzers, and FM RDS reception**, so that a degraded return loss, a tripped relay, or an FM carrier that has gone silent can be spotted and attributed to the right site and monitoring point.

## Key Features

- **Monitor RF power per sensor**: Follow the forward power, reflected power, return loss, and VSWR for every sensor and detector, together with the degraded and failure flags raised by the device itself.
- **Supervise site infrastructure**: Keep an eye on the junction box temperature and humidity, hardware mismatches, no-response conditions, power supply failures, and the number of open warnings and alarms.
- **Watch ATS rules and I/O units**: See the state of each automatic transmitter switching rule, and the relay, universal input, dry contact, and analog input states of the connected IOUs.
- **Configure and monitor RF Hawkeye**: Read the arcing and degradation status per processing unit, adjust thresholds, observation windows, and alert periods, and turn analysis on and off directly from DataMiner.
- **Monitor FM RDS and audio level**: Check the PI, PS name, PTY, radio text, and block error rate for each tuned FM frequency, with the audio level in dBFS and built-in silence detection thresholds.

## Use Cases

### Catching Antenna System Degradation Before It Causes an Outage

**Challenge**: A slowly rising VSWR or return loss on a transmitter feeder often goes unnoticed until the transmitter folds back or trips.

**Solution**: The connector exposes the return loss, VSWR, and forward and reflected power of every sensor and detector, together with the device's own degraded and failure flags, and the RF Hawkeye arcing counters per minute, hour, day, week, and month.

**Benefit**: Detect gradual degradation and arcing trends centrally, and schedule maintenance on the right feeder before an outage occurs.

### Detecting Silence on an FM Transmitter

**Challenge**: An FM transmitter can stay on air with a healthy carrier while the audio has dropped, which conventional RF monitoring does not reveal.

**Solution**: The FM receiver audio level is polled every five seconds and comes with silence detection thresholds, while the RDS data confirms that the correct program (PI and PS name) is being received on each frequency.

**Benefit**: Get alerted on dead air or a wrong program within seconds, from the same element that monitors the RF chain.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_DAC_System_PMB_and_RDS_Monitor_Technical).
