---
uid: Connector_help_AppearTV_Manager
---

# AppearTV Manager

The **AppearTV Manager** is an application for managing and creating elements using the **AppearTV General Platform**.

The application is used to have an overview of all the devices and services. On top of this application, there is a Visual Overview layer to visualize the elements, DVE map, and services.

## About

The **AppearTV Manager** application makes it possible to search the network for AppearTV Chassis elements. The **Skyline IP Network Discovery** connector must be installed for this.

When the chassis elements have already been created on the DMA, you can also use the sync option to sync the application with the DMA.

## Configuration

The AppearTV Manager is a virtual connector, so you do not have to fill in any configuration parameters during element creation.

## Visual Overview

### Devices/Map page

All DVEs (slot cards) of all the AppearTV Chassis elements in the system are mapped out in categories. Those categories are: Input, Decoding, (pre-) Processing, Encoding/Transcoding, (post-) Processing, and Mux/Output.

In each shape, there are additional KPIs such as **Chassis Name**, **Slot Number**, and **Number of Ports**. When you click a DVE shape, the DVE will be opened.

### Devices/Rack page

An overview is available of all the physical racks. In each rack you can see the different chassis devices.

When you click "*Arrange*" in the context-menu (right-click-menu), you can drag and drop the units to another position in the racks.

This way you can create a visual rack overview that matches the physical setup, and it will be easier to find devices that are in alarm.

The **Rack Names** can be configured ont the Visual Overview page Discovery/Settings Racks.

When you click a device in the rack overview, the corresponding chassis element will be opened. (For extra information about the chassis connector, see [AppearTV General Platform](xref:Connector_help_AppearTV_General_Platform).)

### Services/Overview page

An overview is available with all created DataMiner services. For each service, you can see the number of alarms: Critical (Cr), Major (Ma), Minor (Mi) and Warning (Wa).

When you click on a service shape, the service card will be opened.

### Services/Config page

Here you will find a list of all the created services. The service names are configurable.

### Discovery/Settings page

This page is used for configuration of the network search for chassis devices.

#### General

**Progress** and **Detected Devices** are parameters that will update while the scan is running.

**Detection Status** and **Result**, contain the state and the number of discovered devices. The two buttons allow you to **start** or **Abort** the scan.

Note that to be able to use the detection mechanism, the DMA needs to have an element running that uses the [Skyline IP Network Discovery](xref:Connector_help_Skyline_IP_Network_Discovery) connector.

#### Settings

Before you start the scan, you need to make sure the IP range is configured. The scan will check all the IPs in the range if there are devices available.

You can edit the range by supplying the **IP Address** and **Subnet Mask** or you can fill in the **Start and Stop IP Address**.

The parameter **Elementname Prefix** is used to supply a prefix for all the detected devices. Default: *AppearTV*.

The page button **Racks** opens the Rack Configuration table. You can add or delete racks and change the name, description, and rack dimension. (These racks are visible on the Visual Overview page **Devices/Racks**)

### Discovery/List page

After a scan is performed, the detected devices will be populated in the table with all devices. The IP is used as the index of the table. if the chassis has DUAL IPs, you can see the second IP in the table.

You can change all configurations for each entry in the table. The buttons in the table let you **Create** or **Delete** the actual elements.

When an element is not created, you can also remove the entry from the list by using the **Remove Entry** button.

At the top of the page, you can find the **Create** and **Delete All Elements** buttons. With these buttons, you can create or delete all elements. The elements will be created with the connector **AppearTV General Platform** version: **production**.

There is also the **Synchronize** button, which can be useful if this application is installed on a system that already contains a lot of **AppearTV General Platform** Chassis elements.

## Data Display

On the data pages of the element, you can configure some additional parameters.

### Device Detection page

With **Elements View**, you can choose in which view the generated elements will be placed.

All other parameters are also available in the Visual Overview layer.

### Services page

With **Service Visio**, you can choose if a Visio file needs to be assigned to the the service. The Visio file name can be configured in **Service Visio Name**.

The **Service View** will let you select in which view the services should be placed after they are created.

In the **Service Table**, you can see extra columns **Filter 1**, **2**, and **3**. These columns are not available in the Visual Overview layer, but they are just to see the result of the **Filter Config**.

When you open the **Filter Config** subpage, you will see a table with settings for the extra filters.

There are three filters: **Filter 1**, **2**, and **3**. each filter can be of type *Disabled*, *Property*, *Card*, or *Service Name*. Next to the type, there is also the **Filter Value** and **Set Service Property**.

When **Set Service Property** is enabled, the result value of the filter will be updated in the property of the service. The property name will be *Filter 1*, *Filter 2*, or *Filter 3*.

Below is an overview of the different filter types combined with their filter values:

- *Disabled*: The filter is inactive; filter value is not needed.

- *Property*: When this type is selected, the property from the chassis (provide the property name as the filter value) will be in the filter.

- *Card*: When this type is selected, the filter result value will contain a self defined value when a filter matches in the card types. Format: `Satellite:*Sat*;Analog:*Analog*;Other:*`

  The format is a semicolon-separated string, each time containing a 'filter-value' (\* is used as wildcard) representing the value that you want in the filter.

- *Service Name*: This is the same behavior as type *Card*, except now the filtering looks at the service name instead of the card type.

The button **Apply Filters** will force the execution of the filtering mechanism.
