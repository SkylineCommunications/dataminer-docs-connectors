---
uid: Connector_help_NPC_System_ACU550
---

# NPC System ACU550

## About

The NEYRPIC® ACU550 is a microprocessor-based Antenna Control Unit (ACU) for the tracking of geostationary and low-orbit satellites.

This connector establishes a TCP/ONC-RPC session with the ACU to monitor antenna position and status in real time, drive the antenna through its operating and tracking modes, and surface ACU, motor, and per-axis alarms directly in DataMiner.

### Version Info

| Range                | Key Features     | Based on     | System Impact                                        |
|----------------------|------------------|--------------|------------------------------------------------------|
| 1.0.0.x              | Initial version  | -            | -                                                    |
| 1.0.1.x [SLC Main]   | Initial version  | 1.0.0.3      | Some parameters were relocated, renamed, or updated. |

## Key Features

- **Real-time antenna status**: Continuously monitors current azimuth, elevation, and polarization positions, along with their targets, offsets, position errors, and drive speeds.

- **Multi-mode operation and tracking**: Supports the ACU operating modes (standby, rate, position, stow/unstow) and tracking modes (monopulse, step, orbital, and auto tracking) for both geostationary and low-orbit satellites.

- **Satellite and position presets**: Retrieves and applies satellite and position presets, including satellite name, nominal longitude, polarization, beacon frequency, and acquisition thresholds.

- **Alarm monitoring**: Exposes ACU, motor, and per-axis (azimuth, elevation, and polarization) alarm status for fast fault detection.

- **Signal and version insight**: Reports beacon signal level, nominal acquisition level, and acquisition threshold correction, together with firmware and interface version information.

## Use Cases

### Keeping Geostationary Antennas Locked on Target

**Challenge**: Pointing drift and signal degradation on a geostationary link can go unnoticed until the service is impacted.

**Solution**: The connector continuously reports azimuth/elevation/polarization position errors, offsets, and signal level, and allows operators to trigger monopulse or step tracking from DataMiner.

**Benefit**: Faster detection and correction of pointing errors, resulting in more stable links and reduced signal loss.

### Automating Low-Orbit Satellite Tracking

**Challenge**: Low-orbit satellites move quickly and require frequent mode changes and preset loading that are error-prone when handled manually per antenna.

**Solution**: The connector drives orbital and auto-tracking modes and applies satellite/position presets programmatically, so passes can be prepared and executed consistently.

**Benefit**: Reliable, repeatable acquisition and tracking with less manual intervention.

### Centralized Fault Management Across an Antenna Fleet

**Challenge**: Monitoring ACU, motor, and per-axis faults on multiple antennas from separate local interfaces slows down response times.

**Solution**: The connector aggregates ACU, motor, and azimuth/elevation/polarization alarm status into DataMiner, where alarms can be correlated and escalated centrally.

**Benefit**: A single operational view of the antenna estate and quicker resolution of hardware faults.

## Technical Reference

### Prerequisites

- **Network connectivity** to the ACU is required so DataMiner can open the TCP/ONC-RPC session used to poll status and send commands.

- **DataMiner 10.4.0.0 (build 14003) or higher** is required.

- **The polling IP and IP port of the ACU** are required during element creation.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## Notes on Usage

Create a DataMiner element using this connector to monitor and control the ACU. No special actions are required to use the element.

The connector creates a TCP client to retrieve all data from the ACU, so no data will be available in Stream Viewer.
