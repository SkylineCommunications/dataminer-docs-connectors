---
uid: Connector_help_Grass_Valley_Thomson_Graphite_Technical
---

# Grass Valley Thomson Graphite Technical

## About

The Grass Valley Thomson Graphite is a digital TV receiver designed for monitoring.

This connector is used to retrieve input data information from the Grass Valley Thomson Graphite device using serial communication. It allows deep monitoring of the device input's sync statuses, their configurations, and the receiver status.

## Configuration

### Connections

#### Serial Main Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **Type of port**: By Default *UDP*.
- **IP address/host**: The polling IP of the destination.
- **IP port**: The IP port of the destination, by default *2901*.

## How to use

### General

On this page, you can check the **Connection Status** and general details for the device (Firmware Version, etc.).

### Inputs

This page displays the **Inputs** table, which provides detailed information about all configured inputs. It also enables input configuration and management.

Each input is periodically polled to retrieve up-to-date status and operational parameters. This polling period can be configured individually for each input.

You can add, edit, or remove inputs by right-clicking the table and selecting the action you want:

- **Add input**: Allows you to add a new input to the Inputs table by specifying its type, input number, description, and polling frequency. This action **does not affect the device**.
- **Configure input**: Allows you to edit the input's operational parameters. These changes are **sent to the device.**
- **Delete selected input(s)**: Removes the selected inputs from the Inputs table. This action **does not affect the device.**
