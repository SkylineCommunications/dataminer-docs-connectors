---
uid: Connector_help_RCN_Event_Router_Management
---

# RCN Event Router Management

This is a router management system connector that checks all events from the user database, displays them in the connector, and creates the appropriate scheduler tasks that will execute the script to switch the crosspoints on the routers.

The key objectives of the connector is to collect all relevant events and switch appropriate crospoints on defined routers. The whole process is being monitored.

## About

### Version Info

| Range            | Key Features | Based on | System Impact |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version. | -            | -                 |

### Product Info

| Range | Supported Firmware |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

User need to fill database credentials on DataBase Configuration page before any actions.
Database credentials: Server Address, Port, User Name, Password.

## How to use

After you have correctly initialized the connector as described above, you will find all daily events on **Events page**.

Events can be in following states:

              1)Pending - Scheduler task is created.
  
              2)Running - Script is executed and crosspoint is set successfully.
  
              3)Completeed - Script is executed and router is switch to CBG.
              
              4)Failed To Run - Script is executed but set on router failed.
              
              5)Failed Swtich To CBG - Script is executed but switch to CBG on router failed.
  

Events page has Weekly Events, Completed Events and Logging subpages.

**Weekly Events** subpage contains Weekly Events table which displays all events for next 7 days.
**Completed Events** subpage displays all completed events in Completed Events table.
On **Logging** subpage user can found all logging about manual actions from element or message which will give a more context why switch failed.

On **General** page user can see listed all customers with configuration of related router element to that customer. User can specify destination, source and CBG ports.

**Database Configuration** contains all necessary data to establish a connection with the user's database.

## Notes

Dates and Times in Daily Events, Weekly Events and Completed events tables are stored like we get it from database. However, that time has difference with server time with offset of 3 hours.
Database use Eastern time, server use Pacific time.
