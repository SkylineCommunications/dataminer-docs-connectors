---
uid: Connector_help_Techex_Darwin_SRT_Input
---

# Techex Darwin SRT Input


## About

The Techex Darwin SRT Input connector enables monitoring of the subtypes SRT Output of the Techex Darwin via HTTP and Kafka subscription. It provides users with access to real-time data directly within DataMiner.

## Key Features

- **Module information**: Retrieve and monitor all generic information of the SRT Input modules.
- **Real time Statistics**: By subscription of kafka each subscripted module contains direct updates of the statistics.
- **Reliability and Recovery monitoring**: Retrieve data from each SRT Input Module.

## Technical Information

When you configure a DataMiner element using this connector, specify the IP address linked to the HTTP connection.

Once an element is configured, the connector will need to have credentials being configured in the "Communication Settings" page to start the polling for the HTTP connection. 
Next to this, you will need to complete the full configuration of the Kafka Settings page. Make sure that the Client ID and Group ID are unique for the full DataMiner System for the specific Techex Darwin device.
Conflicting IDs will make it so the subscription will not be correctly establish.


After this the connector will poll generic information of the SRT Input module via the HTTP connection and real-time updates via Kafka subscription.
