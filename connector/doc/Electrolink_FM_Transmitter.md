---
uid: Connector_help_Electrolink_FM_Transmitter
description: "Monitor Electrolink FM transmitter power, thermal and supply measurements, operating states, and remote controls in DataMiner using SNMP."
---

# Electrolink FM Transmitter

## About

The **Electrolink FM Transmitter** connector gives operators a consolidated view of transmitter operation through SNMP. It allows you to monitor RF output and reflected power, thermal and supply measurements, and key transmitter states in DataMiner, with alarm monitoring and trending for operational follow-up.

## Key Features

- **Monitor transmitter health:** View the overall operating state alongside forward and reflected power, heat sink temperature, driver power, and supply voltage and current.
- **Track key operating conditions:** Monitor fan, interlock, VSWR, temperature, RF output, and VSWR block status.
- **Manage output remotely:** Enable or disable the transmitter and adjust its configured output power level through the connector.
- **Configure communication and notifications:** Set LAN settings, the SNMP trap destination, and transmitter email notifications.
- **Tailor data collection:** Adjust polling intervals and enable or disable individual datasets with the Polling Manager.

## Use Cases

### Remote Fault Diagnosis

**Challenge**: When RF output drops at a remote transmitter site, operational information is needed to guide a technician before a site visit.

**Solution**: Review forward and reflected power alongside VSWR and interlock status in DataMiner to investigate the reduced output and identify conditions that warrant on-site checks.

**Benefit**: Technicians get relevant measurements and status information before a visit, helping focus the investigation.

### Maintenance Planning

**Challenge**: Changes in transmitter operating conditions must be assessed when planning maintenance at remote sites.

**Solution**: Review heat sink temperature, supply voltage, and supply current trends in DataMiner to identify changes that warrant inspection.

**Benefit**: You can use observed changes to inform maintenance priorities and planned site inspections.

### Planned Transmitter Work

**Challenge**: During scheduled operational work, transmitter output must be changed and the reported operating condition must be confirmed.

**Solution**: Remotely disable the transmitter or adjust its configured output power through DataMiner, then verify the reported transmitter state and forward and reflected power measurements. Follow site safety procedures; remote controls and reported measurements do not replace them.

**Benefit**: You can coordinate output changes and review the reported response from the same interface during planned work.

## Prerequisites

This connector requires **DataMiner version 10.4.0.0 - 14003** or higher.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation page](xref:Connector_help_Electrolink_FM_Transmitter_Technical).
