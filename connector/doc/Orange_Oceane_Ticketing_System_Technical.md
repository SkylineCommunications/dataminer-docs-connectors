---
uid: Connector_help_Orange_Oceane_Ticketing_System_Technical
---


# Orange Oceane Ticketing System Technical Documentation

## About

The Orange Oceane Ticketing System connector integrates DataMiner with the Orange Oceane Ticketing System, enabling automated ticket creation from alarms. This connector streamlines incident management by linking alarms directly to tickets, ensuring issues are addressed promptly and tracked efficiently. It works in conjunction with a DataMiner Automation script and hyperlinks that extend the Alarm Console menu to include a "Create Ticket" option, allowing users to initiate ticket creation directly from alarms.

## Configuration

### Connections

#### HTTP Connection - Orange Oceane API

This connector uses an HTTP connection for the Orange Oceane Ticketing System API and requires the following input during element creation:

- **HTTP CONNECTION:**

  - **IP address/host:** The base URL of the Orange Oceane Ticketing System (user-defined).

- **Timeout configuration:**

  - In the "More TCP/IP Settings" section, ensure the **Include timeout** checkbox is **not selected**. This is necessary because the connector does not poll any endpoints, and retries are implemented internally by the connector logic.

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
  - **User ID:** The identifier of the user creating the tickets.

When this is done, click the **Authenticate** button in the API Settings section to establish the connection with the Orange Oceane Ticketing System.

Note that the "Client ID" and "Client Secret" are used for authentication, and the "User ID" is used to identify the user creating the tickets but is not used in the authentication process.

## Automation Scripts

The connector requires the **Orange Oceane Ticketing System** Automation script to be installed in the DataMiner System. This script is essential for extending the Alarm Console menu with the **Create Ticket** option and handling the logic for ticket creation, including checking for existing tickets and prompting the user for ticket details.

## Hyperlinks

To enable the **Create Ticket** option in the Alarm Console's right-click menu, hyperlinks must be added to the DataMiner System. The following hyperlink configuration is an example of how to extend the menu and link to the Automation script:

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

This hyperlink configuration ensures that the "Create Ticket" option is available in the Alarm Console, triggering the Automation script with the necessary alarm details. The provided HyperLinks.xml file assumes that the script named "Orange Oceane Ticketing System" is located in the "Automation scripts" root folder within the Automation module (Apps -> Automation). If you prefer to place the script in a different folder, please update the HyperLinks.xml file accordingly. 

> [!TIP]
> For more information on configuring hyperlinks in DataMiner:
> - [Hyperlinks.xml](https://aka.dataminer.services/Hyperlinks_xml).
> - [Adding a Custom Command to the Alarm Console Shortcut Menu](https://docs.dataminer.services/user-guide/Basic_Functionality/Alarms/Advanced_alarm_functionality/Adding_a_custom_command_to_the_Alarm_Console_shortcut_menu.html)  
> - [Linking a Shape to an Automation Script](https://docs.dataminer.services/user-guide/Basic_Functionality/Visio/linking_shapes/Linking_a_shape_to_an_Automation_script.html)

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

## Prerequisites
To ensure integration with the Orange Oceane Ticketing System in DataMiner, please verify the following requirements:
- **Network access:** Orange Oceane Ticketing System API must be accessible over the network for API communication.
- **Authentication configuration:** Configure the necessary authentication credentials, including Client ID, Client Secret, and User ID.
- **Automation script:** Install and configure the "Orange Oceane Ticketing System" automation script.
- **DataMiner version:** Ensure you are using DataMiner version 10.5 or higher to fully support the automation script functionality (note: this is relevant despite this being driver documentation).