---
uid: Connector_help_Miranda_RCP-200
---

# Miranda RCP-200

This connector can be used as a remote controller for Miranda RCP-200 devices.

## About

The objective of this connector is to control DataMiner elements using RCP-200 keyboards. DataMiner acts as a gateway:

- Providing some parameter values from elements.
- Changing parameters of elements, based on requests sent by RCP-200.

DataMiner is responsible for providing all the information to be displayed on the RCP-200 buttons:

- String (HTML formatted)
- Background color
- Text color

Also, the layout is dynamic. This means that the parameters displayed on the keyboard could change, depending on which button is clicked. This is the case when parameters are on different pages.

CSV files can be used to provision the data (devices, pages, buttons) in the element.

### API

The RCP-200 devices can interact with the DMA using a REST API, with the DMA element acting as the server. All data is transferred in **JSON** format.

One single method is available to indicate which button on which page is clicked. The API replies with a response containing the complete design of the requested page.

Request URI: http://\<DMAIP\>:\<PORT\>/restapi/SetParameter?panelIp=\<Panel IP\>&page=\<Device Page\>&buttonID=\<Button ID\>

- Panel IP: The IP address of the keyboard generating the command.
- Device Page: Page reference. If empty, the default page (home page) will be returned.
- Button ID: The button that was clicked. The range depends on the configuration of the keyboard (default 1 -\> 24). If empty, this will be considered a page refresh.

Response:

- Device page: The name of the returned page. Note that when a request is received from the device or when a response is sent to it, the page name can potentially contain the reference of the selected device. This device reference will be used to know from which element the parameter value should be retrieved.
- Description of the buttons (ID, value, background color, text color).

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not need any input during element creation.

### Initialization

When you create an element using this connector, some default settings will be applied. To change these settings, see [Configuration Page](#configuration-page).

## Usage

### General Page

This page displays the **status** and **URI** of the API service.

### Simulation Page

This page allows you to simulate the generation of a keyboard page and interact with it. The same code is used as to reply to the RCP-200.

### Devices Page

The table on this page lists the elements for which DataMiner needs to act as a gateway for RCP-200.

You can select a connector in a dropdown list and then select one of the elements using that connector in a second dropdown list and add it to the table.

### Pages Page

The table on this page defines the design of each keyboard page, more specifically the position of each button group on the keyboard.

- **Page Reference**: Name of the page.
- **Button Group Reference**: Reference to the button group to display on this page.
- **X Position** and **Y Position**: The absolute position of the button group on the page.
- **Device Required**: Indicates if the device reference should be added to the page name in the response.

### Buttons Page

The table on this page defines groups of buttons to be displayed on the keyboard pages.

- **Button Group Reference**: Name of the button group in which the button should be placed.
- **X Position** and **Y Position**: The relative position of the button in the group.
- **Type**: Can be *Title*, *Page Link*, *Element Reference*, *Parameter Value*, or *Parameter Update*.
- **Element Reference**: Optional. A reference to a row in the **Devices table**. Only applicable when **Type** is *Element Reference*. Links the page to a specific device.
- **Parameter ID**: Optional. Only applicable when **Type** is *Parameter Value* or *Parameter Update*. Format: `<parameter ID>` or `<parameter ID><key>`.
- **Parameter Value**: Optional. Only applicable when **Type** is *Parameter Update*.
- **Page Link**: Optional. Used to navigate to another page.
- **Title**: Optional. The text to show on the button.
- **Background Color**: Optional. Allows you to override the default background color. See [Notes](#notes) for the available options.
- **Text Color**: Optional. Allows you to override the default text color. See [Notes](#notes) for the available options.
- **Format**: Extra formatting. See [Notes](#notes).

### Import/Export Page

Provides the functionality to import/export CSV files to provision devices, pages, and buttons.

To import a CSV file:

1. Click the **Refresh** button to load the list with available elements on the DataMiner Agent.

1. Select the correct file in one of the dropdown parameters, and confirm your selection.

The CSV file will be loaded in the element.

To export a CSV file:

1. Fill in a name for the export.

   The name will be the first part of the filename.

1. Click the **Export** button.

The exported files will be placed in the Documents folder of the protocol. Existing files will be overwritten.

The status parameters will indicate whether or not the import was successful.

### Configuration Page

This page contains controls to define the settings that are used by the API.

- **Number of Rows**: By default 3.
- **Number of Columns**: By default 8.
- **Default Page**: This is the page to return when no page is specified in the request.
- **Default Background Color**: The button color when not overridden in the **Buttons Table**.
- **Default Text Color**: The button color when not overridden in the **Buttons Table**.
- **Default Set Timeout**: The default time to wait until a parameter set succeeded.
- **REST API Port**: The TCP port on which the REST API will run.

## Notes

### Special text formatting

The **Format** column on a button can be used to specify some optional conditions. Multiple pipe-separated conditions can be added.

- `PAGE:DeviceSelection2Page:<b>*</b>`: In case the page that will be generated is "DeviceSelection2Page", the text will be surrounded by `<b>` and `</b>`.

- `MAPVALUE:1=OK;2=Loss`: Allows you to change the value of a parameter to another value.

### Special color formatting

For the color parameters, you can specify special options that can be used for conditional coloring.

- `ALARM`: Returns the color that matches the alarm severity of the parameter linked to this button.

- `VALUE:1=FF1111;2=FF2222`: Use the color "FF1111" when the value of the parameter is 1, and use the color "FF2222" when the value of the parameter is 2.
