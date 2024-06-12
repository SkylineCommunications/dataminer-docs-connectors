---
uid: Connector_help_DASDEC-III
---


# Digital Alert Systems DASDEC-III

The purpose of this connector is to receive alerts from the DASDEC-III. It will act as a server using the smart-serial protocol. It can log received messages to an elastic database. To forward alerts, SCP via public-private key authentication must be used.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 5.2.2                   |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Serial Main Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The connector will act as a server. Set this field to "*Any*".
  - **IP port**: By default *20002*. A different port can be specified.

### Initialization

To perform the public-private key initialization, follow the following steps
1) On General page, fill in the "Host" as the host IP of the DASDEC.
2) On General page, click the "Generate Keys" button. This will generate a private key file in C:\Skyline DataMiner\Documents\\DASDEC\privatekey as well as a public key in the "Public Key" parameter
3) On the DASDEC web GUI, navigate to Setup/Security and change the SSH Key Type under the drop down list to RSA
4) Copy the public key from the parameter and paste into the Text Box next to the "Add Public Key" button
5) Click the "Add Public Key" button
6) Click "Accept SSH Authorization Changes"
7) User can now Approve Mandatory/Voluntary Open alerts. If alert is not forwarded, check the element logging for errors.

## How to Use

### General

On this page, you can generate the SSH Public/Private key pair and configure the Elastic Storage Period. It also contains the following page buttons:
-Driver Configuration - Here you can view the error counter/clear the error counter
-Display Key Configuration - Here you can configure the display key accross all message-related tables

### Alerts

This page contains the **Mandatory Open Alerts** and the **Voluntary Open Alerts** tables. Each alert contains a countdown. Once the countdown reaches zero different actions will occur depending on the type of alert:
-EAN, NPT, RMT - Message will be forwarded to DASDEC/moved to **Alert Logging** table
-RWT - Message will be forwarded to DASDEC based on last message countdown and then moved to **Alert Logging** table
-All other messages: Message will not be forwarded to DASDEC and be moved to **Alert Logging** table with a status of "expired".
Do note that the operator can manually forward a message at any time using the "Approve" button

Also contains "Alert Logging" page button
-Alert Logging: Includes the Alert Logging table as well as various configuration parameters. 

### Debug

This page contains the last received message. Here a user can trigger a RWT provided they fill in all of the required Net parameters. They can also trigger an Automatic RWT, which will automatically send an RWT every 7 days.
