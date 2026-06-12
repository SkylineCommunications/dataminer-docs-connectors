---
uid: Connector_help_Slack_Messaging
---

# Slack Messaging

## About

Slack is a cloud-based team messaging and collaboration platform widely used for real-time communication across organizations. This connector can be used to integrate DataMiner with a **Slack workspace**. It will communicate with Slack and ensure that the configured list of actions is executed. In order to keep this connector as general as possible, these actions are defined in **automation scripts**.

When commands are sent into a Slack channel, these will be picked up by the element running this connector. When the element detects a known command, it will execute the automation script linked to that command.

> [!WARNING]
> Only versions 1.1.0.X and above are fully supported by Slack due to the deprecation of legacy bots and classic apps. You can read more about it [here](https://docs.slack.dev/changelog/2024-09-legacy-custom-bots-classic-apps-deprecation/).

## Key Features

- **Slack DataMiner integration**: Allows for DataMiner to interact with Slack, enabling users to execute DataMiner automation scripts directly from Slack channels.
- **Automated Slack messages**: Enables DataMiner to send messages to Slack channels or users based on certain events or conditions defined in automation scripts.
- **Activate Automation Scripts in Slack**: Allows users in Slack to activate automation scripts specially designed for this integration.

## Use Cases

### Receive Real-Time Notifications in Slack from DataMiner

![Slack Messaging Alarms in Slack](~/connector/images/Slack_Messaging_AlarmsInSlack.png)


**Challenge**: Operators want to receive real-time notifications in Slack when certain events occur in DataMiner, such as alarms or performance thresholds being breached.

**Solution**: Use the Slack Messaging connector to send automated messages to a designated Slack channel whenever specific conditions are met in DataMiner.

**Benefit**: Improves responsiveness and collaboration by ensuring that relevant team members are immediately informed of critical events through their existing communication platform.

### Trigger DataMiner Automation Scripts from Slack Commands

**Challenge**: Users want to execute DataMiner automation scripts without leaving their Slack workspace.

**Solution**: Use the Slack Messaging connector to allow users to trigger DataMiner automation scripts by sending specific commands in Slack channels.

**Benefit**: Enhances productivity and streamlines workflows by enabling users to interact with DataMiner directly from Slack, reducing the need to switch between applications.

### Track and Update Previously Sent Messages in Slack 

**Challenge**: Operators need to update status messages or notification in Slack as situations evolve rather than sending new messages that clutter the slack channels.

**Solution**: Use the Slack Messaging connector's Tracked Messages table to tag sent messages and later update them with new information. 

**Benefit**: Keeps Slack channels organized and reduces notifiation fatigue.

## Technical Reference

### Prerequisites 

- **A Slack Account** is needed for access to Slack in general.

- **A Slack Workspace** which your account has full access to is needed to define where your Slack App will be located in.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Slack_Messaging_technical).
