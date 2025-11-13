---
uid: Connector_help_Nokia_Altiplano_Manager_Technical
---

# Nokia Altiplano Manager

## About

The **Nokia Altiplano Manager** connector enables virtualized communication between network elements within the **Altiplano Solution**, supporting both **Master** and **Slave** roles with configurable REST API and Kafka-based data exchange. Operating through a virtual connection, it provides a unified interface for monitoring, configuring, and executing network management tasks across key operational domains such as OLT inventory, API scheduling, Kafka job tracking, and InterApp messaging.

In **Master** mode, the connector actively manages API requests and Kafka streams, initiates InterApp communications, and oversees inventory and operational data processing. This role enables full orchestration capabilities within the Altiplano Solution, allowing the element to coordinate data exchange and system behavior across multiple domains.

When operating in **Slave** mode, the connector passively receives InterApp messages from its designated *Master* element, ensuring synchronized data flow and operational consistency. The received data is then routed through the OLTs configured within the Slave element, enabling seamless downstream integration without initiating independent processes.

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

When you create an element using this connector, you will have to define the working role of the element: **Master** or **Slave**.

#### Master Role Configuration

When the element is assigned the Master role, you can configure the following capabilities:

- **Kafka Streams**: Enable or disable the Kafka Streams selector, located in the **Operational Data** section of the **Configuration** page.
- **REST API Requests**: Enable or disable REST API functionality via the **Inventory API** section of the **Configuration** page. If the REST API parameter is enabled, you can activate specific API request types. If this parameter is disabled, all associated API parameters will remain in a *Not Configured* state.

#### Slave Role Configuration

When the element is assigned the Slave role, you must designate a corresponding Master element. This Master will serve as the source of InterApp messages received by the Slave element.

## How to Use

### Configuration Page

On this page, you will find the configuration options for **Kafka** and **API** requests, which may be executed and processed as required. Additionally, the interface includes a dedicated button that displays all Altiplano Managers currently configured with the operational role of Slave.

When manual initiation of API queries is required, you can use the **Execute API Requests**. This button initiates InterApp communication with the REST interface connectors to carry out the API requests, assuming the API request configuration is enabled.

### OLTs Page

This page presents a table listing all OLTs retrieved through the **REST API OLTs Inventory** request. The displayed data reflects the current set of OLTs available within the Altiplano Solution.

The page also includes two parameters that support automated and manual OLT management:

- **Last Discovery**: Displays the timestamp of the most recent execution of the automatic discovery process.
- **Automatic Discovery**: Enables or disables the automatic detection of OLT elements. When this is enabled, the system attempts to match OLT table entries with existing elements based on the OLT name. If a match is found, the Element ID column is populated with the element's ID. If no match is found, the column remains empty.

Additionally, the page provides an **Add OLT** button, allowing you to manually register new OLT entries in the table.

### Inventory Page

> [!NOTE]
> This page is only visible when the element is configured with the **Master** working role.

This page displays a table listing all API requests initiated (or scheduled) by the Master element. It also includes a set of operational parameters that you can configure as needed, including the following:

- **Max Simultaneous API Requests**: Specifies the maximum number of API requests that can be sent at a time.
- **Last API Table Update**: Displays the timestamp of the most recent update to the API Requests Inventory table, typically triggered by job completions, new entries, or data processing events.
- **Inventory Execution**: Defines the frequency at which the Master element executes the API processes.
- **Max API Jobs Recorded**: Indicates the maximum number of entries retained in the API Requests Inventory table; older records are automatically removed once this threshold is reached.

The page also includes the **Altiplano API Senders** page button, which shows all active **Altiplano REST Interfaces** elements configured to receive InterApp requests from the **Altiplano Manager** Master element.

### Operative

> [!NOTE]
> This page is only visible when the element is configured with the **Master** working role.

This page displays a table listing all Kafka files received from the Generic Kafka Consumer elements. It also includes a set of operational parameters that you can configure as needed, including the following:

- **Last Kafka Jobs Update**: Displays the timestamp of the most recent update to the Kafka Jobs, typically triggered by job completions, new entries, or jobs processing events.
- **Max Kafka Jobs Recorded**: Indicates the maximum number of entries retained in the API Requests Inventory table; older records are automatically removed once this threshold is reached.
- **Max Simultaneous Jobs**: Specifies the maximum number of Kafka jobs that can be processed at a time.

The page also includes the **Altiplano Kafka Analyzers** page button, which shows all active **Generic Kafka Consumer** elements configured to retrieve Kafka information from the **Altiplano Manager** Master element.

### InterApp Messages

This page provides visibility into the InterApp communication activity of the element. The displayed elements are:

- **Last InterApp Message**: Indicates the timestamp of the most recent update to either the Inbound or Outbound table.
- **Max InterApp Messages Recorded**: Defines the maximum number of records to retain in each table. Once the limit is reached, older entries are automatically removed.
- **Inbound Table**: Displays messages received by the element via InterApp.
- **Outbound Table**: Displays messages sent by the element via InterApp.
