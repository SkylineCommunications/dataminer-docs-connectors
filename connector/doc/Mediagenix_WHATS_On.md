---
uid: Connector_help_Mediagenix_WHATS_On
---

# Mediagenix WHATS On

The function of this connector is to receive and display data from a Mediagenix WHATS On service. The Mediagenix WHATS On software allows broadcasting and media companies to schedule and manage video and radio streams. The open architecture of the software allows users to define their own communication channel between service and connector, resulting in multiple versions of the connector.

## About

### Version Info

| Range              | Key Features                                                                  | Based on | System Impact |
|--------------------|-------------------------------------------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | - Initial version. <br>- Requests can be stored in DOM (from 1.0.0.12)        | -        | -             |
| 2.0.0.x [Obsolete] | - Finnish Broadcasting Company branch <br>- Communication through web service | -        | -             |
| 2.0.1.x [Obsolete] | Support for Unicode characters added.                                         | 2.0.0.4  | -             |
| 2.0.2.x [SLC Main] | Communication through RabbitMQ.                                               | 2.0.1.7  | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | TBD                    |
| 2.0.2.x   | 2.9.2.r1.588           |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 2.0.2.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

Depending on the connector range, you may need to configure the connection settings on the Configuration page of the element.

### Redundancy

There is no redundancy defined.

## How to use (range 1.0.0.x)

Most of the actions trigger an interaction with an element that's created based on the [BeIN Manager connector](https://catalog.dataminer.services/details/connector/3437). To link both elements, the parameters **Manager DMA ID**, **Manager Element ID** and **Manager Parameter ID** need to be filled in on the Settings page. 

From version 1.0.0.12 onwards, it's possible to store all requests as [DataMiner Object Model (DOM) instances](https://docs.dataminer.services/user-guide/Advanced_Modules/DOM/DOM.html). To enable this, please check the Settings page section.

### General Page

The General page only indicates if the services are running or not.

### Incoming Requests Page

The Incoming Requests page contains the **Incoming Requests** table and the identifier of the **Current Incoming Request**.

A request can be removed from the Incoming Requests table by pressing the **Delete** button of the corresponding row. This action won't remove the request in Whats On. 

Depending on the Manager DMA ID parameter, the BeIN Manager element or the corresponding DOM instance will be updated.

### Outgoing Requests Page

The Outgoing Requests page holds the **Outgoing Requests** table, as well as the **Commands** Resend Active and Resync Selected. The content of the Outgoing Requests table is equal to the content of the Incoming Requests table with the difference that sets can only be done from the Outgoing Requests table.

A request can be removed from the Outgoing Requests table by pressing the **Delete** button of the corresponding row. This action won't remove the request in Whats On.

A request can be adjusted in Whats On by pressing the **Send** button of the corresponding row in the Outgoing Requests table.

A request can be canceled in Whats On by pressing the **Cancel** button of the corresponding row in the Outgoing Requests table.

A request can get overwritten in the Outgoing Requests table with the corresponding entry from the Incoming Requests table by pressing the **Sync** button of the selected row in the Outgoing Requests table.

A subset of requests can be synchronized between DataMiner and Whats On by setting the togglebutton of the Outgoing Requests table **Select** column to Selected and pressing the **Resync Selected** button at the top of the page.

The requests that indicate booked, set up, running and error can be synchronized between DataMiner and Whats On by pressing the **Resend Active** button at the top of the page.

Depending on the Manager DMA ID parameter, the BeIN Manager element or the corresponding DOM instance will be updated.

### Settings Page

On here it's possible to enable or disable **Heartbeat** requests, specify **Expiration Times** and link an element that's created based on the BeIN Manager connector.

To enable request convertion to DataMiner Object Models, the **Manager DMA ID** parameter needs to be set to **DOM**. The parameters Manager Element ID and Manager Parameter ID can be left blank.

Once every day, the requests are synced between the Mediagenix Whats On element (Incoming Request table) and the BeIN Manager element if one is linked. In case the Manager DMA ID parameter is set to DOM, the connector will check the Incoming Request table and try to create the missing DataMiner Object Model instances. These actions can also be triggered manually by pressing the **Resync Requests** button at the bottom of the Settings page.

Once every hour, the connector will check for expired requests and will try to remove them from the Incoming and Outgoing Request table and the BeIN Manager element if one is linked.

Once every five minutes, the connector will check if there are requests (Outgoing Request table) that must be re-sent to Whats On and the BeIN Manager element (if one is linked) because sending it failed previously.

### Debug Page

The wsCurrentlyExchangedRequest parameter with ID 11000 can be used by a web service that receives the incoming requests. Messages that are set on this parameter are stripped and converted in table rows that are pushed to the Incoming and Outgoing Requests tables.

The message format is:
EXCHANGE_TAG;REQUEST_ID;REQUEST_TYPE;REQUEST_STATE;COLUMN_NAME_1:COLUMN_VALUE_1;...;COLUMN_NAME_N:COLUMN_VALUE_N

Cleaning the Incoming and Outgoing Requests tables is possible from the debug page. This will not remove the corresponding DOM instances if the **Manager DMA ID** parameter is set to **DOM**.

## How to use (range 2.0.2.x)

During startup of the element, the connector will start listening to several hardcoded RabbitMQ queues using the connection settings defined in the parameters.
Data coming in through these queues is parsed and stored in one of the multiple tables in the connector.

On the Configuration page of this connector, you can configure the connection settings for the RabbitMQ communication.

All other pages contain tables displaying the parsed data received through these RabbitMQ queues.
