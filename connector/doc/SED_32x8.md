---
uid: Connector_help_SED_32x8
---

# SED 32x8

## About

The SED 32x8 is a signal routing matrix device. This connector uses GPIB communication to monitor and configure the SED 32x8 matrix, providing real-time visibility on routing states, temperature status, and power conditions.

## Key Features

- **Matrix monitoring**: View and manage the full 32x8 signal routing matrix through a dedicated matrix view.
- **Input/Output management**: Access detailed input and output configuration through dedicated tables.
- **Temperature monitoring**: Track the device's thermal status to ensure safe operating conditions.
- **Power monitoring**: Monitor the power status to detect and respond to power-related issues.
- **Application information**: Retrieve and display device application information at a glance.

## Use Cases

### Centralized Monitoring and Control

**Challenge**: Broadcast engineers need a centralized way to monitor and control signal routing across a 32x8 matrix without manual on-site intervention.

**Solution**: Deploy the SED 32x8 connector in DataMiner to provide a live matrix view and full remote control over signal routing.

**Benefit**: Reduces the need for physical access to the device, enabling faster routing changes and improving operational efficiency.

![Matrix view allowing users to monitor and control signal routing](~/connector/images/SED_32x8_MatrixView.png)

![Tables with the inputs and outputs used in the matrix view](~/connector/images/SED_32x8_TableView.png)

### Early Detection of Issues

**Challenge**: Operations teams need to be alerted to potential hardware failures caused by overheating or power anomalies before they result in signal loss.

**Solution**: Use the temperature and power supply status monitoring capabilities of the connector to continuously track device health.

**Benefit**: Early detection of thermal or power issues allows proactive maintenance and minimizes unplanned downtime.

![Page with temperature and power status information](~/connector/images/SED_32x8_Status.png)

## Technical Reference

### Prerequisites

- **DataMiner version 10.5.0.0 - 15485 or higher** is required to run this connector.
- A **GPIB interface** is required to establish communication with the device.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_SED_32x8_Technical).
