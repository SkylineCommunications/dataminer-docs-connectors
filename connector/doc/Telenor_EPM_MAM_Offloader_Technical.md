---
uid: Connector_help_Telenor_EPM_MAM_Offloader_Technical
---

# Telenor EPM MAM Offloader

## About

In the Telenor DMS, the **Telenor EPM MAM Consumer** elements receive messages from a RabbitMQ server. Some of those messages must be saved in an OpenSearch database. To achieve this, the consumer elements push the messages towards the **Telenor EPM MAM Offloader** element using parameter sets. The offloader element buffer those messages and then send them periodically to OpenSearch using Bulk requests.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

On the *General* page, the settings of the OpenSearch database must be filled in:

- **User Name**: The OpenSearch user name.
- **Password**: The OpenSearch password.
- **Nodes**: This table contains the list of the nodes in the OpenSearch database. A node can be added by right-clicking the table and selecting *Add Node...*

## How to Use

On the **Configuration** page, the user can view statistics about the number of messages processed. The user can also change the name of the data streams used for indexing.

The **Rollover** page displays a table showing all the underlying indexes used by the selected data streams and the number of documents they contain. For each data stream, a new index is created every day around midnight by performing a *Rollover* request. The user can choose for how many days an index must remain in the database using the **Index TTL** parameter.
