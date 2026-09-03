---
uid: Connector_help_Casa_Systems_C100G
---

# Casa Systems C100G

## About

The **Casa Systems C100G** connector provides comprehensive, real-time monitoring and control of the Casa Systems C100G Converged Cable Access Platform (CCAP) directly from DataMiner. It unifies the **data** (CMTS/DOCSIS) and **video** (edge QAM) sides of the platform in a single overview, so cable operators no longer need to switch between separate tools to keep their access network healthy.

Built on **SNMPv2**, the connector combines fast, high-frequency data collection with a dedicated virtual-polling thread for heavy data sets. This keeps RF spectrum measurements responsive while large tables (cable modems, channels, video sessions) are collected in the background without impacting performance.

## Key Benefits

- **Unified CCAP visibility**: Monitor DOCSIS downstream/upstream channels, cable-modem status, RF utilization and video delivery from one connector.

- **Built-in RF spectrum analysis**: Inspect upstream interfaces with an integrated spectrum analyzer to troubleshoot noise and signal-quality issues before they affect subscribers.

- **End-to-end video assurance**: Follow video QAM ports, channel statistics and per-session KPIs to guarantee a high-quality video experience across the edge-QAM side of the platform.

- **Proactive fault detection**: Use the Flap List to catch unstable cable modems early, and rely on alarming and trending on key KPIs to act before customers are impacted.

- **Optimized performance**: A separate virtual-polling thread offloads heavy table collection, ensuring spectrum measurements and interactive actions stay fast and responsive.

## Use Cases

### Converged CMTS and Cable-Modem Monitoring

The connector continuously collects the KPIs that matter for the data side of the platform: upstream and downstream channel performance, signal quality (SNR), channel utilization and the online/offline status of connected cable modems. This gives operations teams a live, end-to-end view of DOCSIS health across the entire chassis.

![Casa Systems C100G General Overview](~/connector/images/Casa_Systems_C100G_marketing_general.png)

### RF Spectrum Troubleshooting

Using the integrated spectrum analyzer, operators can visualize the RF spectrum of upstream interfaces to quickly pinpoint noise, ingress and signal-quality problems. Buffered relative and absolute traces keep the spectrum display responsive without overloading the device with repeated requests.

![Casa Systems C100G Spectrum Analyzer](~/connector/images/Casa_Systems_C100G_marketing_spectrum.png)

### Video Service Assurance

For the edge-QAM side of the platform, the connector surfaces video QAM port, channel and input-port statistics, together with detailed video-session KPIs such as bitrates and transport-stream health. This allows operators to assure video services and detect degradations before they reach subscribers.

![Casa Systems C100G Video Overview](~/connector/images/Casa_Systems_C100G_marketing_video.png)

### Detecting Unstable Cable Modems

The Flap List highlights problematic cable modems through flap hits, misses and related counters, helping field and NOC teams prioritize maintenance on the modems and plant segments that cause the most instability.

## Technical Reference

For detailed information on connections, configuration and per-range usage, see the [technical documentation](xref:Connector_help_Casa_Systems_C100G_Technical).
