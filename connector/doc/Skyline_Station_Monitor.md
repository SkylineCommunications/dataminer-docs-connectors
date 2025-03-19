---
uid: Connector_help_Skyline_Station_Monitor
---

# Skyline Station Monitor

The **Skyline Station Monitor** standardizes and simplifies the collection of data for monitoring transmitters and related equipment (tower lights, generators, transfer switches, etc.) across multiple stations/transmission sites. Utilizing real-time monitoring and automation, this connector serves as a mediation layer, gathering data from various collectors and storing it according to predefined parameters. This ensures consistent reporting and display in low-code apps and dashboards. Additionally, the collector supports the collection of non-standard (custom) parameters for stations that need to track data from elements that users might not have permission to access. It also provides the capability to define custom actions.

## Key Features

- Mediates common transmission parameters at regular intervals into standard parameters allowing for standardized reporting.
- Can be extended to monitor additional, custom values from specified elements for data aggregation beyond the standard complement of included parameters.
- Allows you to define a custom polling frequency for standard and custom parameters.
- Polls both the value and alarm state from the source element to allow for passthrough of existing alarm templates.
- Provides historical polling timestamps for analysis.
- Can help isolate users from source elements by only allowing access to the Station Monitor element.
- FCC Licensed Power calculations allow stations to monitor their compliance with transmission output power limitations and provide warnings if the power output exceeds FCC tolerances.

## Use Cases

### Standardized Monitoring of Multiple Transmission Sites

**Challenge**: Unless each transmission site has the exact same complement of equipment, groups that need to monitor multiple transmission sites find that each site needs to be treated as a one-off. This requires setting up custom alarming, custom trending, custom reporting, and custom dashboards for each site, which can be time-consuming and costly at scale.

**Solution**: The **Skyline Station Monitor** provides a way to collect commonly used monitoring and reporting values into a standard footprint.

**Benefit**: There are multiple benefits to this approach that can greatly reduce the admin overhead of managing a large number of sites. Some of these benefits include:

- Standardized alarm and trend templates.
- The ability to reuse reports and low-code apps across sites.
- Users can be provided access to targeted information about a site without getting full access to the source elements.

### FCC Reporting Requirements

**Challenge**: Stations have an obligation to report certain metrics to the FCC related to their transmission towers, including power outputs and tower light status.

**Solution**: By using the **Skyline Station Monitor**, this information is easy to collect in a standardized way.

**Benefit**: By standardizing the collection, monitoring, and trending of key metrics required by the FCC, report generation is a breeze and easy to implement across your entire organization, reducing time to deploy and the costs to manage changes needed down the road.

## Technical Information

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Skyline_Station_Monitor_Technical).
