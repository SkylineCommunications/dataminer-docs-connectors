---
uid: Connector_help_Amagi_Tellyo_Pro
---

# Amagi Tellyo PRO

The Amagi Tellyo PRO DataMiner connector integrates with a cloud-based platform of the same name for live clipping, editing, and publishing to all social and digital channels simultaneously. The Tellyo Pro platform enables the creation of short-form videos, including single clips, highlights, and montages of live or VOD content. The platform allows seamless editing with frame accuracy, adding branding elements, overlays, and graphics, and applying multiple aspect ratios before publishing across various destinations. Additionally, it uses live event metadata to automate and accelerate video production workflows and restream content to OTT and CDN streaming destinations simultaneously.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling address of the product.
- **IP port**: The IP port of the platform, by default *443*.
- **Bus address**: The bus address of the platform, by default *ByPassProxy*.

### Initialization

Specify the **Tellyo-token** on the **General** page. The connector will automatically send requests using this token and will report the response code in the **HTTP Request Status** parameter.

> [!NOTE]
> - The Tellyo Open API is a JSON-based REST API that allows external applications to manage basic tasks within their Tellyo account.
> - All Open API requests require a **Tellyo-Token** header, provided by Tellyo, to uniquely identify the integrating application.
> - The access token can only access one organization. Object IDs (e.g. channels, sources, recordings) are unique within a single region.
> - The same ID can be assigned to different channels in Europe and Australia, but you need a different access token to access those regions.

## How to use

This DataMiner connector offers management and monitoring capabilities for the Amagi Tellyo PRO Platform. Monitoring and configuration settings are retrieved through a polling mechanism that integrates with Tellyo's REST API.

The Tellyo PRO also integrates an [InterApp library](https://github.com/SkylineCommunications/SLC-S-Amagi-Tellyo-PRO-ConnectorAPI), enabling a running element to communicate with other DataMiner elements and Automation scripts. This library supports create, update, and delete actions for recordings.

Below you can find more information about the different data pages available in the element.

- **General**: Displays the Organization ID and Organization Name associated with the specified token. To store this token, use the **Tellyo-Token** parameter. The token will then be used to authenticate the integration and retrieve the necessary information.
- **Users**: Displays a table listing all users of the organization.
- **Channels**: Displays a table listing the available channels in the organization. The ID field can be used, for example, to manage recordings.
- **Sources**: Displays a table listing all sources linked to the organization.
- **Recordings**: Displays a table listing all recordings, linked to the channels and sources tables. A context menu is available with the following actions: add, edit, delete, start, and stop.  

> [!NOTE]
> When scheduling a recording, ensure you schedule at least 10 minutes ahead to allow the recording infrastructure sufficient time to initialize.

> [!IMPORTANT]
> This DataMiner connector is designed to integrate with DataMiner SRM solutions, where a channel is treated as a resource for scheduling recordings. The recordings table maps the booking ID of the event that requested the recording. To facilitate easy updates to the stop recording time if the booking is extended, the DataMiner element will automatically detect changes in the linked bookings and request a stop time update to the Tellyo PRO platform. This can be monitored in the ***General > Debug*** subpage.