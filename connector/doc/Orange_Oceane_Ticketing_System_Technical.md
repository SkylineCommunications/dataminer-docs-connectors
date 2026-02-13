---
uid: Connector_help_Orange_Oceane_Ticketing_System_Technical
---


# Orange Oceane Ticketing System Technical Documentation

## About

The Orange Oceane Ticketing System connector integrates DataMiner with the Orange Oceane Ticketing System, enabling automated ticket creation from alarms. This connector streamlines incident management by linking alarms directly to tickets, ensuring issues are addressed promptly and tracked efficiently. It works in conjunction with a DataMiner automation script and hyperlinks that extend the Alarm Console menu to include "Create Ticket" and "Go to Ticket" options, allowing users to initiate ticket creation directly from alarms.

## Configuration

### Connections

#### HTTP Connection - Orange Oceane API

This connector uses an HTTP connection for the Orange Oceane Ticketing System API and requires the following input during element creation:

- **HTTP CONNECTION:**

  - **IP address/host:** The base URL of the Orange Oceane Ticketing System (user-defined).

- **Timeout configuration:**

  - In the "More TCP/IP Settings" section, ensure the **Include timeout** checkbox is **not selected**. This is necessary because the connector does not poll any endpoints, and retries are implemented internally by the connector logic.

### Prerequisites

To ensure integration with the Orange Oceane Ticketing System in DataMiner, please make sure the following prerequisites are met:

- **Network access:** The Orange Oceane Ticketing System API must be accessible over the network for API communication.
- **DataMiner version:** Make sure you are using DataMiner version **10.5 or higher** to fully support the automation script functionality.
- **Authentication configuration:** Make sure you have the necessary authentication credentials, including Client ID and Client Secret. Additionally, DataMiner usernames with ticket creation permissions must be mapped to their corresponding Oceane User IDs. (See [Initialization](#initialization).)
- **Automation script:** Make sure the "Orange Oceane Ticketing System" automation script is installed. (See [Automation Scripts](#automation-scripts).)

### Initialization

After creating the element, configure the following settings on the **Settings** page:

- **Element Settings:**

  - **Ticket Storage Duration Limit:** The maximum duration tickets are stored (default: 90 days).
  - **Ticket Storage Count Limit:** The maximum number of tickets that can be stored (default: 1000).
  - **Ticket Creation Retry Count:** The number of times to retry creating a ticket if it fails (default: 1).
  - **Display Debug Page:** Option to enable or disable the debug page (default: Disabled).

- **API Settings:**

  - **Client ID:** The client identifier for authentication with the Orange Oceane Ticketing System.
  - **Client Secret:** The secret key for authentication.

When this is done, click the **Authenticate** button in the API Settings section to establish the connection with the Orange Oceane Ticketing System.

Note that the Client ID and Client Secret are used for authentication. The Oceane User ID for ticket creation is obtained from the DataMiner username configuration, which means that each DataMiner username must be mapped to a corresponding Oceane User ID.

## Automation Scripts

The connector requires the **Orange Oceane Ticketing System** automation script to be installed in the DataMiner System. This script is essential for extending the Alarm Console menu with the **Create Ticket** option and handling the logic for ticket creation, including checking for existing tickets and prompting the user for ticket details.

## Hyperlinks

To enable the **Create Ticket** option in the Alarm Console's right-click menu, hyperlinks must be added to the DataMiner System. The following hyperlink configuration is an example of how to extend the menu and link to the automation script:

```xml
<HyperLinks xmlns="http://www.skyline.be/config/hyperlinks">
  <HyperLink id="1"
          version="2"
          name="Create Ticket"
          menu="root"
          type="script"
          alarmColumn="false">
    Orange Oceane Ticketing System||DMA ID=[DMAID];Element ID=[EID];Alarm ID=[ROOTKEY];Element Name=[ENAME];Alarm Value=[VALUE];Root Time=[ROOTTIME:yyyy-MM-ddTHH:mm:ssZ]||Create ticket in Oceane Ticketing Tool|NoConfirmation,CloseWhenFinished
  </HyperLink>
</HyperLinks>
```

- **Required Parameters:**

  - **DMA ID ([DMAID]):** The DataMiner Agent ID.
  - **Element ID ([EID]):** The ID of the element associated with the alarm.
  - **Alarm ID ([ROOTKEY]):** The unique identifier of the alarm.
  - **Element Name ([ENAME]):** The name of the element associated with the alarm.

- **Optional Parameters:**

  - **Alarm Value ([VALUE]):** The value of the alarm.
  - **Root Time ([ROOTTIME]):** The timestamp of the alarm's root cause, formatted as `yyyy-MM-ddTHH:mm:ssZ`.

This hyperlink configuration ensures that the "Create Ticket" option is available in the Alarm Console, triggering the automation script with the necessary alarm details. The provided *HyperLinks.xml* file assumes that the script named "Orange Oceane Ticketing System" is located in the "automation scripts" root folder within the Automation module in DataMiner Cube (Apps > automation). If you would prefer to place the script in a different folder or if you want to rename the script, please update the *HyperLinks.xml* file accordingly.

The hyperlink configuration can also be extended with a "Go To Ticket" option to open the ticket in the Orange Oceane Ticketing System. Below you can find an example that shows how this can be configured. With this example, the "Go To Ticket" option will only be available if the ticket URL is available in the alarm properties ("Oceane Ticket URL" property). This means that it will only be available if the ticket is created for the selected alarm, otherwise it will not appear in the right-click menu. The ticket URL property in the Alarm Console is set by the connector when a ticket is created successfully.

```xml
<HyperLinks xmlns="http://www.skyline.be/config/hyperlinks">
  <HyperLink id="1"
             version="2"
             name="Create Ticket"
             menu="root"
             type="script"
             alarmColumn="false"
             filterElement="AlarmEventMessage.PropertiesDict.&quot;Oceane Ticket ID&quot;[String]==''">
    Orange Oceane Ticketing System||DMA ID=[DMAID];Element ID=[EID];Alarm ID=[ROOTKEY];Element Name=[ENAME];Alarm Value=[VALUE];Root Time=[ROOTTIME:yyyy-MM-ddTHH:mm:ssZ]||Create ticket in Oceane Ticketing Tool|NoConfirmation,CloseWhenFinished
  </HyperLink>
  <HyperLink id="2"
             version="2"
             name="Go To Ticket"
             menu="root"
             type="url"
             filterElement="AlarmEventMessage.PropertiesDict.&quot;Oceane Ticket URL&quot;[String]!=''">
    [PROPERTY:ALARM:Oceane Ticket URL]
  </HyperLink>
</HyperLinks>
```

The "Go To Ticket" option opens the **Oceane Ticketing System** in your browser. The tool has its own authentication mechanism, so the "Go To Ticket" option expects that you have already logged into Oceane in the same browser session. Once you have been authenticated, Oceane saves your session in the browser cookies. The "Go To Ticket" option does not handle authentication. If you have not previously logged into Oceane in the browser, you will see an "Unauthorized" prompt from Oceane. You will need to authenticate separately before using this feature.

With the provided configuration, only one hyperlink option will be displayed at a time: "Create Ticket" appears when no ticket exists for the alarm, while "Go To Ticket" appears only after a ticket has been created.

> [!NOTE]
> Two custom alarm properties should be added to the DMA alarm properties to store the ticket ID and URL. They should be named **Oceane Ticket ID** and **Oceane Ticket URL**, respectively. The connector will automatically set these properties when a ticket is created successfully. The **Oceane Ticket ID** property will contain the ticket ID, and the **Oceane Ticket URL** property will contain the URL to access the ticket in the Orange Oceane Ticketing System. For more information on adding custom properties to alarms, see [Adding custom properties to alarms](https://aka.dataminer.services/Changing_custom_alarm_properties).

> [!TIP]
> For more information on configuring hyperlinks in DataMiner:
>
> - [Hyperlinks.xml](https://aka.dataminer.services/Hyperlinks_xml).
> - [Adding a custom command to the Alarm Console shortcut menu](https://aka.dataminer.services/adding-custom-commands-to-the-alarm-console)
> - [Linking a shape to an automation script](https://aka.dataminer.services/Linking_a_shape_to_an_Automation_script)

## How to Use

To use this connector, follow these steps:

1. Create an element using the Orange Oceane Ticketing System connector in DataMiner, specifying the HTTP connection details and ensuring the **Include timeout** checkbox is **not selected** in the "More TCP/IP Settings."

1. On the **Settings** page, configure the API settings with the provided *Client ID*, *Client Secret*, and *User ID*, then authenticate.

1. Configure the desired element settings, such as ticket storage limits, retry counts, and whether to display the debug page.

   The [Debug page](#debug-page) can be used to monitor ticket queue statuses for troubleshooting purposes, but you will not need this page in normal circumstances.

1. To create a ticket:

   1. Right-click an alarm in the Alarm Console and select **Create Ticket** in the menu.

   1. If the ticket does not already exist, you will be asked to enter ticket details, including:

      - Priority (required)
      - Urgency (required)
      - Technical Impact (required)
      - Client Impact
      - Description

   1. After filling in the details, click **Create Ticket** to submit the request.

      The connector will attempt to create the ticket:

      - If **successful**, it updates the alarm properties with the ticket ID and URL and adds the ticket to the **Tickets** table.
      - If **unsuccessful**, it adds the ticket to **Tickets** table with **failed** status, and it records the failure in the **Failed Ticket Requests** table.

## Interfaces

### Dynamic Interfaces

- **Virtual dynamic interfaces:**

  - **Tickets Table:** Contains created tickets with fields such as Instance, Ticket ID, Alarm ID, DataMiner ID, Element ID, Element Name, Created At, Priority, Urgency, Technical Impact, Client Impact, Root Cause, and Status.
  - **Failed Ticket Requests Table:** Contains information about failed ticket creation attempts, with fields such as Instance, Ticket ID, HTTP Error Code, App Error Code, Error Message, and Error Description.

These tables are updated by the connector as tickets are created or fail to be created.

## Debug Page

The connector provides a debug page (enabled via the Settings page) that displays the status of ticket queues:

- **Ticket Queue Processing Lock:** Indicates if the ticket processing is locked or not with the locked status indicating that the connector is currently processing the ticket.
- **Pending Ticket Creation Queue:** Shows the status of pending ticket creation requests (buffer).

These can be useful for troubleshooting issues with ticket creation.
