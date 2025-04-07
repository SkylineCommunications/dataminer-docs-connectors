---
uid: Connector_help_Telefonia_por_Cable_S.A_de_C.V._Ticketing_BE_Technical
---

# Telefonia por Cable S.A de C.V. Ticketing BE

The Telefonia por Cable S.A de C.V. Ticketing BE connector is used to send and update all the tickets processed before by Telefonia por Cable S.A de C.V. Ticketing WM into the Cherwell Platform and SFyC Platform via API. 

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components                                                                                     | Exported Components |
|---------|-----------------|---------------------|-------------------------------------------------------------------------------------------------------|---------------------|
| 1.0.0.x | No              | Yes                 | - | -                   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: IP Address of the host that will contain the endpoints for the ticket operations.
  - **IP port**: The IP port of the destination. (default: *80*)
  - **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.


### Initialization

Indicate if additional configuration of parameters is necessary in a newly created element.

#### Configuration

- *Ticketing Processing*: If enabled all tickets received will be processed and will be sent to the respective API. If disabled not ticket will be processed, yet all tickets will still be received.
- *Max Retries*: Specifies how many retries a ticket has for each operation, so if the ticket fails it will try again, if max retries are reached the ticket will be marked as Error and will not be further processed. 
- *Max Tickets Per Request*: Specifies how many tickets are sent in each operation request to avoid sending all tickets in one single request. This means it can take multiple request to fulfill an operation for all available tickets.


## How to use

This connector will receive tickets via Interapp coming from the connector Telefonia por Cable S.A de C.V. Ticketing WM, this tickets when received will be added to the Ticket Overview table and marked as Received.

If *Ticketing Processing* is enabled, it will start to process all tickets following the next flow of actions:

- *Retrieval of existing tickets*: A request will be sent to retrieve all available tickets both from "Falla de Linea" and "SNR"
- *Check of existing tickets to be sent*: Based on the retrieved existing tickets, a comparison will be done to check which tickets-to-be-sent are already in the platform.
- *Add Note to Existing Tickets*: For all tickets-to-be-sent that are already in the platform a request to Add a Note to the existing ticket will be sent, if completed successfully the ticket will be completed, otherwise it will retry until it reaches the maximum number of retries.
- *Create Tickets*: For all tickets to process that do not have a existing ticket in the platform, a request to create a ticket will be done.
- *Create OT*: After the tickets have been created the ticket number is used for the work order, then a request to create a work order for each ticket will be done.
- *Update Ticket OT*: After the work orders have been created, the OT number is used to create a request to update the OT number on the ticket and then is sent. if completed successfully the ticket will be completed.


