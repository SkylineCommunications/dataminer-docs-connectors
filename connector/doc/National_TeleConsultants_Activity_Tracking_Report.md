---
uid: Connector_help_National_TeleConsultants_Activity_Tracking_Report
---

# National TeleConsultants Activity Tracking Report

## About

This connector retrieves information from the database about the actions performed by users on the current alarms, and generates **manual** or **automated** reports according to some configurable parameters. In order to correctly schedule the automated **reports**, an automation script has to be created (can be downloaded along with the connector).

The connector uses SLNet calls to run an SQL query with configurable parameters that either outputs as a table that can be exported to a .CSV file or to a .CSV directly via an automation script. The connector allows you to configure the list of DMAs that will be monitored (in case of a cluster) and the list of users and actions that will be included in the report.

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range   | Supported Firmware                    |
|---------|---------------------------------------|
| 1.0.0.x | DataMiner DB schema for version 8.5.x |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | No                      | -                     | -                       |

## Installation and configuration

### Creation

There is no need of any kind of special configuration while creating the element. The connection information and other miscellaneous params will be provided later.

### Configuration

The minimum information necessary to run any report is the list of DMAs to be monitored. This is located in the **Configuration** page. You can add the IDs of the DMAs and optionally a description. The particular report parameters such as actions/users to be considered and start and end dates can be configured on the pages **Manual** and **Automated Report** (see below).

## Usage

### Manual Report

This page allows you to generate a report **on demand** and export it to .CSV. You will need to input the start and end date of the report and (optionally) the actions and users to be searched. If you leave the latter blank, all users or actions will be queried. To add a new entry to users and actions tables, right-click them an select the add action. The results will be displayed on the **Manual Report Results** page (so you can see the table full-width). If you want to export the results, the **Report File Name** parameter should be filled in with a valid location.

### Manual Report Results

This page shows the results of a manually generated report. You can also see the problems (if any) during the generation.

### Automated Report

This page allows you to schedule a new report. Since **its execution is periodic**, there is no a fixed end date, but a placeholder instead and a timespan calculated from that placeholder. You can also choose if the timespan is measured in days or hours. You can customize the configuration parameters of the scheduled task that will be created (which you can edit at any time in the **Automation** module). Note that the automation script included with the protocol is installed first, and its name matches with the one provided by the user on this page. The output reports will be created according to the **Automated Report Location** path set on the **Configuration** page.

### Configuration

This page allows you to configure the DMAs to be monitored and the location of the files corresponding to the automated reports.

### Queue

This page shows the queue of pending reports to be generated. You can delete reports from the queue.

## Notes

The **automated reports** are created at the path set on the **Configuration** page using the prefix *automatic_report\_* and the time of execution. Watch the log files for potential problems periodically.
