---
uid: Connector_help_Digital_Alert_Systems_DASDEC-III
---


# Digital Alert Systems DASDEC-III

The purpose of this connector is to receive alerts from the DASDEC-III. It will act as a server using the smart-serial protocol. It can log received messages to an Elasticsearch database. To forward alerts, SCP via public-private key authentication must be used.

## About

### Version Info

| Range              | Key Features                | Based on | System Impact                          |
|--------------------|-----------------------------|----------|----------------------------------------|
| 1.0.0.x            | Initial version             | -        | -                                      |
| 1.0.1.x [SLC Main] | Added HTTP/SNMP connections | 1.0.0.2  | Element configuration must be adapted. |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 5.2.2                  |
| 1.0.1.x   | 5.2.2                  |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Serial Main Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The connector will act as a server. Set this field to "*Any*".
  - **IP port**: By default *20002*. A different port can be specified.

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **Device address**: This is not required.

SNMP Settings:

- **Port number**: *161*
- **Get community string**: *public*
- **Set community string**: *private*

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: *80*
- **Bus address**: *ByPassProxy*

### Initialization

For full communication with DataMiner, various prerequisites must be met, as detailed below.

#### Licenses

On the DASDEC-III, navigate to **Setup** > **Main** > **Main/License** and ensure that the following licenses are installed:

- **Master**: This is required for the DASDEC-III for users to operate and configure the device.
- **V5.0 Enabling Key**: This is required for the DASDEC-III for users to operate and configure the device.
- **EAS_NET (includes DVS169)**: Under the Net Alert Licenses, this is required for the smart-serial connection and to ensure that DataMiner will receive EAS alerts from the device.

#### EAS NET Setup

With the **EAS_NET** license installed, the DASDEC-III can send data over TCP/IP networks. To set this up, follow these steps:

1. On the DASDEC-III, navigate to **Setup** > **Net Alerts**.

1. In the EAS NET Client section, enable all options under **Master Switches**.

1. Add a new EAS NET Client with the following settings:

   - **Client Name**: Any name.
   - **Remote IP**: The IP address of the DataMiner server.
   - **Port**: The port specified for the smart-serial connection during element creation (default: 20002).
   - **Event Transfer Protocol**: TCP event notification.
   - **Local Network Device**: First (main) Ethernet.

1. Accept the changes.

1. Test the connection by clicking the **Test Connection** button.

   The device should be able to connect to the DataMiner server. If the connection fails, check the network settings and firewall rules.

#### Public-Private Key Initialization

To perform the public-private key initialization, follow these steps:

1. On the **General** page, fill in the "Host" as the host IP of the DASDEC.

1. On the **General** page, click the **Generate Keys** button.

   This will generate a private key file in `C:\Skyline DataMiner\Documents\DASDEC\privatekey` as well as a public key in the **Public Key** parameter.

1. In the DASDEC web GUI, navigate to **Setup** > **Network** > **Security**, and change the **SSH Key Type** in the dropdown list to RSA.

1. Copy the public key from the parameter and paste it into the box next to the **Add Public Key** button.

1. Click the **Add Public Key** button.

1. Click **Accept SSH Authorization Change**.

1. Ensure that the DataMiner IP address is included in the **SSHD Whitelist Configuration**.

You can now approve mandatory/voluntary open alerts. If an alert is not forwarded, check the element logging for errors.

#### SNMP Initialization

SNMP on the DASDEC-III requires a package to be installed. To set this up, follow these steps:

1. Reach out to Digital Alert Systems support to obtain the SNMP package.

1. Navigate to **Setup** > **Main** > **Upgrade** and install the SNMP package.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### General

On this page, you can generate the **SSH public/private key pair** and configure the **Elastic Storage Period**.

This page also contains the following page buttons:

- **Driver Configuration**: Here you can view and clear the error counter.
- **Display Key Configuration**: Here you can configure the display key across all message-related tables.
- **Authentication**: Here you can configure the authentication for the HTTP connection.

### Alerts

This page contains the **Mandatory Open Alerts** and the **Voluntary Open Alerts** tables.

Each alert contains a countdown. Once the countdown reaches zero, different actions can occur depending on the type of alert:

- EAN, NPT, RMT: The message will be forwarded to DASDEC/sent to the **Alert Logging** table
- RWT: The message will be forwarded to DASDEC based on the last message countdown and then moved to the **Alert Logging** table
- All other messages: The message will not be forwarded to DASDEC, and it will be moved to the **Alert Logging** table with the status "expired".

Note that the operator can manually forward a message at any time using the **Approve** button.

Via the **Alert Logging** page button, you can access the Alert Logging table as well as various configuration parameters.

### Debug

This page contains the last received message.

You can also trigger an RWT here by filling in all required Net parameters. You can also trigger an Automatic RWT, which will automatically send an RWT every 7 days.

### Web Interface

This page displays the web GUI.
