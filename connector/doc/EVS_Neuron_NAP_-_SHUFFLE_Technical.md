---
uid: Connector_help_EVS_Neuron_NAP_-_SHUFFLE_Technical
description: "Configure and use the EVS Neuron NAP - SHUFFLE connector in DataMiner, including HTTP REST API setup, polling options, and audio channels."
---

# EVS Neuron NAP - SHUFFLE

## About

The EVS Neuron NAP - SHUFFLE connector enables real-time monitoring and control of Neuron Shuffle devices, which provides large-scale IP audio routing and processing.

This connector communicates with the device using the **REST API (v2.0.0)** over **HTTP**. Firmware version **6.x** is required.

## Configuration

### Connections

#### HTTP Main Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

Once the element has been created in DataMiner, the **General** page allows you to configure the **API Version** used to communicate with the device. Fill in the IP address of the device to start monitoring it.

On the **Polling Settings** page, you can configure the polling intervals for each data group and enable or disable polling per group.

## How to Use

The connector polls data as soon as the **IP Address** parameter is filled in with the correct IP address. On-demand polling can be triggered via the **Polling Settings** page.

### General Page

The **General** page provides essential device identity information, including the **Product Name**, **Product Version** and **API Version**. The Element Configuration section on this page allows you to set the API version and access the **Polling Settings** and **Protocol Queue** pages.

### Polling Settings Page

The **Polling Settings** page contains the **Polling Manager** table, which lists all configurable polling groups. For each group, you can view and adjust the **polling interval**, **admin status**, and the **last poll result**. This page gives you full control over how frequently each dataset is retrieved from the device.

### Protocol Queue Page

The **Protocol Queue** page provides insight into the connector's internal request handling. When changes are made, the connector builds and queues HTTP requests accordingly, and it may bundle multiple updates into a single request where possible. This page shows the item currently being processed and the full queue of pending requests, which is useful for understanding connector behavior or diagnosing unexpected communication patterns.

### Input/Channel Configuration Pages

The **Audio Delay Banks**, **MADI Inputs**, **MADI Outputs**, **IP Inputs**, and **IP Outputs** parameters enable monitoring and configuration for the corresponding inputs, outputs, and channels.
