---
uid: Connector_help_Radeus_Labs_ACU_8200
---

# Radeus Labs ACU 8200

## About

The Radeus Labs 8200 Antenna Control Unit (ACU) is designed to control and monitor satellite antenna positioners. It is compatible with industry-standard drive cabinet interfaces and legacy position feedback devices, such as absolute rotary optical encoders and brushless size-11 and size-20 resolvers.

With this connector, operators get a clear, real-time view of antenna positioning and receiver performance directly in DataMiner.

## Key Features

- **Antenna position monitoring**: Track the actual positions of the antenna at a glance.
- **Receiver monitoring**: Follow receiver parameters such as the receiver signal level.
- **Device status**: View the overall status of the ACU, including faults and acknowledgements.
- **Remote configuration**: Configure site, receiver, encoder, limit, motion, timing, option, positioner, and target settings.
- **SNMP-based integration**: Connects to the device through SNMP for fast and reliable communication.

## Use Cases

### Use Case 1

**Challenge**: Operators of satellite teleports with multiple antennas need to know at any moment whether each antenna is correctly pointed and whether the received signal is healthy, without visiting the antenna site.

**Solution**: The connector polls the ACU for the actual antenna positions and receiver parameters, such as the receiver signal level, and displays them clearly on the Main View page.

**Benefit**: Enables quick detection of pointing or signal issues and proactive action before service is affected.

### Use Case 2

**Challenge**: Operators need to react quickly to ACU faults and limit conditions, and adjust antenna targets and motion settings remotely.

**Solution**: The connector exposes the device status and faults, and lets operators configure targets, limits, and motion settings from the Settings pages.

**Benefit**: Reduces site visits and speeds up fault resolution and antenna repointing.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation page](xref:Connector_help_Radeus_Labs_ACU_8200_Technical).
