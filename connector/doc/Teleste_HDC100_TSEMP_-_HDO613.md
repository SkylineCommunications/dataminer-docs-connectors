---
uid: Connector_help_Teleste_HDC100_TSEMP_-_HDO613
---

# Teleste HDC100 TSEMP - HDO613

The HDO613 is a Forward Path Amplifier that supports frequencies up to 1218 MHz with a 29 dB gain.

About

The **Teleste HDC100 TSEMP - HDO613** connector can be used to display and configure information of the related device. A **serial** connection is used in order to successfully retrieve and configure the information of the device. There are also different possibilities available for **alarm monitoring** and **trending**.

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 4.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range   | Supported Firmware          |
|---------|-----------------------------|
| 4.0.0.x | Unknown<br>BIOS Version 1.0 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 4.0.0.x   | No                  | Yes                     | -                     | -                       |

## Installation and configuration

### Creation

A DVE using this connector is automatically created by an element using the parent connector.

## Usage

### General

This page displays *General Parameters* such as **Module Type**, **IP Address**, **Serial number**, **Hardware Version**, **Software Version**, **BIOS Version**, **Fan Status**, **Temperature**, **Up Time**, **Slot Number**, **Rack Number**, etc.

### Adjustments

This page contains two parameters, **Attenuator** and **Equalizer.**

### Monitoring

The **Alarm Control Detection** Parameters are present in this Page: **ACD**, **ACD on Delay** and **ACD off Delay**. Plus the Tables: **HDO613 Analog Alarm Limits** and **HDO613 Discrete Alarm Limits**.
