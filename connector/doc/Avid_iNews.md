---
uid: Connector_help_Avid_iNews
---

# Avid iNews

This connector monitors input booking details associated with the **Avid iNews**. It retrieves these entries from iNews, processes them, and displays them in a table in DataMiner. These entries are then used to create bookings in the system.

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The address of the host that is hosting the Avid iNews service.
- **IP port**: The port on which the Avid iNews service is listening.
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy.*

### Initialization

When a new element is created, the **username, password, and server name** of the Avid iNews should be entered on the **General** page. These credentials are necessary for a successful connection and communication during sessions.

## Usage

This connector presents the booking details on two different data display pages on the element card.

### General

This page contains information about the system:

- **Server**: iNews server name.
- **User Name**: User name of the iNews user.
- **Password**: Password that is necessary for a successful login.

### Bookings

This page contains all the bookings that have been made during a period of time determined by the user (default: last 7 days):

- **Days to Retrieve**: The time period for which the bookings are listed in the table.
- **Booking Table**: Table containing the necessary information about each individual booking from this time period.
- **Booking Table Row Max Count**: Maximum number of rows displayed in the table (default: 500 rows).

### Historical Bookings

This page contains all the bookings for a selected date:

- **Date of the Booking**: Date for which the bookings should be listed.
- **Historical Booking**: Table containing the bookings for the selected date.
