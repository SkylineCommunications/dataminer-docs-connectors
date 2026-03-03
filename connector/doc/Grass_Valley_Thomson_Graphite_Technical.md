---
uid: Connector_help_Grass_Valley_Thomson_Graphite_Technical
---

# Grass Valley Thomson Graphite Technical

## About

## Configuration

### Connections

#### Serial Main Connection

This connector uses a Serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **Type of port**: By Default *UDP*.
- **IP address/host**: The polling IP of the destination.
- **IP port**: The IP port of the destination, by default *2901*.

## How to use

### General

On this page, you can check the **Connection Status** and general details for the device (**Firmware Version**, etc...).

### Inputs

This page displays the **Inputs** table, which provides detailed information about all configured inputs. It also enables input configuration and management.

Each Input is periodically polled to retrieve up-to-date status and operational parameters. This polling period can be configured individually for each input.

Inputs can be added, edited or removed by right clicking on the table and selecting the desired action.
- **Add input**: It adds a new input to the Inputs table by specifying its Type, Input number, Description and Polling frequency. **This action does not affect the device.**
- **Configure input**: It allows editing the input’s operational parameters. **It sends the changes to the device.**
- **Delete selected input(s)**: Removes the selected inputs from the Inputs table. **This action does not affect the device.**