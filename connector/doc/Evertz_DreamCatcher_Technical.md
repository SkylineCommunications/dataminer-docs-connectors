---
uid: Connector_help_Evertz_DreamCatcher_Technical
---

# Evertz DreamCatcher

## About

Evertz DreamCatcher is a scheduling system for generating "growing files". This system has four main components:

- **Schedules**: The top-level metadata that hold references to one or more events.
- **Events**: The entities actually doing work in the system.
- **Tasks**: The activities to perform during an event.
- **Resources**: Abstractions of the many different entities in the system that can be operated upon.

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

To start polling device data, go to the **General** page of the element and specify the **Username** and **Version**.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

Once the credentials have been configured as detailed above, the element will show the necessary data in its tables, and you will be able to create schedules or tasks.

To **create a schedule**:

1. Go to the **Schedules** page and click the **Create Schedule** page button.

1. In the pop-up window, fill in the schedule name, start time, and end time, and also add the events that are associated with the schedule.

1. When all the necessary information has been filled in, click the **Create Schedule** button.

   The connector will then execute the command, and the new schedule will be added in the Schedules table.

To **create a task**:

1. Go to the **Tasks** page and click the **Create Task** page button.

1. In the pop-up window, fill in the necessary parameters and click the **Create Task** button.

   The new task will then be added in the Tasks table.
