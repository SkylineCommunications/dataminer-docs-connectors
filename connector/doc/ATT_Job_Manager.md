---
uid: Connector_help_ATT_Job_Manager
---

# ATT Job Manager</h1>

## About

This is a virtual connector used to execute **automation scripts (jobs)** when certain conditions are met. It works together with the **ATT Channel Manager** connector (version 1.0.1.9 and later). **The ATT Job Manager** listens for notifications from the **ATT Channel Manager** and executes **automation scripts** in response.

It allows you to register automation scripts (jobs) that accept at least three input parameters: **Command**, **Result**, and **Feedback**. It is possible to create a wide variety of jobs and assign them to a specific trigger. The connector will automatically execute the registered **Jobs** when a matching notification is received.

The **Command** parameter is used to send information to the automation script.

The **Result** parameter is a numeric value used to notify the ATT Job Manager about execution result of the automation script and can be:

**Failed** = 2, **Succeeded** = 3

The **Feedback** parameter is used to send information from the script to the ATT Job Manager about the possible cause of the automation script failure, and it will be displayed in the Queue Table.

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

## Usage

### Jobs

The **Jobs** page contains a table with all of the available jobs. Using a context menu, you can add new jobs or remove existing jobs.

### Queue

The **Queue** page contains a table with all of the enqueued jobs to be executed. Jobs in the queue are executed sequentially. The time interval between the execution of two jobs can be configured. Using the buttons **Remove** and **Execute Now**, it is possible to delete jobs from the queue or execute them without waiting for the execution interval.

### Executed Jobs

The **Executed Jobs** page contains a table with all of the enqueued jobs that were executed with success. Jobs in this table can be removed manually. This table implements an **Auto Cleanup** functionality that can be configured using a pop-up page.

### Failed Jobs

The **Failed Jobs** page contains a table with all of the enqueued jobs that failed to execute. Jobs in this table can be executed manually or permanently deleted. This table implements an **Auto Cleanup** functionality that can be configured using a pop-up page.

## Notes

The **ATT Job Manager** works together with the **ATT Channel Manager** protocol and certain **automation scripts**, for example, **Script_ATT IPX Update_V2**.
