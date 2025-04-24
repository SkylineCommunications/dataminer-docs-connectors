---
uid: Connector_help_Evertz_DreamCatcher_Technical
---

# Evertz DreamCatcher

Evertz DreamCatcher is a scheduling system for generating “growing files”. This system has 4 main components: Schedules, Events, Tasks, and Resources.

- Schedules are the top level metadata that holds reference to one or many Events. 
- Events are the entities actually doing work in the system.
- Task are the activities to perform during the event.
- Resources are abstractions of many different entities in the system that can be operated upon.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial version</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |2.9.2.r1.588         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### Serial Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:


- Direct connection:

  - **Baudrate**: Baudrate specified in the manual of the device, e.g. *9600*.
  - **Databits**: Databits specified in the manual of the device, e.g. *7*.
  - **Stopbits**: Stopbits specified in the manual of the device, e.g. *1*.
  - **Parity**: Parity specified in the manual of the device, e.g. *No*.
  - **FlowControl**: FlowControl specified in the manual of the device, e.g. *No*.

### Initialization

To start polling device data, the user must need to set the Username and Version. Those parameters are placed on General page.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

To retrieve data, we need to configure the credentials on main page. After configure those parameters, the user will show all tables with the desire data.

- To create a Schedule, the user needs to go to Schedules page and click on **Create Schedule** pagebutton. On that popup window, the user needs to fill in all the information (schedule name, start and end time) and also add the events that are associated to the schedule. After fill in all the information, the user must click the **Create Schedule** button and the connector will execute the command. After click the button, the user will see the Schedule created on Schedules table.
- To create a Task, the user needs to go to Tasks page and click on **Create Task** pagebutton. On that popup window, the user must need to fill in all the parameters and click on **Create Task** button. After click the button, the user will see the task created on Tasks table.
