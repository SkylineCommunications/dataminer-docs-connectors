---
uid: Connector_help_EVS_Neuron_NAP_-_CONVERT_Technical
---

# EVS Neuron NAP - CONVERT

## About

The EVS Neuron NAP - CONVERT connector enables monitoring and control of Neuron Convert devices, which provide high-density video and audio format conversion. This allows real-time visibility and management of conversion operations within broadcast environments.

This connector communicates with the device using the **REST API (v1.0.0)** over **HTTP**. Firmware version **6.x** is required.

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x | Initial version. Uses a smart-serial connection with support for unsolicited messages. | - | - |
| 2.0.0.x [SLC Main] | Redesigned to use REST API over HTTP. No longer supports unsolicited messages. | - | - |

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|--|--|--|--|--|
| 1.0.0.x | Yes | Yes | - | - |
| 2.0.0.x | No | Yes | - | - |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (fixed value: *2072*).

### Initialization

Once the element has been created in DataMiner, the **General** page allows you to configure the **API Version** used to communicate with the device. On the **Polling Settings** page, you can configure the polling intervals for each data group and enable or disable polling per group.

## How to use

The connector polls data at element startup. On-demand polling can be triggered via the **Polling Settings** page.

### General Page

The **General** page provides essential device identity information, including the **Product Name**, **Product Version**, **Model Version**, and **API Version**. The Element Configuration section on this page allows you to set the API version and access the **Polling Settings** and **Protocol Queue** pages.

### Polling Settings Page

The **Polling Settings** page contains the **Polling Manager** table, which lists all configurable polling groups. For each group you can view and adjust the **polling interval**, **admin status**, and the **last poll result**. This page gives you full control over how frequently each data set is retrieved from the device.

### Protocol Queue Page

The **Protocol Queue** page provides insight into the connector's internal request handling. When changes are made, the connector builds and queues HTTP requests accordingly, and may bundle multiple updates into a single request where possible. This page shows the item currently being processed and the full queue of pending requests, which is useful for understanding connector behavior or diagnosing unexpected communication patterns.

### Video Processing Page

The **Video Processing** page provides a tree control that gives an overview of all configured **video processing paths** and their associated **channels**. This is the main entry point for navigating the conversion processing hierarchy.

### Video Path Processing Page

The **Video Path Processing** page contains a table listing all video paths on the device, including their **input/output wire modes**, **UHD settings**, and **proxy output configuration**.

### Video Channel Processing Page

The **Video Channel Processing** page contains a table listing all video processing channels, including their **assigned path**, **input selection**, **lock status**, **output format**, and **deinterlacer settings**. From this page you can navigate to the following sub-pages:

- **Input Formats**: Lists the **active**, **main**, and **backup input formats** per channel. This allows you to detect format mismatches or active failovers.
- **Delay & Frame Sync**: Shows the **frame delay**, **vertical and horizontal delay**, **IO delay**, and **frame sync alignment** settings per channel.
- **Embedders**: Displays and allows configuration of the **audio and data embedder mode** and **audio group selection** per channel.
- **RGB Gain**: Shows the **RGB gain**, **black levels**, **clipping**, and **hue shift** color correction settings per channel.
- **HDR Conversion**: Displays the **color space mode**, **input/output color spaces**, **normalization**, **LUT selection**, and **matrix mode** for HDR conversion per channel.
- **Scaling**: Contains the **scaling conversion mode**, **low-pass filter settings**, and **horizontal sharpness controls** per channel.
