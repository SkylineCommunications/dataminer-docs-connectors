---
uid: Connector_help_Mediagenix_WHATS_On
---

# Mediagenix WHATS On

The function of this connector is to receive and display data from a Mediagenix WHATS On service. The Mediagenix WHATS On software allows broadcasting and media companies to schedule and manage video and radio streams. The open architecture of the software allows users to define their own communication channel between service and connector, resulting in multiple versions of the connector.

## About

### Version Info

| Range              | Key Features                                                                    | Based on | System Impact |
|--------------------|---------------------------------------------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | - Initial version. <br>- Requests can be stored in DOM (from 1.0.0.12 onwards). | -        | -             |
| 2.0.0.x [Obsolete] | - Finnish Broadcasting Company branch. <br>- Communication through web service. | -        | -             |
| 2.0.1.x [Obsolete] | Support for Unicode characters added.                                           | 2.0.0.4  | -             |
| 2.0.2.x [SLC Main] | Communication through RabbitMQ.                                                 | 2.0.1.7  | -             |

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

Most of the actions trigger an interaction with an element that is created based on the [BeIN Manager connector](https://catalog.dataminer.services/details/connector/3437). To link the elements, the parameters **Manager DMA ID**, **Manager Element ID**, and **Manager Parameter ID** need to be filled in on the Settings page.

From version 1.0.0.12 onwards, all requests can be stored as [DataMiner Object Model (DOM) instances](https://docs.dataminer.services/user-guide/Advanced_Modules/DOM/DOM.html). For more information, see [Settings Page](#settings-page).

### General Page

The General page indicates whether the services are running.

### Incoming Requests Page

The Incoming Requests page contains the **Incoming Requests** table and the identifier of the **Current Incoming Request**.

You can remove a request from the Incoming Requests table by clicking the **Delete** button of the corresponding row. This action will not remove the request in Whats On.

Depending on the Manager DMA ID parameter, the BeIN Manager element or the corresponding DOM instance will be updated.

### Outgoing Requests Page

The Outgoing Requests page contains the **Outgoing Requests** table as well as the commands **Resend Active** and **Resync Selected**.

The content of the Outgoing Requests table is equal to that of the Incoming Requests table, except that sets can only be done from the Outgoing Requests table.

- To remove a request from the Outgoing Requests table, click the **Delete** button of the corresponding row. This action will not remove the request in Whats On.

- To adjust a request in Whats On, click the **Send** button of the corresponding row in the Outgoing Requests table.

- To cancel a request in Whats On, click the **Cancel** button of the corresponding row in the Outgoing Requests table.

- To overwrite a request in the Outgoing Requests table with the corresponding entry from the Incoming Requests table, click the **Sync** button of the selected row in the Outgoing Requests table.

- To synchronize a subset of requests between DataMiner and Whats On, set the toggle button in the **Select** column of the Outgoing Requests table to *Selected* and clicking the **Resync Selected** button at the top of the page.

- To synchronize requests between DataMiner and Whats On that are indicated as booked, set up, running, and error, click the **Resend Active** button at the top of the page.

Depending on the Manager DMA ID parameter, the BeIN Manager element or the corresponding DOM instance will be updated.

### Settings Page

On this page, you can enable or disable **Heartbeat** requests, specify **Expiration Times**, and link an element that is created based on the BeIN Manager connector.

To enable request conversion to DataMiner Object Models, the **Manager DMA ID** parameter needs to be set to **DOM**. The parameters Manager Element ID and Manager Parameter ID can be left blank.

Once every day, the requests are synced between the Mediagenix Whats On element (Incoming Request table) and the BeIN Manager element if one is linked. In case the Manager DMA ID parameter is set to DOM, the connector will check the Incoming Request table and try to create the missing DataMiner Object Model instances. You can also trigger these actions manually by clicking the **Resync Requests** button at the bottom of the Settings page.

Once every hour, the connector will check for expired requests, and it will try to remove them from the Incoming and Outgoing Request table and the BeIN Manager element if one is linked.

Once every five minutes, the connector will check if there are requests (Outgoing Request table) that must be re-sent to Whats On and the BeIN Manager element (if one is linked) because sending them failed previously.

### Debug Page

The *wsCurrentlyExchangedRequest* parameter with ID 11000 can be used by a web service that receives the incoming requests. Messages that are set on this parameter are stripped and converted into table rows that are pushed to the Incoming and Outgoing Requests tables.

This is the message format:
`EXCHANGE_TAG;REQUEST_ID;REQUEST_TYPE;REQUEST_STATE;COLUMN_NAME_1:COLUMN_VALUE_1;...;COLUMN_NAME_N:COLUMN_VALUE_N`

Cleaning the Incoming and Outgoing Requests tables is possible from the Debug page. This will not remove the corresponding DOM instances if the **Manager DMA ID** parameter is set to **DOM**.

## How to use (range 2.0.2.x)

During startup of the element, the connector will start listening to several hardcoded RabbitMQ queues using the connection settings defined in the parameters. Data coming in through these queues is parsed and stored in one of the multiple tables in the connector.

On the Configuration page of this connector, you can configure the connection settings for the RabbitMQ communication.

All other pages contain tables displaying the parsed data received through these RabbitMQ queues.
