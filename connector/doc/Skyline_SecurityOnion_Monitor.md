---
uid: Connector_help_Skyline_SecurityOnion_Monitor
---

# Skyline SecurityOnion Monitor

This connector can be used to retrieve and monitor data collected by a SecurityOnion instance.

## About

### Version Info

| Range              | Features | Based on | System Impact |
|--------------------|----------|----------|---------------|
| 1.0.0.x [SLC Main] | -        | -        | -             |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 |                     |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

When you have created the element, go to the **Configuration** page and configure the following parameters:

- **Elasticsearch URL**: Specify the URL of the SecurityOnion Elasticsearch instance, including the port number.
- **Elasticsearch Username**: Specify the username that will be used to authenticate towards the Elasticsearch instance.
- **Elasticsearch Password**: Specify the password that will be used to authenticate towards the Elasticsearch instance.
- **AbuseIP API Key [Optional]**: Specify the API key to retrieve information from the AbuseIP API.

## How to use

With this connector, you can retrieve and monitor connections that are logged by a SecurityOnion instance. The connector can retrieve additional information from the AbuseIP api as well.

You can make snapshot recordings of all connections that were made during the recording. It is also possible to compare two recordings with each other.

You can also whitelist connections. This allows you to declutter the list of connections.

## Notes

To ensure the connector can retrieve data from the Elasticsearch instance, make sure to [whitelist the IP address of the DataMiner Agent on the SecurityOnion instance](https://docs.securityonion.net/en/2.3/so-allow.html).
