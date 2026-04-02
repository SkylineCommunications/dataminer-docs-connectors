---
uid: Connector_help_SES_Event_Manager
---

# SES Event Manager

## About

The SES Event Manager connector automates event and ticket management for SES satellite operations within the DataMiner environment. It continuously monitors active alarms across your DataMiner elements and transforms them into actionable events. It automatically creates, updates, and resolves tickets through the DataMiner Ticketing module, ensuring that no critical event goes untracked.

By bridging the gap between alarm monitoring and ticket management, this connector provides operations teams with a unified workflow for handling incidents from detection to resolution.

## Key Features

- **Automated event detection and tracking**: The connector polls active alarms at configurable intervals and processes them into structured events. Each event captures essential metadata such as severity, source element, and associated services, giving your team immediate visibility into operational issues.

- **Intelligent ticket management**: Events are automatically evaluated and escalated into tickets based on configurable rules. The connector handles the complete ticket lifecycle, including creation, status updates, and automatic resolution when underlying alarms clear.

- **Ticket follow-up handling**: When an event clears before a ticket has been created, the connector intelligently handles the follow-up process, ensuring that transient issues are still tracked and documented according to your operational policies.

- **Custom automation rules**: Define custom ticket automation rules that trigger DataMiner automation scripts when new events are detected. This allows you to tailor the event-to-ticket workflow to match your organization's specific processes.

- **Support NOC assignment**: Manage multiple Support Network Operations Centers and configure default ticket assignment rules. Ensure tickets are routed to the right team from the moment they are created.

- **Automated cleanup**: Configure retention policies to automatically clean up resolved events and error logs. Choose between count-based or duration-based cleanup methods to keep your system performant.

## Use Cases

- **Satellite Operations Centers** looking to automate incident management workflows.
- **Multi-site NOC environments** that require centralized event-to-ticket correlation.
- **Organizations** seeking to reduce mean time to resolution (MTTR) through automated ticket creation and escalation.

## Prerequisites

- This connector requires **DataMiner 10.5.0** or higher.
- **DOM** is required for creating and managing DOM definitions and instances.
- The DOM-based **Ticketing module** is required for ticket creation, updates, and resolution.

## Technical Reference

For detailed technical information, including connection configuration and advanced setup instructions, refer to the [technical page](xref:Connector_help_SES_Event_Manager_Technical).
