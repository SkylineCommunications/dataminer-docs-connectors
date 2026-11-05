---
uid: Connector_help_Skyline_SmartRec_Application
---

# Skyline SmartRec Application

This connector works in combination with the **Ericsson RedBee EPG**, **Witbe Robot** and **WitBe Robot Manager** connectors. The goal is to **monitor** the **replay/startover functionality** of **set-top boxes**. The connector **manages** which **assets/programs** need to be tested and also **aggregates** the **test results**.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x [Obsolete] | Initial version | - | - |
| 2.0.0.x [Obsolete] | DVE elements for each channel | 1.0.0.12 | - |
| 2.0.1.x [SLC Main] | Split in separate elements for each platform | 2.0.0.17 | - Recreation of element is required<br>- Loss of all trend data |

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|--|--|--|--|--|
| 2.0.1.x | No | Yes | - Ericsson RedBee EPG<br>- WitBe Robot Manager<br>- WitBe Robot<br>- Ziggo Set Reservation Color | Skyline SmartRec Application - Channel |

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

A **channel number** needs to be set for each entry in the **Channel Status table**.

The **script** to be run by the WitBe robot needs to be configured via the **StartOver Configuration** and **Replay Configuration** parameters on the **Configuration page**.

### Redundancy

There is no redundancy defined.

## How to use

The **Channel Status** **page** shows the monitored channels for which tests are managed. You can remove the child DVE element by pressing the delete button; however, this is only possible when the channel is no longer monitored.

The **EPG Bookings table** contains a list of all program broadcasts that are in the resource manager. Programs in this table will be sent to the WitBe Robots for testing. The WitBe Robot Manager will handle the distribution of these program test campaigns. The aggregated result of all performed tests is shown in the **Program Status Column**.

The **Configuration page** is used to configure various aspects of the tests and the connector:

- Ignoring of startover tests that are performed too close to the end of the program.
- Configuration of the minimum number of test results required to aggregate the result.
- Configuration of test scripts to be used by WitBe robots.
- Enabling or disabling debug logging.
- Sending test results to the staging environment.

The **Ignored Assets pop-up page** allows you to create filters to ignore test results of certain programs.

The color of programs in the resource manager will be set to the color of the alarm of the **Program Status** in the **EPG Bookings table**.

The **EPG Result table** shows whether a program has already been tested.

The **StartOver Tests table** contains the aggregated results of all startover tests on a program. Startover tests are performed on programs that are currently airing. If the status is ***pending***, this means that there are not enough test results yet to show an aggregated result.

The **Replay Tests table** is similar, but contains results for replay tests. Replay tests are performed on programs that have finished broadcasting.

The **Robot Test page** contains data about all individual test results received from the **WitBeRobots**.

The **StartOver Channel Issues page** shows if many sequential programs are failing. This provides information as to the root cause of the issue that is causing the programs to fail.

The **Daily Aggregation page** provides an overview of the kind of issues that have occurred each day.

The **Weekly Aggregation page** provides an overview of the kind of issues that have occurred over a week.

This connector will export the Skyline SmartRec Application - Channel connector. An element will be created automatically for each monitored channel in the resource manager.

## Notes

Temporarily unassign all alarm templates when you start, stop or restart the element or its exported elements.
