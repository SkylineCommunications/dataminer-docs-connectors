---
uid: Connector_help_Roku_ECP_Technical
---

# Roku ECP

## About

The Roku ECP (External Control Protocol) connector enables DataMiner to monitor and control Roku streaming devices through Roku’s native HTTP-based API. It provides full visibility into device information, installed applications, and active playback sessions, while allowing operators to send remote control commands directly from the DataMiner platform.

## Configuration

### HTTP Connection

This connector communicates with Roku devices using HTTP requests over port 8060, which is the default Roku ECP port.

The connector does not rely on the IP address entered during element creation. Instead, it dynamically uses the Device IP configured directly inside the element. This allows operators to freely update device details without recreating the element.

### Initialization

After the element has been created, navigate to the **General** page and enter the Roku device's IP address in the **Device IP** field. When you submit the IP, the connector automatically adds the device to the Devices table and begins monitoring it. The port does not need to be entered, as Roku ECP uses a fixed port (8060) that is handled automatically by the connector. Device information, app lists, and active app data are refreshed every minute.

No credentials are required to use this connector. The only requirement is that Remote Control via the Roku External Control Protocol (ECP) API is enabled on the Roku device.

## How to Use

Within the **Devices** table, you can update the IP address of a device at any time or remove it entirely using the delete button. This makes it easy to manage devices that change networks or are replaced.

The **Remote Control** page allows you to interact with the Roku device as if you were using a physical Roku remote. You can launch installed channels by selecting one from the drop-down menu under the **Channel** column. You can also send navigation and system commands, including Up, Down, Left, Right, Select, Home, and Back, to control the interface remotely.

Behind the scenes, all commands are executed using lightweight HTTP ECP requests, ensuring fast communication and immediate feedback. The connector also continuously tracks the active application, installed apps, and playback-related information, offering a clear and real-time overview of the Roku device's state.
