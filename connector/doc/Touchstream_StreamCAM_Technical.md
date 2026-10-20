---
uid: Connector_help_Touchstream_StreamCAM_Technical
---

# Touchstream StreamCAM

## About

This is an HTTPS-based connector that can be used to monitor and configure **Touchstream StreamCAM**, a cloud-based stream monitoring solution.

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination. The default value is *443*.
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy*.

### Initialization

To start using this connector, specify the **Authorization Token** and **X-TS-ID Token** on the **General** page of the element.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### Dynamic Streams

Dynamic streams are how event-based monitoring is provisioned. Instead of configuring the streams for each event by hand, you define a reusable **template** describing the streams that an event of that type needs. When an event is received, the connector expands the assigned template into concrete streams and provisions them in StreamCAM.

The flow is:

1. An event arrives, either from an external system or entered manually, and lands as a row in the **Dynamic Streams Provisioning** table.
1. The connector looks up the template name(s) on that row in the **Event Template** table.
1. Every matching template row is expanded into one stream, grouped per dynamic group.
1. The resulting streams are sent to StreamCAM in a bulk call per dynamic group, and start being monitored.
1. When the event ends, the streams are deactivated and eventually archived or deleted.

#### Dynamic Streams Template

The **Dynamic Streams Template** page holds the **Event Template** table. Rows are keyed by template name, and a template consists of **all** rows sharing the same **Template Name**. There is one row per stream that a template should produce. Each row defines the **Product**, **Format**, **CDN**, **Channel**, **Manifest**, **Headers**, **Environment**, the Adobe equivalents, and the **Dynamic Group** the resulting stream belongs to.

To create a template, enter a name in the **Template Name** box and click **Add Template**, then fill in the rows. Existing rows can be copied or removed with the **Duplicate** and **Delete** buttons on the row.

The **Manifest** column accepts placeholders that are substituted with the event's own values at provision time:

| Placeholder | Replaced with |
|-------------|---------------|
| `{{Event_ID}}` | The event ID of the provisioned event |
| `{{YoSpace_Stream_ID_HLS}}` | The YoSpace HLS stream ID of the event |
| `{{YoSpace_Stream_ID_MPD}}` | The YoSpace MPD stream ID of the event |

This is what allows a single template row to serve every event of that type: the manifest URL is written once, with the event-specific part left as a placeholder.

#### Dynamic Groups

The **Dynamic Groups** page lists the groups that streams are provisioned into, each with its **Schedule Group**, **Polling Subscription**, and **Monitor Concurrency**. The **Dynamic Group** column of a template row determines which group the resulting stream is created in, and the connector sends one bulk API call per dynamic group.

> [!IMPORTANT]
> A template row is skipped if its **Dynamic Group** cannot be resolved against the Dynamic Groups table, or if its combination of **Product**, **Format**, **CDN** and **Environment** does not match an entry in the **Stream Types** table. The rest of the template is still provisioned, so a partially provisioned event usually means one of these two lookups failed. The skipped rows are logged in the element logging.

#### Dynamic Streams Provisioning

The **Dynamic Streams Provisioning** table holds one row per event, showing the assigned **Template**, **Event ID**, **Event Name**, **Event Label**, **Booking ID**, **Start Date**, **End Date** and the time it was provisioned. A row can reference several templates at once by specifying a comma-separated list of template names, in which case the streams of all listed templates are merged.

Each row has a **Provision** and a **Deactivate** button to trigger the action manually. The **Results** column reports the state of the last action:

| Result | Meaning |
|--------|---------|
| *Not Provisioned* | The event is known, but its streams have not been created yet. |
| *In Progress* | A provision action is running. |
| *Deactivating* | A deactivation action is running. |
| *Updating Dynamic Groups* / *Updating Manifests* | An update action is running. |
| *Error. One or more template names not found* | The template name on the row does not exist in the Event Template table. |

> [!NOTE]
> Provisioning and deactivation are rejected while an action is already running for that row, so a row stuck on *In Progress* will ignore further requests until the running action completes.

#### Provisioning from an External System

Provisioning is normally driven by another system rather than by the buttons. An external caller, such as an automation script triggered by a booking system, writes a JSON payload to the **SRM Parameter** of the element. The connector parses it and performs the requested action.

The payload identifies the event (`EventId`, `EventName`, `EventLabel`, `BookingId`, `AssetId`, `EventStartDate`, `EventEndDate`), names the template(s) to apply (`TemplateName`), supplies the placeholder values (`YoSpaceStreamIdHls`, `YoSpaceStreamIdMpd`), and sets the requested `Action`:

| Action | Value | Effect |
|--------|-------|--------|
| Provision | 0 | Creates the streams for the event from its template(s). |
| Deactivate | 1 | Deactivates the event's streams. |
| Update | 4 | Moves the event's streams to different dynamic groups or dates. |
| ManifestUpdate | 5 | Updates the manifests of already provisioned streams. |
| ManifestDeactivation | 6 | Deactivates specific manifests of the event. |

Rows are matched on **Booking ID**: a payload whose booking ID is already present updates that row, and any other payload adds a new row. As an alternative to templates, the payload can carry an explicit list of manifests, in which case the streams are built from those directly.

> [!NOTE]
> If **Follow Mode** is active on a provision row, the connector periodically executes the automation script configured in **Automation Script Name**, passing it the row ID and booking ID, and reports a failure once **Automation Failure Time** has elapsed.

#### Monitoring Results and Cleanup

Provisioned streams and their monitoring results appear on the **Dynamic Streams**, **Dynamic Streams Overview**, and **Dynamic Streams Status Detail** pages. Streams that are no longer active move to the non-active dynamic streams set, whose polling is controlled by the **Non-Active Streams Polling** setting.

Cleanup of finished events is configurable:

- **Streams Deletion**: Enables or disables automatic cleanup. Nothing is removed while this is disabled.
- **Max Time of Stream Storage**: How long, in hours after the event end date, a stream is kept before it is cleaned up.
- **Streams Deletion Method**: Whether an expired stream is deleted outright or archived in StreamCAM.
- **Delete Archived Streams Automatically**: When this is enabled, archived streams are deleted as well.

### Managing Channels, Products, Stream Types, and Streams

Independently of the dynamic streams, the **Channels**, **Products**, **Stream Types**, and **Streams** pages each allow you to add, edit, or delete entries. To add an entry, click the corresponding page button (e.g., **Add Channel**), fill in the fields on the subpage, and confirm with the button at the bottom of the subpage.

Note that the **Stream Types** table is also used to resolve the streams generated from a template, so a product, format, and CDN combination used in a template must exist here.

### Stream Availability

Via the **Config Time Period** page button, you can access a subpage where you can specify the time frame for which the stream availability statistics (availability, outage count, outage duration, MTBF, and MTTR) are calculated.

### VOD Polling

The **VOD Status**, **Detailed VOD Status**, and **Manifest Trawl - Failed Assets** pages only apply to data sources that have VOD services.

> [!IMPORTANT]
> If the data source does not support VOD, disable the **VOD Polling** toggle button. If you do not, the element can go into timeout because of the resulting 404 NOT FOUND responses.

## Notes

As from range 1.0.1.x, the **Live Status Detail** table implements the status details by row instead of by column, so it contains more rows than in the 1.0.0.x range. The columns are adjusted accordingly.
