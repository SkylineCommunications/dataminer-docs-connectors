---
uid: Connector_help_Vitec_EZ_TV
---

# Vitec EZ TV

## About

This connector interfaces with the VITEC EZ TV Management Web-API (Version 8.3.1.0) to facilitate the automated management of IPTV and Digital Signage assets. It allows for the retrieval of existing channel lineups and endpoint configurations, as well as the provisioning of new static channels and Set-Top Box (STB) endpoints. The connector utilizes token-based authentication and adheres to the API's strict pagination and permission requirements.

## Key Features

- **Channel Inventory Retrieval**: Retrieves a comprehensive list of EZ TV Channels permitted for the user, supporting pagination via offset and limit, and filtering by attributes such as name, type (e.g., IPV4, RTP), or multicast IP.

- **Static Channel Provisioning**: Enables SysAdmin Users to create new static channels by specifying essential details like channel name, number, IP address, port, and stream type (IPV4, URLW, RTP, etc.).

- **Endpoint Asset Discovery**: Fetches lists of Digital Signage Endpoints (STBs/Players) with detailed status information, including current mode (IPTV/DigitalSign), firmware version, and connectivity status (online/offline).

- **Endpoint Provisioning**:Allows SysAdmin Users to register new endpoints into the system by providing required fields such as IP address, name, MAC address, and endpoint ID.

- **Manual Backup Configuration**: Supports the definition of manual backup streams (e.g., a secondary multicast IP or URL) when creating a primary channel to ensure redundancy.

## Use Cases

### Automated Channel Lineup Synchronization

**Challenge**: Maintaining an external program guide or internal database that matches the current IPTV channel lineup is difficult due to frequent manual updates on the VITEC server.

**Solution**: Use the connector to periodically poll the GET /channels endpoint, using the lastUpdate filter to identify changes.

**Benefit**: Ensures that downstream systems always reflect the accurate channel names, numbers, and stream URLs without manual data entry.

### Bulk Endpoint Onboarding

**Challenge**: Provisioning a new building with hundreds of Set-Top Boxes requires tedious manual entry of MAC addresses and IPs into the administrative UI.

**Solution**: Use the connector's POST /endpoints capability to iterate through a CSV or database list of new hardware and programmatically register them as unprovisioned or active endpoints.

**Benefit**: Drastically reduces deployment time and eliminates human error during large-scale hardware rollouts.

### Multicast Stream Audit

**Challenge**: Administrators need to verify which multicast IP addresses and ports are currently in use to prevent network conflicts when planning new streams.

**Solution**: Retrieve all channels using GET /channels and filter/sort the results to extract a list of all assigned IP Address and port values.

**Benefit**: Prevents IP conflicts and stream collisions by providing a clear view of the currently utilized network resources.

## Technical Reference

### Prerequisites

- **SysAdmin Credentials** are needed for creating new channels and endpoints, as the POST methods for these resources are explicitly restricted to users with System Administrator privileges.
