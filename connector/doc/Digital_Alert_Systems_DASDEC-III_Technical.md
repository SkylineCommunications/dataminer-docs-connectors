---
uid: Connector_help_Digital_Alert_Systems_DASDEC-III_Technical
---

# Digital Alert Systems DASDEC-III

## About

The Digital Alert Systems DASDEC-III is a professional Emergency Alert System (EAS) decoder and encoder used by broadcasters to receive, manage, and forward emergency alerts across radio, TV, and IP networks. It handles mandatory and voluntary EAS messages and supports alert forwarding over TCP/IP networks using the EAS NET protocol.

The DASDEC-III connector integrates the device into DataMiner by acting as a smart-serial server, receiving EAS alerts pushed from the DASDEC-III over TCP/IP. It also uses SNMP for device status monitoring. Received alerts can be logged to an Elasticsearch database for historical records. Alert forwarding back to the DASDEC-III is handled securely via SCP using public-private key authentication.

## Configuration

### Connections

#### Serial Main Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The connector will act as a server. Set this field to *Any*.
  - **IP port**: By default, *20002*. A different port can be specified.

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

![Main Licenses](~/connector/images/DASDEC-III_Main_License.png)

![Net Alert Licenses](~/connector/images/DASDEC-III_Net_Alert_License.png)

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

![EAS NET Client Setup](~/connector/images/DASDEC-III_EAS_NET_Client.png)

#### Public-Private Key Initialization

To perform the public-private key initialization, follow these steps:

1. On the **General** page, fill in the host IP of the DASDEC.

1. On the **General** page, click the **Generate Keys** button.

   ![SSH Key Generation](~/connector/images/DASDEC-III_SSH_Key_Generation.png)

   This will generate a private key file in `C:\Skyline DataMiner\Documents\DASDEC\privatekey` as well as a public key in the **Public Key** parameter.

1. In the DASDEC web GUI, navigate to **Setup** > **Network** > **Security**, and change the **SSH Key Type** in the dropdown list to RSA.

1. Copy the public key from the parameter and paste it into the box next to the **Add Public Key** button.

1. Click the **Add Public Key** button.

   ![SSH Key Setup](~/connector/images/DASDEC-III_SSH_Key_Setup.png)

1. Click **Accept SSH Authorization Change**.

1. Ensure that the DataMiner IP address is included in the **SSHD Whitelist Configuration**.

   ![SSH Key Whitelist](~/connector/images/DASDEC-III_SSHD_Whitelist.png)

You can now approve mandatory/voluntary open alerts. If an alert is not forwarded, check the element logging for errors.

#### SNMP Initialization

SNMP on the DASDEC-III requires a package to be installed. To set this up, follow these steps:

1. Reach out to Digital Alert Systems support to obtain the SNMP package.

1. Navigate to **Setup** > **Main** > **Upgrade** and install the SNMP package.

![Package Installation](~/connector/images/DASDEC-III_Package_Upgrade.png)

## How to Use

### General

On this page, you can generate the **SSH public/private key pair** and configure the **Elastic Storage Period**. Clicking the **Generate Keys** button will generate a new key pair, which will be used for SCP authentication. The public key must be added to the DASDEC-III web GUI, while the private key is stored in the DataMiner server.

This page also contains the following page buttons:

- **Driver Configuration**: Allows you to view and clear the error counter.
- **Display Key Configuration**: Allows you to configure the display key across all message-related tables.
- **Authentication**: Allows you to configure the authentication for the HTTP connection.

### Alerts

This page contains the **Mandatory Open Alerts** and the **Voluntary Open Alerts** tables.

There is a countdown for each alert. Once the countdown reaches zero, different actions can occur depending on the type of alert:

- **EAN, NPT, RMT**: The message is forwarded to DASDEC and sent to the **Alert Logging** table
- **RWT**: The message is forwarded to DASDEC based on the last message countdown and then moved to the **Alert Logging** table
- **All other messages**: The message is **not forwarded** to DASDEC but is moved to the **Alert Logging** table with the status *expired*.

Note that you can manually forward a message at any time using the **Approve** button.

Via the **Alert Logging** page button, you can access the Alert Logging table as well as various configuration parameters. Alerts that have been acknowledged or expired are moved to the Alert Logging table. If needed, you can restore an alert from the Alert Logging table back to the Mandatory/Voluntary Open Alerts table. The **Elastic Storage Period** parameter defines how long alerts are stored in the Alert Logging table.

Via the **Alert Automation** page button, you can set up the DataMiner connector to trigger an RWT automatically every 7 days. This is useful for testing the alert forwarding functionality.

### Debug

This page contains the last message received.

### Web Interface

This page displays the web GUI. The web interface is only accessible when the client machine has network access to the product.
