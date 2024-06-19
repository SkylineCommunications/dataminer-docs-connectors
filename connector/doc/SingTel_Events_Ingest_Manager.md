---
uid: Connector_help_SingTel_Events_Ingest_Manager
---

# SingTel Events Ingest Manager

This connector is used by Singtel to import booking events from the excel file. Once the booking events are imported, SRM booking will be created for each imported bookings.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version. | -            | -                 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

No extra configuration is needed.

### Redundancy

There is no redundancy defined.

## How to use

To use the **Excel import** function, the **Excel File Path** needs to be configured under the **General** page. Use **Local** import mode for a local directory and use **Remote** import mode for a shared folder directory.

**General Page** 

This page includes parameters to configure the file import, including the **Username**, **Password**, and a list of the available Excel files in the directory.

**Booking Events Page**

This page displays a table that contains all the imported booking events, as well as the events that come from the **ForeTV Event Manager** element. If an SRM booking fails to be created for a booking event, the **Recreate** button will be available, allowing the user to edit or recreate bookings through the booking wizard window. SRM bookings will only update automatically when there is a change in the existing booking event.

**Import File Page**

This page contains parameters to display the status of the file import. It also has configurable parameters to set the **Import Interval** and the **Time of Day** to import. The **Import Now** button allows the user to import the file without waiting for the interval. This page also contains a subpage that allows the user to manually import a file by providing the full path of the file.

**Setting Page**

This page contains parameters to configure the **Auto-Cleanup** rule of the Booking Events table. It also contains parameters to configure the **Email Address** to which an email will be sent after the booking events are imported. The **Mandatory Fields** table allows the user to specify the mandatory fields of the Booking Events table.
