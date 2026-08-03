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

### Provisioning

The **Channels**, **Products**, **Stream Types** and **Streams** pages each allow you to add, edit or delete entries. To add an entry, click the corresponding page button (e.g. **Add Channel**), fill in the fields on the subpage, and confirm with the button at the bottom of the subpage.

### Stream Availability

Via the **Config Time Period** page button, you can access a subpage where you can specify the time frame for which the stream availability statistics (availability, outage count, outage duration, MTBF and MTTR) are calculated.

### VOD Polling

The **VOD Status**, **Detailed VOD Status** and **Manifest Trawl - Failed Assets** pages only apply to data sources that have VOD services.

> [!IMPORTANT]
> If the data source does not support VOD, disable the **VOD Polling** toggle button. If you do not, the element can go into timeout because of the resulting 404 NOT FOUND responses.

## Notes

- As from range 1.0.1.x, the **Live Status Detail** table implements the status details by row instead of by column, so it contains more rows than in the 1.0.0.x range. The columns are adjusted accordingly.
