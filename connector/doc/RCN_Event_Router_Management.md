---
uid: Connector_help_RCN_Event_Router_Management
---

# RCN Event Router Management

This is a router management system connector that checks all events from the user database, displays them in the connector, and creates the appropriate scheduled tasks that will execute the script to switch the crosspoints on the routers.

The key objectives of the connector are to collect all relevant events and switch appropriate crosspoints on defined routers. The whole process can be monitored.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

Before you start using the element, on the **Database Configuration** page, fill in the following database credentials: **Server Address**, **Port**, **User Name**, and **Password**.

## How to Use

### Events Page

After you have correctly initialized the connector as described above, you will find all daily events on the Events page.

Events can be in following states:

- *Pending*: A scheduled task has been created.

- *Running*: The script has been executed, and the crosspoint has successfully been set.

- *Completed*: The script has been executed, and the router has switched to CBG.

- *Failed To Run*: The script has been executed, but the set on the router failed.

- *Failed Switch To CBG*: The script has been executed, but the switch to CBG on the router failed.

The Events page also has several subpages:

- **Weekly Events**: Contains a table listing all events for the next 7 days.
- **Completed Events**: Contains a table listing all completed events.
- **Logging**: Displays the logging for manual actions from the element or a message with more information about why a switch failed.

Dates and times in the Daily Events, Weekly Events, and Completed Events tables are stored as they were retrieved from the database. However, note that the time has a difference of 3 hours with the server time. The database use Eastern time, while the server use Pacific time.

### General Page

The General page lists all customers with the configuration of the router element related to that customer.

You can specify the destination, source, and CBG ports.

### Database Configuration

The Database Configuration page contains the parameters required to establish a connection with the database (see [Initialization](#initialization)).
