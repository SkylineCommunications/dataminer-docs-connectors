---
uid: Connector_help_LTN_Transport_Portal_Technical
---

# LTN Transport Portal

## About

The LTN transport portal is a platform for live video transmission solutions. It uses a global network of Points of Presence (PoPs) to ensure efficient and low-latency video delivery. With intelligent adaptive bit rate (ABR) encoding and dynamic stream routing, it optimizes video quality and routing paths based on real-time network conditions.

The **LTN Transport Portal** connector provides DataMiner with centralized monitoring of LTN Transport Portal booking and distribution data. It retrieves booking information, endpoint details, endpoint statuses, distribution groups, and API health through the LTN Transport Portal HTTP API, giving operators a consolidated view of transport activity and service status.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

The HTTP connection uses a default timeout of *20s*.

### Initialization

When the element has been created, specify the username, password, and API key to establish a connection with the portal. You will need to request an API key from the vendor.

## How to Use

After the credentials have been configured and the connector has obtained an authentication token, DataMiner automatically retrieves booking, endpoint, and distribution group information from the portal every minute.

### Booking Endpoints

Use this page to track source, destination, standard converter, and unknown booking endpoints with connector state, endpoint status, channel information, and traffic rates in packets per second and bits per second.

### Bookings

Use this page to monitor scheduled, running, past, canceled, and unknown bookings, including booking status, timing, resolution, and work order information.

### Distribution Group

Use this page to retrieve distribution groups and their associated endpoints to provide visibility into how transport paths are organized.

### Polling Configurations

Use this page to configure API-specific polling intervals, pagination, page sizes, and polling history to balance data freshness with API load.

### Multi-Threading

Use this page to review multithreading statistics, including active threads and waiting threads, command durations, and thread usage for active-source and polling operations, to troubleshoot connector performance.

## Notes

### Supported API data

The connector uses the LTN Transport Portal API to retrieve:

- Bookings and booking endpoints.
- Booking endpoint statuses.
- Distribution groups and distribution group endpoints.
- An authentication token through the portal token endpoint.

This information can be used to track transport activity, validate service availability, and investigate operational issues.
