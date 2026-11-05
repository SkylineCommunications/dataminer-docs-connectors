---
uid: Connector_help_Appear_X_Platform
---

# Appear X Platform

The Appear X Platform connector allows users to configure and display information from the Appear X10/X20 chassis and its associated module cards.

> [!NOTE]
>
> - This connector is the successor of the **[AppearTV X20 platform](https://catalog.dataminer.services/details/7bb327a7-0844-4c2b-b5bc-fbfd4e3bc8de)** connector, which will be gradually phased out and will eventually become deprecated. For new greenfield deployments, we strongly recommend using this **Appear X platform** connector instead.
> - On the U.S. market, the same chassis is also offered under the Sencore brand, with the following model names: **Sencore DMG-3200** (X10 chassis), **Sencore DMG-4100**, and **Sencore DMG-4200** (X20 chassis).

## Key Features

- **Real-time module status**: View connected modules with real-time health information, emphasizing key metrics for quick insights and diagnostics.
- **Essential device information access**: Quickly access configuration settings, ensuring efficient module management.
- **Detailed network configuration**: Configure IP settings, network masks, and gateway parameters to ensure smooth network connectivity across the chassis.
- **Scalable integration**: Supports up to 14 modules within one chassis, offering flexible scalability and adaptation for expanding system demands.

> [!NOTE]
> The complete list of supported modules and additional technical details are available on the [Technical help page](xref:Connector_help_Appear_X_Platform_Technical).

## Use Cases

### Data Insights

**Challenge:** Monitor traffic rates and alarms from one central place with customized thresholds and filters.

**Solution:** The **Appear X Platform** connector comes with pre-defined alarm and trending templates, allowing you to monitor the entire chassis with a few clicks. From System metrics such as uptime, to TS- or PID-level bitrate monitoring, anything is possible.

**Benefit:** Achieve **better system oversight** and targeted management of alarms, reducing complexity and enhancing operational efficiency.

![Visual Overview](~/connector/images/Appear_X_Visual_Overview.png)

> [!TIP]
> By using the integrated **Polling Manager Table**, you can speed up the the most important polling parameters for your use case.

### Predicting Upcoming Sun Outages on Satellite Demodulators

**Challenge:** Sun outages for earth stations receiving from geostationary earth orbit (GEO) satellites happen during the equinox seasons (February–March and September–October) for a period of around two weeks, when the sun passes through the equatorial plane, which is used by the GEO satellites. During these periods, the sun is directly behind the satellite as seen from the receiving earth station, causing a disturbance.

**Solution:** The **Link Margin** status on affected demodulators will start to deviate from the expected range. By means of alarm thresholds configured for this connector, a critical alarm can be raised **before** the outage happens.

**Benefit:** Predict outages by means of the connector status monitoring.

## Technical info

### Prerequisites

- **DataMiner version 10.3.9 or higher** is required for compatibility with the Appear X Platform connector.
- **Administrator permissions** are needed to configure each module through the connector.
- **Network access** to the Appear X chassis is essential, including IP address and UDP port (default: 443).

> [!NOTE]
> For in-depth information on configuring and using the DataMiner connector to connect to the chassis, refer to the [Technical help page](xref:Connector_help_Appear_X_Platform_Technical).

