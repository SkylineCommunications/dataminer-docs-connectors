---
uid: Connector_help_Skyline_Booking_Manager
---

# Skyline Booking Manager

## About

The Skyline Booking Manager is a generic application that allows you to fully manage bookings with the SRM module.

### Version Info

| Range   | Description                                                                               | DCF Integration | Cassandra Compliant |
|---------|-------------------------------------------------------------------------------------------|-----------------|---------------------|
| 2.0.1.x | Initial version.                                                                          | No              | Yes                 |
| 2.0.2.x | Removed Booking Manager Tables. A visual overview is provided to enable CRUD of bookings. | No              | Yes                 |
| 2.0.3.x | Replaced QAction 63000 by NuGet packages. Compatible with SRM 2.0.X.                      | No              | Yes                 |

## Installation and configuration

### Creation

This connector uses a virtual connection and does not require any input during element creation.

## Usage

### General

The General page contains a complete set of configuration parameters, used to customize the Booking Wizard, the application itself, and the booking execution.

The General page has several subpages:

- **Events**: This page allows you to manage custom events to be added in future bookings.
- **Properties**: This page allows you to manage custom properties to be added in future bookings.
- **SLA Tracking**: Allows you to configure the SLA Tracking mode for every booking state.
- **States**: Allows you to configure the available states and state transitions.
- **State Colors**: Allows you to specify the UI colors for every booking status.
- **Booking Block Info**: Defines the different placeholders that can be used to fill the property "VisualBlockContent".
- **Custom Actions**: Allows to define up to five customizable buttons on the booking detail area of the Booking Manager.
