---
uid: Connector_help_Techex_Darwin_SRT_Input
description: Learn how to configure and use the Techex Darwin SRT Input connector to monitor module information and real-time statistics.
---

# Techex Darwin SRT Input

## About

The Techex Darwin SRT Input connector enables monitoring of the subtypes SRT Input of the Techex Darwin via HTTP and Kafka subscription. It provides users with access to real-time data directly within DataMiner.

## Key Features

- **Module information**: Retrieve and monitor general information about the SRT Input modules. Including network and transport configuration, FEC configuration. 
- **Real-time statistics**: View statistics updated in real time for each subscribed module thanks to Kafka subscriptions. These include stream, traffic, latency statistics for each module. This helps to know direct after event happens the current status of the statistics.
- **Reliability and recovery monitoring**: Retrieve data from each SRT Input Module. It indicates the network status and recovery of the network clear.

## Technical Information

When you configure a DataMiner element using this connector, specify the **IP address** linked to the HTTP connection.

Once the element is configured, you will need to configure credentials on its **Communication Settings** page to start the polling for the HTTP connection, and you will have to complete the Kafka configuration on the **Kafka Settings** page.

When you configure the element, make sure that the **Client ID** and **Group ID** are **unique** across the entire DataMiner System for that specific Techex Darwin device. Conflicting IDs will make it impossible to correctly establish the subscription.

When everything has been correctly configured, the connector polls the SRT Input module for general information over HTTP and receives real-time updates through a Kafka subscription.
