---
uid: Connector_help_Tektronix_Sentry
---

# Tektronix Sentry

The **Tektronix Sentry** connector will display information related to the **Sentry** device.

## About

The **Tektronix Sentry** connector will display information related to the selected **Sentry** device. This information and details, such as Ports, Transport and Services, are available on different pages, described in the "Usage" section of this document. Alarm monitoring and trending are possible for some of the parameters in the connector, e.g. the **bitrate**.

**Note: This connector requires the .Net Framework 4.0.**

## Key Features

- **Device Information**: Quickly see details about your Sentry device.
- **Monitoring**: Track important parameters, such as bitrate, and receive alerts if something needs your attention.
- **Trends**: Observe how certain values change over time to help with troubleshooting and planning.
- **SNMP traps**: Listens for automatic updates when events occur.

## Use Cases

### Use Case 1
**Challenge:** Operators need to ensure that the bitrate of services remains stable to maintain broadcast quality among multiple Sentries. Unexpected drops can go unnoticed until they impact viewers.
**Solution:** The Tektronix Sentry connector continuously monitors bitrate values and triggers alarms when values fall outside predefined thresholds.
**Benefit:** Issues are detected early, allowing for quick intervention before service quality is affected.

### Use Case 2
**Challenge:** When a service interruption occurs, it can be difficult to pinpoint the root cause without detailed device data.
**Solution:** The connector provides access to historical trends and alarm logs, making it easier to trace back to the moment and cause of the interruption.
**Benefit:** Troubleshooting is faster and more effective, reducing downtime and improving service reliability.

### Use Case 3
**Challenge:** Important device events may be missed if operators rely solely on manual checks or periodic polling.
**Solution:** The connector listens for SNMP traps, providing automatic notifications when significant events occur.
**Benefit:** Operators are immediately informed of critical changes, enabling rapid responses to potential issues.