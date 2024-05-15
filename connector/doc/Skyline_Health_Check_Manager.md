---
uid: Connector_help_Skyline_Health_Check_Manager
---

# Skyline Health Check Manager

DMA systems have some resources like Disk Space, Memory Management, Boot Time, and more, that require systematic checks to ensure the system has no ongoing issues and its performance is not being affected. 
Skyline Health Check Manager helps with these checks, with features to schedule subscription and script based tests on system and element parameters.

## About

Skyline Health Check Manager helps users with System Checks of resources in a single window pane, with predefined threshold, element and index filtering on a scheduled logic within the connector.
 
With this connector users will be able to:

- Map standalone and table column parameters of any protocol and any protocol version to a subscription.
- Add, Edit or Delete tests based on DMS Scripts or Subscriptions, that need to meet certain threshold based on a set of available operations
- View all tests results in a single pane of information on a table with details about failures.
- Configure schedule of the tests on Daily, Weekly and Monthly options.

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial version</li>        |-         |-         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Automation Scripts

Make sure the following scripts are available in the DMS:

- HealthCheckTableManager

## How to use

### General

This page displays an overview of the tests results across time, including **Total Number Of Tests, Failure Rates, Last Tests Date**

### Test Configuration

#### Test Configuration Table

In the Test Configuration table you can create tests based on **DMA Scripts** or **Subscriptions** based on the Parameter Subscription table.

1. Right-Click the Test Configuration Table.
2. Select **Add Test...** in the context menu.
3. In the pop-up window (which is an interactive Automation script), enter the following information:
	- **Test Type**: Select if the test is a Script based test or a Subscription based test.
	- **Name**: Select the test name from the available scripts or subscriptions (based on Test Type selection).
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
	- **Status**: Check if you want the test to be included for next tests run or unchecked if you don't want it to be included.

You can also edit tests via context menu.
To delete tests click the end column with the "Delete" button

#### Parameter Subscription Table

In the Parameter Subscription table you can create subscription based off standalone or column parameters of any element present in the DMS.

1. Right-Click the Parameter Subscription Table.
2. Select **Add Subscription...** in the context menu.
3. In the pop-up window (which is an interactive Automation script), enter the following information:
	- **Subscription Name**: Provide the name the subscription will have and will be displayed on a test creation.
	- **Protocol**: Select the protocol name from a list of all the available protocols on the DMS).
	- **Protocol Version**: Provide the protocol version for this subscription, the version provided will affect which elements are checked on tests runs.
	- **Parameter Type**: Select the parameter type between Standalone and Table Parameter.
	- **Table**: Only available if Parameter Type 'Table Parameter' is selected. Select the table that contains the that is going to be mapped.
	- **Parameter**: Select the parameter to be mapped from the available parameters on the selected connector and if applicable, table selected.

You can also edit subscriptions via context menu.
To delete subscriptions click the end column with the "Delete" button

### Results

When the tests run, all of enabled tests will be displayed on this table with some information like Test Name, Failure Rate, Success and Failure count, details about failed tests and time of the test.
This table will be cleaned based on the configured Auto Delete time at the top of the connector page.
You can also choose to clean all results from the table.

### Configuration

The connector contains configurations to customize its behavior:
	- **Email Addresses**: Allows the user to provide a list of emails that will receive a report of the tests run, similar to the results table.
	- **Recurrence**: Allows the user to view and edit the recurrence set for the tests to schedule runs with Daily, Weekly and Monthly options. The user can always see when is due the next tests run.
	- **Longer Duration Time**: The user can provide a time to account for tests run within that period and get information on the failure rate of them.
	- **Execute Tests**: The user can starts any tests execution even if its not the scheduled time for the next run, this will run all enabled tests and send the report emails.
