# Orange Oceane Ticketing System Connector

## About

The Orange Oceane Ticketing System Connector is a tool that bridges DataMiner alarms with the Orange Oceane Ticketing System, enabling efficient incident management. This connector transforms how you handle alarms by converting them into actionable tickets with minimal effort.

### Key Features

- **Efficient Ticket Creation:** Easily generate tickets from DataMiner alarms, eliminating time-consuming processes and ensuring no incident goes unnoticed.
- **Customizable Ticket Fields:** Tailor ticket details to your organization's needs, including priority, urgency, technical impact, client impact, description and more.
- **Real-time Status Updates:** Instantly track ticket creation status and monitor for successes or failures.
- **Robust Error Handling:** Detailed error reporting for failed ticket creations ensures quick resolution of issues.
- **Advanced Debugging:** Enable the debug page to monitor ticket queues and troubleshoot issues.


### Use Case

- **Streamlined Incident Management:** When a alarm, such as a network failure or system error, is triggered in DataMiner, the user can right-click on the alarm and select "Create Ticket" from the menu. This action opens a dialog to input essential details like priority, urgency, and impact, which are then used to generate a ticket in the Orange Oceane Ticketing System. This enables the incident management team to respond swiftly, track the issue, and resolve it efficiently, minimizing downtime and ensuring operational continuity.

### Technical Reference

#### Prerequisites

- **Automation Script Deployment:** The Orange Oceane Ticketing System automation script must be installed and configured in DataMiner.
- **Hyperlinks Setup:**  Hyperlinks must be setup properly to extend the alarm console with the "Create Ticket" option.
- **Orange Oceane Ticketing System Access:** API credentials (Client ID, Client Secret, and User ID) are required for authentication to enable ticket creation within the Orange Oceane system.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation page](xref:Connector_help_Orange_Oceane_Ticketing_System_Technical).