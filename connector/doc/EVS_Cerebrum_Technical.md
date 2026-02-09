---
uid: Connector_help_EVS_Cerebrum_Technical
---

# EVS Cerebrum

This is a WebSocket-based connector with Cerebrum acting as the server, using either secure or non-secure communication, depending on how this is configured within the Cerebrum application.

The data sent over the WebSocket connection, once initial handshakes are complete, is XML-based.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x [Obsolete] | Initial version. | - | - |
| 1.0.1.x [Obsolete] | New version because of invalid connector integration. | - | Loss of trending, alarming, saved parameters, etc. Creating a new element is recommended. |
| 1.0.2.x [Obsolete] | New version because of InterApp update to 1.0.1.x. | - | InterApp communication possibly not backwards compatible. |
| 1.1.0.x [Main] | Connector is updated to represent a Cerebrum system instead of a Cerebrum server.  | - | Element connections need to be reconfigured. |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | API 0.1                |
| 1.0.1.x   | API 0.1                |
| 1.0.2.x   | API 0.1                |
| 1.1.0.x   | API 0.1                |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |
| 1.0.2.x   | No                  | Yes                     | -                     | -                       |
| 1.1.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### WebSocket Connection

This connector uses a WebSocket connection and requires the following input during element creation:

WEBSOCKET INTERFACE:

- **IP address/host**: ws://*\[The polling IP of the destination]\*
- **IP port**: The IP port of the destination, default: *40007*.

Note:
If the EVS Cerebrum system is configured with a **virtual IP address**, the virtual IP address is higly recommended to be used as the polling IP.
If no virtual IP address is configured, use the polling IP address of one of the Cerebrum servers, as the connector will automatically switch the WebSocket connection to the currently active server. 

#### Primary Server SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

#### Secondary Server SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).


### Initialization

To be able to log in to the WebSocket API, specify the **User Name** and **Password** on the **Credentials** page.

When the login is successful, the **Credential State** will show the *OK* state.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### General Page

This page contains parameters related to the **system** and the **WebSocket** API.

### Devices Page

The following options are available in the right-click menu on this page:

- **Refresh Sources**: Refreshes the source information of the selected device.
- **Refresh Destinations**: Refreshes the destination information of the selected device.

### Sources Page

The following options are available in the right-click menu on this page:

- **Add To Category**: Adds the selection of sources to the specified category.
- **Add Alternate Mnemonic**: Adds an alternate mnemonic to the source.
- **Exclude**: Adds the selected sources to the source exclusion list. Any routes matching the source exclusions will not be shown in the routes table. You can for example use this if you do not want to show your "not connected" routes.
- **Cleanup**: Removes all unavailable sources from the source-related tables.

### Source Associations

To **create** a source association, specify the configuration settings on the **Source Configuration** subpage and click the **Create** button.

With the **Delete** option in the right-click menu, you can delete the selected source association.

### Destinations Page

The following options are available in the right-click menu on this page:

- **Add To Category**: Adds the selection of destinations to the specified category.
- **Add Alternate Mnemonic**: Adds an alternate mnemonic to the destination.
- **Cleanup**: Removes all unavailable destinations from the destination-related tables.

### Destination Associations

To **create** a destination association, specify the configuration settings on the **Destination** **Configuration** page and click the **Create** button.

With the **Delete** option in the right-click menu, you can delete the selected destination association.

### Subscription Filtering

For **levels**, **sources**, and **destinations**, it is possible to subscribe only to a subset of each, based on ID. Subscriptions filters are configured on the **Level Subscription Filters**, **Source Subscriptions Filters**, and **Destination Subscription Filters** page, respectively.

If destinations filters are defined, they will be taken into account when setting up routes subscriptions, so that only the relevant routes are subscribed to.

The following options are available in the right-click menus on the filter pages:

- **Subscribe to All**: Disables all filters except the default one. The default filter subscribes to everything.
- **Add Ranged Based Filter**: Allows you to add a new range-based filter by providing *from* and *to* values of IDs.
- **Remove Filters(s)**: Removes the selected filters. The default filter cannot be removed.

> [!NOTE]
> Changes to filter pages will only be applied on element restart.

### Categories

The following options are available in the right-click menu on this page:

- **Create**: Creates a new category with the specified settings.
- **Delete**: Deletes the selected category.
- **Add To Parent**: Adds the selected category to the specified parent category.

On the **Category Sub Categories**, **Category Sources**, **Category Destinations**, and **Category Salvos** subpages, you can also use the **Delete** option in the right-click menu to delete the selected sub category item, source category item, destination category item, or salvo category item, respectively.

### Cortex Link Page

This page provides an overview of the Cortex link **Tx**, **Rx**, and **connectivity** parameters.

### Cortex Link Redundancy Page

This page provides an overview of the Cortex link **redundancy** parameters.

### SQL Server Info Page

This page provides an overview of the **primary** and **secondary** server, and **SQL** information.

### Statistics Page

This page provides an overview of statistics related to the WebSocket API.

## Notes

### Failover System

Most Cerebrum systems consist of both a primary and a secondary server. At any point in time, only one of these servers will be "active", and the other will be in an "inactive" state.

While a connection can always be made to both servers, the inactive server will only respond to the LOGIN and POLL command.
The configuration of the WebSocket-related subscription items is only applicable for the Cerebrum server acting as the active server.
When the **System Controller State** changes to *Enabled*, the Cerebrum server acts as the active server and the WebSocket subscriptions are made.

### Virtual IP Address

If a virtual IP address has been enabled within Cerebrum, this can be used to ensure that the client is always connected to the active server.
However, as this method does not confirm network connectivity from the client to the currently inactive server, some provisions should be made to ensure that a connection will be available following a switch between the servers.

## Upgrade Procedures

### Upgrade from ranges 1.0.1.x or 1.0.2.x to 1.1.0.x

When upgrading from connector ranges 1.0.1.x or 1.0.2.x to 1.1.0.x, it is important to follow the procedure described below to minimize system impact.
When the procedure is applied correctly, there should be no significant system impact, and any data loss should be negligible or non-existent.  

If your system uses the **production version** feature and you intend to designate the new connector range as the production version, note that the upgrade procedure described below must be applied to **all elements using the production version**.
Additionally, the production version must **not** be changed until explicitly indicated in the procedure.

Procedure:
1. Stop the DataMiner elements that need to be upgraded to connector range 1.1.0.x.<br/>
  *If the production version feature is used, this includes all elements currently running the production version.*
2. If applicable to your system setup, configure connector range 1.1.0.x as the prodution version.
3. Reconfigure the DataMiner elements to use the connector range by either:<br/>
Selecting version 1.1.0.x in the Edit Wizard, or<br/>
Changing the production version (as described in the previous step).
4. Update the DataMiner elements by reconfiguring the element connections.<br/>
  *Typically, this only requires configuring the secondary server SNMP connection.*
5. If applicable, restart the DataMiner elements.

After completing the procedure above, the DataMiner elements will have been successfully upgraded from representing a single EVS Cerebrum server to representing an EVS Cerebrum system.
