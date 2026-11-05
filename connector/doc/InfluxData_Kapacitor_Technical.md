---
uid: Connector_help_InfluxData_Kapacitor_Technical
---

# InfluxData Kapacitor

## About

This connector allows you to monitor alarms through the InfluxData Kapacitor HTTP API.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

## How to use

On the **General** page of the element, you can monitor **alarms**. HTTP requests are used to retrieve alarms based on the URL specified on the **Configuration** page.

You can configure the URL manually by changing the **Alarm Request URL**, which will overwrite the Topic ID and Min-Level settings. Alternatively, you can provide the **Topic ID** and **Min-Level**, which will automatically build the expected request URL.

Under the **Polling Configuration**, you can set the automatic polling interval for the alarms. If the **State** toggle button is set to *Disabled*, the alarms will not be polled based on the polling interval, but it will still be possible to trigger the polling with the **Refresh on Demand** button.

The **Debug** page displays the response code and full raw response of the last requests. To see the actual response, a built-in DataMiner tool called Stream Viewer can be used. You can access it by right-clicking the element in the Surveyor and selecting View > Stream Viewer.
