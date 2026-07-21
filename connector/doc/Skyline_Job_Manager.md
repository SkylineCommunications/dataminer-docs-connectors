---
uid: Connector_help_Skyline_Job_Manager
---

# Skyline Job Manager

## About

This connector exposes a REST API that can be used to manage jobs and distribute them to operational domains (DataMiner SRM applications). In this context, the Skyline Job Manager connector works as an intermediary between third-party applications and the SRM Booking module.

A DataMiner job is a domain-specific description to set up SRM services. DataMiner Domain Orchestrators will be able to convert a DataMiner job into one or multiple DataMiner bookings. Whereas a job is an administrative description of a service that needs to be set up, a DataMiner booking is a detailed definition of the service, the configuration profiles and parameters, the exact resources to be used, the detailed schedule, etc.

The purpose of this connector is to manage and store a collection of jobs. Jobs can be ingested via a REST API that is hosted by a Job Manager element. When possible, jobs are distributed to one or multiple network domains (virtual platforms), which then convert the jobs into full service bookings. Typically, automation scripts are used to perform the complex operation of converting a job into a booking.

![Visual Overview](~/connector/images/Skyline_Job_Manager_Visual_Overview.png)

## Key Features

- **REST API**: Exposes a REST API that allows users and third-party applications to push and retrieve DataMiner jobs to/from the DataMiner System.
- **Domain-specific**: Enables users to specify jobs per domain.
- **Multi-service**: Allows a job to be divided into multiple SRM services.

## Use Case

- **Challenge**: Although DataMiner offers ways to manage jobs and scheduled events, many partners use dedicated applications to manage jobs outside of the DataMiner ecosystem.
- **Solution**: This connector acts as an intermediary between third-party applications and the SRM Booking module, enabling easy integration of job/event management applications with DataMiner's SRM framework by translating jobs/events into services and managing their lifecycle.
- **Benefit**: You get a fully integrated ecosystem that manages and monitors the lifecycle of your jobs, events, and services.

## Technical info

### Prerequisites

- **DataMiner version 10.3 or higher** is required for compatibility with the Skyline Job Manager connector.
- The **DataMiner SRM package** is required for converting a DataMiner job to an SRM service.

> [!NOTE]
> For in-depth information on configuring and using the Skyline Job Manager connector, refer to the [Technical help page](xref:Connector_help_Skyline_Job_Manager_Technical).
