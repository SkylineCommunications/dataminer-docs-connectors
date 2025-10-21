---
uid: Connector_help_Skyline_Health_Check_Manager
---

# Skyline Health Check Manager

DMA systems have some resources like Disk Space, Memory Management, Boot Time, and more, that require systematic checks to ensure that the system has no ongoing issues and its performance is not affected.

Skyline Health Check Manager helps with these checks, with features to schedule subscription- and script-based tests on system and element parameters.

## About

Skyline Health Check Manager helps users with system checks of resources in a single window pane, with predefined threshold, element, and index filtering. It includes the following features:

- Map standalone and table column parameters of any protocol and any protocol version to a subscription.
- Add, edit, or delete tests based on Automation scripts or subscriptions, which need to meet certain thresholds based on a set of available operations.
- View all test results in a single pane of information in a table with details about failures.
- Configure a schedule to run the tests with daily, weekly, and monthly options.

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 |                     |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Automation Scripts

Make sure the **HealthCheckTableManager** Automation script is available in the DMS.

## How to use

### General

This page displays an overview of the test results over time, including the **Total Number Of Tests**, **Failure Rates**, and **Last Tests Date**.

### Test Configuration

#### Test Configuration Table

In the Test Configuration Table, you can create tests based on **Automation scripts** or **subscriptions** based on the Parameter Subscription table:

1. Right-click the Test Configuration Table.

1. Select **Add Test** in the context menu.

1. In the pop-up window (which is an interactive Automation script), enter the following information:

   - **Test Type**: Select if the test is a script-based test or a subscription-based test.

   - **Name**: Select the test name from the available scripts or subscriptions (based on the Test Type selection).

   - **Operator**: Select the operator from the available options:

     - Equal To (==)

     - Not Equal To (!=)

     - Less Than (<)

     - Less or Equal Than (<=)

     - Greater Than (>)

     - Greater or Equal Than (>=)

     - Between (BETWEEN)

     - Not Between (NOT BETWEEN)

   - **Threshold**: Provide the expected value that will be compared using the selected operator.

   - **Element Filter**: Provide the filter for the elements using wildcard filtering.

   - **Display Key Filter**: Provide the filter for the index (if applicable) using wildcard filtering.

   - **Status**: Select this option if you want the test to be included for the next test run, or clear the option if it should not be included.

You can also edit tests via the context menu.

To delete tests, click the **Delete** button in the last column.

#### Parameter Subscription Table

In the Parameter Subscription Table, you can create subscriptions based on standalone or column parameters of any element present in the DMS.

1. Right-click the Parameter Subscription Table.

1. Select **Add Subscription** in the context menu.

1. In the pop-up window (which is an interactive Automation script), enter the following information:

   - **Subscription Name**: Provide the name the subscription will have, which will be displayed during test creation.

   - **Protocol**: Select the protocol name from a list of all the available protocols in the DMS.

   - **Protocol Version**: Provide the protocol version for this subscription. The provided version will affect which elements are checked during test runs.

   - **Parameter Type**: Select the parameter type: *Standalone* or *Table Parameter*.

   - **Table**: Only available if Parameter Type is set to *Table Parameter*. Select the table that contains the parameter that is going to be mapped.

   - **Parameter**: Select the parameter to be mapped from the available parameters from the selected connector and, if applicable, the selected table.

You can also edit subscriptions via the context menu.

To delete subscriptions, click the **Delete** button in the last column.

### Results

When the tests run, all enabled tests will be displayed in this table, with some information like Test Name, Failure Rate, Success and Failure count, details about failed tests, and the time of the test.

This table will be cleaned up based on the auto-delete time configured at the top of the page.

You can also choose to clean all results from the table manually.

### Configuration

The connector contains settings to customize its behavior:

- **Email Addresses**: Allows you to provide a list of emails that will receive a report of the test run, similar to the results table.

- **Recurrence**: Allows you to view and edit the recurrence set for the scheduled test runs, with *Daily*, *Weekly*, and *Monthly* options. You can always see when the next test run is due.

- **Longer Duration Time**: Allows you to specify a duration during which tests will run and get information on their failure rate.

- **Execute Tests**: You can start the execution of any tests even if it is not the scheduled time for the next run. This option will trigger all currently enabled tests. **Please note that tests executed this way will not send report emails.**
