---
uid: Connector_help_Telefonia_por_Cable_S.A_de_C.V._Ticketing_BE_Technical
---

# Telefonia por Cable S.A de C.V. Ticketing BE

## About

The Telefonia por Cable S.A de C.V. Ticketing BE connector is used to send and update all the tickets processed by Telefonia por Cable S.A de C.V. Ticketing WM into the Cherwell Platform and SFyC Platform via API.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The IP address of the host that will contain the endpoints for the ticket operations.
- **IP port**: The IP port of the destination (default: *80*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

When you have created the element, configure the following parameters:

- **Ticketing Processing**: If enabled, all tickets received will be processed and sent to the respective API. If disabled, no tickets will be processed, but all tickets will still be received.
- **Max Retries**: Specifies how many retries a ticket has for each operation, so if a ticket fails the connector will try again. If the maximum number of retries is reached, the ticket will be marked as *Error* and will not be processed further.
- **Max Tickets Per Request**: Specifies how many tickets are sent in each operation request to avoid sending all tickets in one single request. This means that it can take multiple requests to fulfill an operation for all available tickets.

## How to Use

This connector will receive tickets coming from the connector Telefonia por Cable S.A de C.V. Ticketing WM via InterApp communication. These tickets will then be added to the Ticket Overview table and marked as *Received*.

If **Ticketing Processing** is enabled, the connector will start to process all tickets following this flow of actions:

- **Retrieval of existing tickets**: A request will be sent to retrieve all available tickets both from "Falla de Linea" and "SNR".
- **Check of existing tickets to be sent**: Based on the retrieved existing tickets, a comparison will be done to check which tickets-to-be-sent are already in the platform.
- **Adding a note to existing tickets**: For all tickets-to-be-sent that are already in the platform, a request to add a note to the existing ticket will be sent. If this is completed successfully, the ticket will be completed; otherwise, the connector will retry until it reaches the maximum number of retries.
- **Creation of tickets**: For all tickets to process that do not have an existing ticket in the platform, a request to create a ticket will be made.
- **Creation of OT**: After the tickets have been created, the ticket number is used for the work order, and then a request to create a work order for each ticket will be made.
- **Update of ticket OT**: After the work orders have been created, the OT number is used to send a request to update the OT number on the ticket. If this is completed successfully, the ticket will be completed.
