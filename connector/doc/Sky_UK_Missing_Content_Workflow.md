---
uid: Connector_help_Sky_UK_Missing_Content_Workflow
---

# Sky UK Missing Content Workflow

This connector is used by enhanced services that contain elements of the protocol [Sky UK VICC](xref:Connector_help_Sky_UK_VICC). With this connector, alarms are generated according to predefined rules.

## About

To use this connector, create a service that uses it as the service definition, add the necessary element and select the parameters mentioned below. It will check the current and future events for missing content and raise alarms per individual video item for video content, per screen graphic ID for logo content and per event ID for others.

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Installation and configuration

### Creation

#### Service Main Connection

This connector uses a service connection and requires the following input during element creation:

SERVICE CONNECTION:

Elements/Parameters:

- [Sky UK VICC](xref:Connector_help_Sky_UK_VICC)

  - **Channel From User**
  - **Data Update Trigger**

### Configuration of Elements

In this page you need to select what elements you want to include in this service.

This service needs the VICC element for the target channel intended to monitor .

## Usage

### Alarms

This page displays the **Early Warning List Table** with a unique row for each alarm scenario.

### Device Data

For this workflow, current and future events are grouped differently for each alarm type.

**Video Content Missing**: For this table, events are grouped by **Video Item**, if video content is missing, the first occurrence is mentioned by **Event ID** and **Event Time**.

**Logo Content Missing**: For this table, events are grouped by the **On Screen Graphic ID**, if logo content is missing, the first occurrence is mentioned by **Event ID** and **Event Time**.

**VICC Update** is the date and time of the latest update trigger received from the **VICC** element.

**VICC DMA-Elem ID** is the identifier for the subscribed **VICC** element for use elsewhere in the connector.

**Channel Bus** is the **Channel From User** value from the **VICC** to populate the **Channel** column in the **Early Warning List Table**.

**BSS Service Status**: when this is Off-Air, this workflow won't trigger any alarms, for other values (NA or On-Air) or if the parameter isn't subscribed, the workflow will run as expected.

### Subscriptions Active

This shows the **Subscription Table** where you can find detailed information regarding each subscription made under this service. For each subscription (row), the following information is present:

- **SourceKey [IDX]**: String key identifying each subscription. Consists of the "DataMiner ID / Element ID / Parameter ID : Row Key Filter" of the subscribed parameter.

- **Parameter Value**: The value of the subscribed parameter.

- **DataMiner ID**: The DataMiner ID of the Agent running the subscribed parameter.

- **Element ID**: The element ID of the element containing the subscribed parameter.

- **Parameter ID**: The parameter ID of the subscribed parameter.

- **Row Key Filter**: The row key filter used to selected a specific row from the table in order to subscribe to a cell parameter.

   > [!NOTE]
   > The row key filter is only needed for a cell parameter. Otherwise, it is "NA".

- **Protocol Name**: The name of the connector used by the element containing the subscribed parameter.

### General Parameters

Table with subscribed parameters of the service.
