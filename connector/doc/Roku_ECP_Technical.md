---
uid: Connector_help_Roku_ECP_Technical
---

# Roku ECP

## About

The Roku ECP (External Control Protocol) connector enables DataMiner to monitor and control Roku streaming devices through Roku’s native HTTP-based API. It provides full visibility into device information, installed applications, and active playback sessions, while allowing operators to send remote control commands directly from the DataMiner platform.

## Configuration

### HTTP Connection

This connector communicates with Roku devices using HTTP requests over port 8060, which is the default Roku ECP port.

The element dynamically uses the IP address configured for the Roku device on the General page of the element, so the IP entered during element creation is not important.

### Initialization

After the element has been created, go to the **General** page, and fill in the IP address of the Roku device in the **Device IP** field.

## How to use

No credentials are required. The device only has to be enabled for remote control using the API.

When the IP address of the Roku device has been specified on the **General** page, the entry will automatically be added the **Devices** table, and the information will be refreshed every minute.
