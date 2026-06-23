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

On this page, you can generate the **SSH public/private key pair** and configure the **Elastic Storage Period**. Pressing the **Generate Keys** button will generate a new key pair, which will be used for SCP authentication. The public key must be added to the DASDEC-III web GUI, while the private key is stored in the DataMiner server.

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

Via the **Alert Logging** page button, you can access the Alert Logging table as well as various configuration parameters. Alerts that have been acknowledged or expired will be moved to the Alert Logging table. If needed, the operator can restore an alert from the Alert Logging table back to the Mandatory/Voluntary Open Alerts table. The **Elastic Storage Period** parameter defines how long alerts will be stored in the Alert Logging table.

Via the **Alert Automation** page button, you can set up the DataMiner connector to trigger an RWT automatically every 7 days. This is useful for testing the alert forwarding functionality.

### Debug

This page contains the last received message.

### Web Interface

This page displays the web GUI.
