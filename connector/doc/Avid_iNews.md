---
uid: Connector_help_Avid_iNews
---

# Avid iNews

This connector monitors input booking details associated with the **Avid iNews**.

## About

This connector monitors input booking details, retrieves these entries from iNews, processes them, and displays them as a table within DataMiner. These entries are then used to create bookings in the system.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|------------------|-----------------|---------------------|-------------------------|
| 1.0.0.x          | Initial version | No                  | Yes                     |

## Installation and configuration

### Creation

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The address of the host that is hosting the Avid iNews service.
- **IP port**: The port on which the Avid iNews service is listening.
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy.*

### Initialization

When a new element is created, the **username, password and server name** of the Avid iNews should be entered on the **General** page. These credentials are necessary for a successful connection and communication during sessions.

## Usage

This connector presents the booking details in two different data display pages on the element card.

### General

This page contains information about the system:

- **Server**: Server name of the iNews.
- **User Name**: User name of the iNews user.
- **Password**: Password that is necessary for a successful login.

### Bookings

This page contains all of the bookings that have been made during the period of time that is determined by the user (default: last 7 days):

- **Days to Retrieve:** Time period for which the bookings are listed in the table.
- **Booking Table:** Booking table containing the necessary information about each individual booking from the said time period.
- **Booking Table Row Max Count:** Maximum number of rows diplayed in the table (default: 500 rows).

### Historical Bookings

This page contains all of the bookings for a certain date that is chosen by the user:

- **Date of the Booking:** Date for which the user wants to list the bookings.
- **Historical Booking:** Table that contains the bookings for the chosen date.