---
uid: Connector_help_Skyline_Booking_Monitoring
---

# Skyline Booking Monitoring

## About

This a virtual connector that allows the SRM framework to report the status of bookings to produce alarm and trend data over the booking data.

This connector is meant to be installed together with the Skyline Booking Manager connector in SRM 1.2.14 or higher.

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

## How to use

This connector is part of the **SRM** framework.

To use this connector properly, open the **Skyline Booking Manager** and configure the following settings:

- **Bookings Monitoring Element**: The name of the Skyline Bookings Monitoring element.

- **Bookings Monitoring Mode**: Set this to one of the following states:

  - **None**: No bookings will be reported
  - **Non-Nominal**: All failed, quarantined, and interrupted bookings will be reported to the configured element.
  - **All Bookings**: All configured bookings will be reported.

## General Page

This page contains a table listing all monitored bookings.

The connector will monitor bookings that are running, bookings in a non-nominal state, and past bookings.

Two buttons are available that allow you to **clear all bookings** or **clear all nominal bookings**, while keeping bookings with non-nominal states.

In addition, the **Refresh** button will refresh the Bookings Table based on the configuration.

## Configuration Page

Two parameters are available on this page:

- **Retention Time**: Duration for which a booking is kept in the table after the booking is finished.

- **Past Lookup Time**: Past time period for which the element actively looks for bookings that have not ended.

## Notes

This connector should **always be deployed as part of the SRM framework**. It is intended to work with a 1-on-1 mapping to a Skyline Booking Manager.
