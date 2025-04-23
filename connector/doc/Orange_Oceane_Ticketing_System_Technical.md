# Orange Oceane Ticketing System Connector Technical Documentation

## About

The Orange Oceane Ticketing System connector integrates DataMiner with the Orange Oceane Ticketing System, enabling automated ticket creation from alarms. This connector streamlines incident management by linking alarms directly to tickets, ensuring issues are addressed promptly and tracked efficiently. It works in conjunction with an automation script and hyperlinks that extend the alarm console menu to include a "Create Ticket" option, allowing users to initiate ticket creation directly from alarms.

## Configuration

### Connections

**HTTP Connection – Orange Oceane API**

This connector uses an HTTP connection for the Orange Oceane Ticketing System API and requires the following input during element creation:

- **HTTP CONNECTION:**

  - **IP address/host:** The base URL of the Orange Oceane Ticketing System (user-defined).

**Additional Configuration During Element Creation:**

- In the "More TCP/IP Settings" section, ensure the "Include Timeout" checkbox is unchecked. This should be done because the connector does not poll any endpoints, and retries are implemented internally by the connector logic.

### Initialization

After creating the element, the user must configure the following settings on the settings page:

- **Element Settings:**

  - **Ticket Storage Duration Limit:** The maximum duration tickets are stored (default: 90 days).
  - **Ticket Storage Count Limit:** The maximum number of tickets that can be stored (default: 1000).
  - **Ticket Creation Retry Count:** The number of times to retry creating a ticket if it fails (default: 1).
  - **Display Debug Page:** Option to enable or disable the debug page (default: Disabled).

- **API Settings:**

  - **Client ID:** The client identifier for authentication with the Orange Oceane Ticketing System.
  - **Client Secret:** The secret key for authentication.
  - **User ID:** The identifier of the user creating the tickets.

The user must then click the "Authenticate" button in the API Settings section to establish the connection with the Orange Oceane Ticketing System. Note that the "Client ID" and "Client Secret" are used for authentication, and the "User ID" is used to identify the user creating the tickets and is not used in the authentication process.

## Automation Scripts

The connector requires the "Orange Oceane Ticketing System" automation script to be installed on the DataMiner system. This script is essential for extending the alarm console menu with the "Create Ticket" option and handling the logic for ticket creation, including checking for existing tickets and prompting the user for ticket details.

## Hyperlinks

To enable the "Create Ticket" option in the alarm console's right-click menu, hyperlinks must be added to the DataMiner system. The following hyperlink configuration is an example how to extend the menu and links to the automation script:

```
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

**Parameters:**

- **Required Parameters:**
  - **DMA ID ([DMAID]):** The DataMiner Agent ID.
  - **Element ID ([EID]):** The ID of the element associated with the alarm.
  - **Alarm ID ([ROOTKEY]):** The unique identifier of the alarm.
  - **Element Name ([ENAME]):** The name of the element associated with the alarm.

- **Optional Parameters:**
  - **Alarm Value ([VALUE]):** The value of the alarm.
  - **Root Time ([ROOTTIME]):** The timestamp of the alarm's root cause, formatted as `yyyy-MM-ddTHH:mm:ssZ`.

This hyperlink configuration ensures that the "Create Ticket" option is available in the alarm console, triggering the automation script with the necessary alarm details.

> \[!NOTE\] For more information on configuring hyperlinks in DataMiner, refer to the DataMiner Hyperlinks Documentation.

## How to Use

To use this connector, follow these steps:

1. Create an element using the Orange Oceane Ticketing System connector in DataMiner, specifying the HTTP connection details and ensuring the "Include Timeout" checkbox is unchecked in the "More TCP/IP Settings."
2. On the settings page, configure the API Settings with the provided Client ID, Client Secret, and User ID, then authenticate.
3. Set the desired Element Settings, such as ticket storage limits, retry counts, and whether to display the debug page.
4. In the alarm console, right-click on an alarm and select "Create Ticket" from the menu.
5. If the ticket does not already exist, a dialog will appear prompting the user to enter ticket details, including:
   - Priority (required)
   - Urgency (required)
   - Technical Impact (required)
   - Client Impact
   - Description
6. After filling in the details, click "Create Ticket" to submit the request.
7. The connector will attempt to create the ticket:
   - If successful, it updates the alarm properties with the ticket ID and URL and adds the ticket to the Tickets table.
   - If unsuccessful, it adds the ticket to Tickets table with failed status and it records the failure in the "Failed Ticket Requests" table.

**Note:** The debug page can be enabled in the Element Settings to monitor ticket queue statuses for troubleshooting purposes.

## Interfaces

### Dynamic Interfaces

- **Virtual dynamic interfaces:**
  - **Tickets Table:** Contains created tickets with fields such as Instance, Ticket ID, Alarm ID, DataMiner ID, Element ID, Element Name, Created At, Priority, Urgency, Technical Impact, Client Impact, Root Cause, and Status.
  - **Failed Ticket Requests Table:** Contains information about failed ticket creation attempts, with fields such as Instance, Ticket ID, HTTP Error Code, App Error Code, Error Message, and Error Description.

These tables are updated by the connector as tickets are created or fail to be created.

## Debug Page

The connector provides a debug page (enabled via Element Settings) that displays the status of ticket queues:

- **Ticket Queue Processing Lock:** Indicates if the ticket processing is locked or not with the locked status indicating that the connector is currently processing the ticket.
- **Pending Ticket Creation Queue:** Shows the status of pending ticket creation requests (the buffer).

These can be useful for troubleshooting issues with ticket creation.