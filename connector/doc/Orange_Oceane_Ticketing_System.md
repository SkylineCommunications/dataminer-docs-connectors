---
uid: Connector_help_Orange_Oceane_Ticketing_System
---

# Orange Oceane Ticketing System

## About

The Orange Oceane Ticketing System connector is a tool that bridges DataMiner alarms with the Orange Oceane Ticketing System, enabling efficient incident management. This connector transforms how you handle alarms by converting them into actionable tickets with minimal effort.

### Key Features

- **Efficient ticket creation:** Easily generate tickets from DataMiner alarms, eliminating time-consuming processes and ensuring no incident goes unnoticed.
- **Customizable ticket fields:** Tailor ticket details to your organization's needs, including priority, urgency, technical impact, client impact, description, and more.
- **Real-time status updates:** Instantly track ticket creation status and monitor for successes or failures.
- **Robust error handling:** Detailed error reporting for failed ticket creation ensures quick resolution of issues.
- **Advanced debugging:** Enable the debug page to monitor ticket queues and troubleshoot issues.

### Use Case: Streamlined Incident Management

- **Challenge**: Incidents need to be quickly tracked and resolved.

- **Solution**: This connector integrates DataMiner with the Orange Oceane Ticketing System, allowing quick and efficient management of tickets based on alarms.

- **Benefit**: When an alarm, such as a network failure or system error, is triggered in DataMiner, you will easily be able to create a ticket via the Alarm Console right-click menu, with all the essential details such as the priority, urgency, and impact. A corresponding ticket will then be generated in the Orange Oceane Ticketing System, enabling the incident management team to respond swiftly, track the issue, and resolve it efficiently, minimizing downtime and ensuring operational continuity.

### Technical Reference

#### Prerequisites

- **Automation script deployment:** The Orange Oceane Ticketing System automation script must be installed and configured in DataMiner.
- **Hyperlinks setup:** Hyperlinks must be set up properly to extend the Alarm Console with the "Create Ticket" and "Go to Ticket" options.
- **Orange Oceane Ticketing System access:** API credentials (Client ID and Client Secret) are required for system authentication. Additionally, DataMiner usernames with ticket creation permissions must be mapped to their corresponding Oceane User IDs, which the automation script uses when creating tickets.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation page](xref:Connector_help_Orange_Oceane_Ticketing_System_Technical).

