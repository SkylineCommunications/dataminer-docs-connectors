---
uid: Connector_help_Linear_Acoustic_Aero_2000
---

# Linear Acoustic AERO.2000

## About

The Linear Acoustic AERO.2000 is a 2RU loudness management platform capable of hosting one or two AEROMAXr processing instances (at least one is required). It provides real-time adaptive wideband and/or multiband processing, including an advanced ITU limiter.

## Key Features

- **General**: Displays the SNMP connection status, as well as system information such as the model name, software version, and FPGA version.
- **Status**: Provides a quick overview of the hardware (CPU and RAM usage), temperature and fan readings, video and audio input status, redundant power supply, engine status, and Cn 2000 state.
- **Instance 1 and 2**: Displays the programs of each processing instance, including the silence state and loudness of each program, with a loudness alarm when the value falls out of range.
- **Traps**: Logs incoming SNMP traps, with settings to configure how traps are logged and when they are removed.

## Use Cases

**Challenge**: Ensuring that broadcast audio stays within loudness regulations and that processing hardware remains healthy, without constant manual checks.

**Solution**: Installing the Linear Acoustic AERO.2000 connector lets you monitor the loudness and silence state of every program in real time. You are alerted through a loudness alarm when a value falls out of range.

**Challenge**: Detecting hardware or signal problems before they affect on-air audio.

**Solution**: The connector shows CPU and RAM usage, temperatures, fan speeds, power supply redundancy, and the status of video, audio, and reference inputs. It also logs incoming SNMP traps, so you can quickly identify and react to faults.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation page](xref:Connector_help_Linear_Acoustic_Aero_2000_Technical).
