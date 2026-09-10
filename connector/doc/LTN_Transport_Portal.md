---
uid: Connector_help_LTN_Transport_Portal
---

# LTN Transport Portal

## About

The **LTN Transport Portal** connector provides DataMiner with centralized monitoring of LTN Transport Portal booking and distribution data. It gives operators a consolidated view of transport activity and service status.

## Key Features

- **Booking lifecycle monitoring**: Monitor scheduled, running, past, canceled, and unknown bookings.

- **Endpoint visibility**: Verify endpoint status, channel information, and traffic rates.

- **Distribution group monitoring**: Retrieve distribution groups and their associated endpoints to provide visibility into how transport paths are organized.

- **API health monitoring**: Expose the status and response information of the main API calls so operators can quickly identify communication or data retrieval issues.

- **Configurable polling**: Configure API-specific polling intervals, pagination, page sizes, and polling history to balance data freshness with API load.

- **Secure API authentication**: Authenticate through the portal's token endpoint using configured credentials and an API key.

- **Multithreaded HTTP requests**: Support parallel HTTP request handling for active-source and polling operations, with runtime statistics for thread usage, waiting threads, and command duration.

- **Web interface access**: Provide a configurable link to the LTN Transport Portal web interface directly from the element.

## Use Cases

### Monitor Transport Bookings

**Challenge**: Operators need to follow transport activity across multiple booking states and quickly identify bookings that require attention.

**Solution**: Use the booking pages to monitor scheduled, running, past, canceled, and unknown bookings, together with their timing, booking status, source and destination endpoints, rates, and API status.

**Benefit**: Operations teams gain a single operational view of booking activity and can more quickly investigate missing, failed, or unexpected bookings.

### Verify Endpoint and Distribution Health

**Challenge**: Transport issues can originate from an endpoint or from the way endpoints are organized into distribution groups.

**Solution**: Monitor source and destination endpoint status, connector state, traffic rates, and distribution group membership from DataMiner.

**Benefit**: Operators can identify endpoint-related problems and assess their impact on transport paths without switching between multiple interfaces.

## Technical Reference

### Prerequisites

- **DataMiner version 10.3.0.0 or higher** is required.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_LTN_Transport_Portal_Technical).
