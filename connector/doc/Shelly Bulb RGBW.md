---
uid: Connector_help_Shelly_Bulb_RGBW
---

# Shelly Bulb RGBW

This connector allows you to monitor and control the Shelly Bulb RGBW dimmable lighting with RGB colors and white temperatures. This product can be connected to any network through Wi-Fi, and it requires no hub, supports 110 V and 220 V power supplies, features a color and white light mode, and allows you to fine-tune the brightness.

## About

### Version Info

| Range              | Features                   | Based on | System Impact |
|--------------------|----------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | HTTP polling communication | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 |                     |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *80*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

On the **General** page, optionally add the username and password for access to the device.

## How to use

On the **Light** page, you can toggle the light on or off and see its power usage. You can also change the **mode** from *White* to *RGBW*.

Depending on the mode, you can then adjust the light temperature on the **White Mode** page or adjust the color on the **Color Mode** page.

The *Settings* page allows you to configure the Wi-Fi and Backup Wi-Fi settings.

> [!NOTE]
> If you make changes on the *Settings* page, this can break the connection between the device and the network/DMA. Be careful when changing these settings.

## Notes

The device supports MQTT, but this is currently not implemented in the connector.
