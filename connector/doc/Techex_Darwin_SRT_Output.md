---
uid: Connector_help_Techex_Darwin_SRT_Output
description: "Learn how the Techex Darwin SRT Output connector monitors module information, real-time statistics, and listeners."
---

# Techex Darwin SRT Output

## About

The Techex Darwin SRT Output connector enables monitoring of the subtypes SRT Output of the Techex Darwin via HTTP and Kafka subscription. It provides users with access to real-time data directly within DataMiner.

## Key Features

- **Module information**: Retrieve and monitor all generic information of the SRT Output modules.
- **Real-time statistics**: View statistics updated in real time for each subscribed module thanks to Kafka subscriptions.
- **Listener monitoring**: Retrieve data from the linked listeners.

## Technical Information

When you configure a DataMiner element using this connector, specify the **IP address** linked to the HTTP connection.

Once the element is configured, you will need to configure credentials on its **Communication Settings** page to start the polling for the HTTP connection, and you will have to complete the Kafka configuration on the **Kafka Settings** page.

When you configure the element, make sure that the **Client ID** and **Group ID** are **unique** across the entire DataMiner System for that specific Techex Darwin device. Conflicting IDs will make it impossible to correctly establish the subscription.

When everything has been correctly configured, the connector polls the SRT Output module for general information over HTTP and receives real-time updates through a Kafka subscription.
