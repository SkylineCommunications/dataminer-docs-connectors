---
uid: Connector_help_CEFD_Memotec_CXU-1240
---

# CEFD MEMOTEC CXU-1240

This is an SNMP connector for the configuration and monitoring of the following types of devices:

- CXU-1240
- CXU-1010

## About

The connector is used to configure a CXU-1240/CXU-1010.

## Configuration and Installation

### Creation

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

**SNMP CONNECTION**:

- **IP address/host**: The polling IP of the device, e.g. *10.11.12.13*

**SNMP Settings**:

- **Port number**: the port of the connected device, default *161*
- **Get community string**: the community string in order to read from the device. The default value is *public*.
- **Set community string**: the community string in order to set to the device. The default value is *private.*

## Usage

Once the element has been configured, it will work on its own.

## General

This page contains some general data concerning the device.

With the button **Clear temperature statistics**, you can clear the temperature parameters

## Admin

This page contains standard administrator parameter such as the location and name of the device.

With the button **Reboot unit**, you can reboot the device.

Click the button **Save Configuration** to save the system parameters to the device.

On this page, you can also switch to the redundant unit and set the SNMP Trap Destination address.

## Configuration - Network

Here you can find the current network settings.

On the **Modify** subpage, you can change these settings. When you have filled in the new values for the parameters, click the **Apply** button to apply these settings to the device.

## Configuration - E1 Ports Page

On this page, you can configure everything related to the E1 ports.

At the bottom of the page, you can change the jitter buffer depth.

> [!NOTE]
> Settings done on this page will immediately be applied to the device.

## Configuration - Wan interfaces

On this page, you can find the configuration of the Wan Interfaces.

Here you can configure the Traffic channels.

- To delete an entry from the table, click the **Delete** button in the corresponding row.

- To create a new entry in the table, click the **Create New Entry.** button located at the bottom of the page, then fill in the parameters and click **Apply**.

> [!NOTE]
> When the maximum number of entries has been reached, you will not be able to add a new entry unless you delete a row first.

## Configuration - Clocking / Configuration - Redundancy

On these pages, you can find the settings for the clocking configuration.

To change these parameters, click the **Modify** button. This will open a window where you can change the selected settings. Click **Apply** to apply your changes to the device.

## Statistics - Network

On this page, you can find the statistics of the network interface.

With the **clear** button, you can clear the network statistics.

## Statistics - E1 Ports

On this page you can find the statistics of the E1 ports.

With the **clear** button, you can clear the corresponding row.

## Performance monitoring E1 Ports

On this page, you can find the performance statistics of the device.

Click the **Intervals** button to open a page where you can select a port and interval to view the performance statistics of up to a day ago in blocks of 15 min.

Clicking the next will shift the interval by one and get the new data.

For example, to select the interval of 45 minutes ago on E1 Port 2:

1. Select Port 2 under the parameter E1 Port.
1. Set the interval to 3 (3\*15min = 45 min ago.)
1. Click **Get**.

## Statistics - Wan Interfaces

On this page, you can find the statistics of the Wan interfaces.

With the **clear** button, you can clear the corresponding row.

## Statistics - Optimization

On this page, you can find the statistics of the optimization of the device.

Clicking the **Clear** button will clear the saved values for TX and RX.

## E1 Ports Table

With the **Clear** button, you can clear the corresponding row.

If you click **Select E1 Port** and then click the button **Mapping**, this will open a window with the time slots of the selected E1 port. You can also select the E1 port by changing the E1 Port Selected parameter located at the top of the page.

You can refresh the time slots by clicking the **Refresh** button located at the bottom of the page.

## Statistics - Clocking

On this page, you can find the statistics of the clocking of the device.

With the **Reset** button, you can reset the statistics.

## Statistics - Redundancy

On this page, you can find the redundancy statistics

With the **Reset** button, you can reset the statistics.

## Traps

On this page, you can see the traps that have been received from the device.

You can delete an entry by clicking the **Delete** button in the corresponding row.

To delete all entries from the table, click the **Clear Table** button located at the bottom of the page.
