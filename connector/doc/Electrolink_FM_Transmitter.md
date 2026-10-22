---
uid: Connector_help_Electrolink_FM_Transmitter
description: "Monitor Electrolink FM transmitter power, thermal and supply measurements, operating states, and remote controls in DataMiner using SNMP."
---

# Electrolink FM Transmitter

## About

The **Electrolink FM Transmitter** connector gives operators a consolidated view of transmitter operation through SNMP. It allows you to monitor RF output and reflected power, thermal and supply measurements, and key transmitter states in DataMiner, with alarming and trending for operational follow-up.

## Key Features

- Monitor overall transmitter state, forward and reflected power, heatsink temperature, driver power, and supply voltage and current.
- Track fan, interlock, VSWR, temperature, RF output, and VSWR block status.
- Enable or disable the transmitter and adjust its configured output power level remotely through the connector.
- Configure LAN settings, SNMP trap destination, and transmitter email notification settings.
- Adjust polling intervals and enable or disable individual datasets with the Polling Manager.

## Use Cases

### Remote Fault Diagnosis

**Challenge**: When RF output drops at a remote transmitter site, you need operational information to guide a technician before a site visit.

**Solution**: Review forward and reflected power alongside VSWR and interlock status in DataMiner to investigate the reduced output and identify conditions that warrant on-site checks.

**Benefit**: You can give the technician relevant measurements and status information before the visit, helping focus the investigation.

### Maintenance Planning

**Challenge**: You need to assess changes in transmitter operating conditions when planning maintenance at remote sites.

**Solution**: Review heatsink temperature, supply voltage, and supply current trends in DataMiner to identify changes that warrant inspection.

**Benefit**: You can use observed changes to inform maintenance priorities and planned site inspections.

### Planned Transmitter Work

**Challenge**: During scheduled operational work, you need to change transmitter output and confirm the reported operating condition.

**Solution**: Remotely disable the transmitter or adjust its configured output power through DataMiner, then verify the reported transmitter state and forward and reflected power measurements. Follow site safety procedures; remote controls and reported measurements do not replace them.

**Benefit**: You can coordinate output changes and review the reported response from the same interface during planned work.

## Technical Reference

### Prerequisites

- This connector requires **DataMiner version 10.4.0.0 - 14003** or higher.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation page](xref:Connector_help_Electrolink_FM_Transmitter_Technical).
