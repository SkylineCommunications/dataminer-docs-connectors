---
uid: Connector_help_Generic_SMPP_SMS_Sender_Technical
---

# Generic SMPP SMS Sender

## About

This connector establishes a TCP/IP connection with an SMS center using the SMPP v3.4 protocol. In this setup, DataMiner acts as the ESME, enabling both sending and receiving of SMS messages via the SMSC, which forwards outgoing messages to their destination and delivers incoming messages back to DataMiner.

## Configuration

### Connections

#### Smart-Serial - Main

This connector uses a smart-serial connection and requires the following input during element creation:

SMART-SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination.

## How to use (2.0.0.x range)

### General

On the right side of this page, you can find the **Transceiver Settings**, which are used to configure the connection to the SMSC. The following parameters are available:

- **Bind Status**: This parameter indicates the status of the connection to the SMSC.
- **Automatic Re-Bind**: This parameter indicates whether the connection to the SMSC should be re-established automatically when it is lost.
- **Bind Transceiver**: This button establishes the connection to the SMSC. The connection is established using the parameters specified on the **Configuration** page.
- **Unbind Transceiver**: This button closes the connection to the SMSC.

On the left side of this page are the parameters for sending messages. The following parameters are available:

- **Destination Number**: The destination phone number to which the message will be sent. Make sure you start with the country code when filling in the destination phone number. For example, if a message needs to be sent to the number "+32 471 123456", fill in "+32471123456".
- **Message**: The text of the message that will be sent.
- **Status Message**: Displays the status of the last sent message.
- **Send Message**: This button sends the message to the destination number. The message is sent using the parameters specified on the **Configuration** page.

### Sent Messages

This page contains a table with an overview of all sent messages. The table contains the following columns:

- **Destination Number**: The destination phone number to which the message was sent.
- **Message**: The text of the message that was sent.
- **Time Sent**: The time when the message was sent.
- **Action**: Button to delete the specific row from the table.

In the top-right corner, the **Clear Table** button can be used to clear the data from the table.

In the lower-right corner, the **Cleanup Config** button opens a page with the cleanup configuration for the Sent Messages table. This subpage contains the following options:

- **Cleanup Method**: The method to be used for cleaning up the Sent Messages table. The options are:
  - **Row Count**: Selecting this option will remove the oldest rows from the table until the number of rows in the table is equal to the value specified in **Max Rows**.
  - **Row Age**: Selecting this option will remove the oldest rows from the table until the age of the oldest row in the table is equal to the value specified in **Max Age**.
  - **Combo**: Selecting this option will remove the oldest rows from the table until the number of rows in the table is equal to the value specified in **Max Rows** and the age of the oldest row in the table is equal to the value specified in **Max Age**.
- **Max Rows**: This parameter contains the maximum number of rows that can be present in the Sent Messages table.
- **Max Age**: This parameter contains the maximum age of the rows that can be present in the Sent Messages table.
- **Cleanup Amount**: This parameters sets the percentage of rows that will be removed from the table when the cleanup method is executed.

### Received Messages

This page contains a table with an overview of all received messages. The table contains the following columns:

- **Source**: The source from which the message was received.
- **Message**: The text of the message that was received.
- **Time Received**: The time when the message was received.
- **Action**: Button to delete the specific row from the table.

In the top-right corner, the **Clear Table** button can be used to clear the data from the table.

In the lower-right corner, the **Cleanup Config** button opens a page with the cleanup configuration for the Received Messages table. This subpage contains the following options:

- **Cleanup Method**: This parameter contains the method to be used for cleaning up the Received Messages table. The options are:
  - **Row Count**: Selecting this option will remove the oldest rows from the table until the number of rows in the table is equal to the value specified in **Max Rows**.
  - **Row Age**: Selecting this option will remove the oldest rows from the table until the age of the oldest row in the table is equal to the value specified in **Max Age**.
  - **Combo**: Selecting this option will remove the oldest rows from the table until the number of rows in the table is equal to the value specified in **Max Rows** and the age of the oldest row in the table is equal to the value specified in **Max Age**.
- **Max Rows**: This parameter contains the maximum number of rows that can be present in the Received Messages table.
- **Max Age**: This parameter contains the maximum age of the rows that can be present in the Received Messages table.
- **Cleanup Amount**: This parameters sets the percentage of rows that will be removed from the table when the cleanup method is executed.

### Configuration

On the Configuration page, you can find all configuration parameters that affect the initialization of the connection to the SMSC and the communication between DataMiner (as "ESME") and the "SMSC".

Make sure that at least **System ID** (= username) and **Password** are correct and match with the credentials needed to set up the connection with the SMSC. If no authentication is necessary, you can leave them blank. The same applies for the **Source Phone Number**.

The rest of the configuration parameters have default values, which should be a good start when initiating a new element. In case default values do not work, you may need to get advice from people familiar with the SMSC for specific settings.

## How to use (1.0.0.x range)

This range of the connector uses a serial connection. The required input for the connection is the same as the smart-serial connection.

Make sure all the parameters on the **Configuration** page are filled in. For some options, a time can be specified. To disable these options, fill in 0 seconds.

Once all parameters are configured and applied, it should be possible to send an SMS to a destination number from the **General** page:

1. Fill in the text to be sent in the **Message** field and apply this change.

1. Fill in the destination phone number (the mobile phone number to which the message needs to be sent) and apply this change.

   Make sure you start with the country code when filling in the destination phone number. For example, if a message needs to be sent to the number "+32 471 123456", fill in "+32471123456".

1. Click the **Send Message** button to send the message.

   A status message will show whether the message was sent successfully.

## Notes

This connector can be used in combination with an Automation script that fills in the message and phone number to initiate SMS notifications.
