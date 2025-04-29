---
uid: Connector_help_Interra_Orion_Real-Time_Content_Monitor_Technical
---

# Interra Orion Real-Time Content Monitor

## About

This is a DataMiner connector for the Interra Systems' ORION, a real-time content monitoring system used in IP-based video delivery infrastructures. ORION monitors multiple aspects of video streams including Quality of Service (QoS), Quality of Experience (QoE), closed captions, loudness compliance, and ad insertion verification. It supports real-time analysis and logging of streaming content, enabling service providers to track alerts, alarms, and impairments across large-scale deployments.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses a HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

## How to use 

### General

On this page, you can configure the user's authentication details to the system's, namely **Username** and **Password**. You can also monitor the authentication status of this user's credentials.

### Feeds

This page provides all information about the available feeds. It also monitors the status of the request to get all available feeds and their monitoring status.

### Feed PIDs

This page displays all information about the available feed PIDs. It also monitors the status of the requests to get the PIDs of each feed.

### Services

This page displays all information about the available services.
