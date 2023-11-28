---
uid: Connector_help_CISCO_NXOS_Manager
---

# CISCO NXOS Manager

The **NX-OS** is an OpenConfig connector. TODO...

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version. | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 10.4-1                 |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: *80*
- **Bus address**: *ByPassProxy*
- **Timeout on a single command (ms)**: *45000* (avoids timeouts in slow responses)

### Initialization

#### Configuration of credentials for eAPI communication
On the Element Settings Page, fill in the eAPI Settings and push Log In to establish the eAPI communication.

#### Configuration of credentials for OpenConfig communication
On the Element Settings Page, fill in the OpenConfig Settings and push Connect to establish the OpenConfig communication.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### System

This page displays the device generic information, which contains the following parameters:  **Memory Utilization**, **Physical Memory**, **Reserved Memory**, **Hostname**, **Software Version**, **Current Datetime**, **Boot Time**, **Domain Name**, **Login Banner**, **MOTD Banner**, **Last Configuration** and **gRPC Connection State**,.

This page also contains 3 subpages which can be accessed by clicking the following buttons:

- **CPU:** Displays the **CPUs Table** which contains the following columns: **Name**, **Total**, **User**, **Kernel**, **Hardware**, **Software**, **Nice**, **Wait** and **Idle**.
- **Processes:** Displays the **System Processes Table** which contains the following columns: **Name**, **Display Key**, **Start-Time**, **User CPU Usage**, **System CPU Usage**, **CPU Utilization**, **Memory Utilization**, and **Args**.
- **Alarms:** Displays the **System Alarms Table** which contains the following columns: **Pid**, **Resource**, **Text**, **Time Created**, **Severity** and **Type ID**.

### Platform PSU

This page displays the **Power Supply Units Table** which contains the following columns: **Name**, **State**, **Capacity**, **Input Current**, **Input Voltage**, **Output Current**, **Output Voltage** and **Output Power**.

### Platform Fan

This page displays the **Fan Table** which contains the following columns: **Name** and **Speed**.

### Platform Temperature

This page displays the **Temperature Table** which contains the following columns: **Display Key**, **Name**, **Type**, **Temperature**, **Status** and **Location**.

### Interfaces

This page displays the **Interfaces Table** which contains the following columns: **Name**, **Description**, **Display Key**, **Operational Status**, **Admin Status**, **In Bit Rate**, **Out Bit Rate**, **MTU**, **Type**, **Loopback Mode**, **Last Change**, **State** **Interface Index**, **Logical**, **In Octets**, **Out Octets**, **Carrier Transitions**, **Last Clear**, **User Description**, **Row State** and **Action**.

### Interfaces Counters

This page displays two tables:
- **Interfaces Counters Rx Table** which contains the following columns: **Interface**, **In Octets**, **In Packets**, **In Unicast Packets**, **In Broadcast Packets**, **In Multicast Packets**, **In Discards**, **In Errors**, **In Unknown Protocols** and **FK to Interfaces**.
- **Interfaces Counters Tx Table** which contains the following columns: **Interface**, **Out Octets**, **Out Packets**, **Out Unicast Packets**, **Out Broadcast Packets**, **Out Multicast Packets**, **Out Discards**, **Out Errors**, **In Unknown Protocols** and **FK to Interfaces**.

### Interfaces Tranceivers

This page displays two tables:
- **Interfaces Transceivers Table** which contains the following columns: **Instance**, **Present**, **Vendor**, **Type**, **Voltage** and **Serial Number**.
- **Interfaces Physical Channels Table** which contains the following columns: **Instance**, **Input Power**, **Output Power**, **Laser Bias Current**, **Foreign Key**.

### Interfaces VLAN

This page displays the **Interfaces VLAN Table** which contains the following columns: **Instance**, **Interface Mode**, **Native VLAN**, **Access VLAN** and **Trunk VLAN**.

### ACL

This page displays three tables:
- **Access Control Lists Table** which contains the following columns: **Name** and **Type**.
- **Access Control List Rules Table** which contains the following columns: **Instance**, **Sequence ID**, **Name**, **Forwarding Action**, **Source**, **Destination** and **IP Protocol**.
- **Access Control List Assignment Table** which contains the following columns: **Interface**, **Ingress ACL Name IPv4**, **Egress ACL Name IPv4**, **Ingress ACL Name IPv6** and **Egress ACL Name IPv6**.

### LLDP

This page displays the **LLDP Neighbors Table** which contains the following columns: **Index**, **Display Key**, **Local Interface Name**, **State**, **Neighbor System Name**, **Neighbor System Description**, **Neighbor Port ID**, **Neighbor Port Description**, **Neighbor Management Address**, **Neighbor ID**, **Neighbor Chassis** and **Neighbor Chassis ID Type**.

### BGP

This page displays the **BGP Neighbors Table** which contains the following columns: **Remote Address**, **Remote Port**, **Local Address**, **Local Port**, **State**, **Administrator Status**, **Remote AS**, **Input Updates**, **Input Notifications**, **Output Updates**, **Output Notifications**, **Established Transitions**, **Established Time**, **Connect Retry Interval**, **Hold Time**, **Keep Alive** and **Minimum Route Advertisement Interval**.

### Multicast Routing

This page displays the **Multicast Routes Table** which contains the following columns: **Key**, **Source**, **Multicast**, **Incoming Interface** and **Outgoing Interface**.

### NBM

This page displays two tables:
- **NBM Interfaces Table** which contains the following columns: **ID**, **Outgoing Bandwidth**, **Incoming Bandwidth**, **Outgoing Remaining**, **Incoming Remaining**, **Unicast Bandwidth Configuration**, **Outgoing Unicast Bandwidth**, **Incoming Unicast Bandwidth**, **Bandwidth Unit**, **Outgoing Usable**, **Incoming Usable**, **Interface Name**, **IP Address**, **IP Mask** and **State**.
- **NBM Flows Table** which contains the following columns: **ID**, **Bucket**, **Bandwidth**, **DSCP**, **Outgoing Interfaces Count**, **Flow Policy**, **Group**, **Incoming Interface**, **Interface Name**, **Is FHR**, **Policed**, **Priority**, **Queue ID** and **Source**.

### PTP

This page displays the following standalone parameters:  **Mode**, **Clock ID**, **PTP Domain**, **Number of PTP Ports**, **Priority 1**, **Priority 2**, **Multi-Domain Status**, **Multi-Domain Priority 1**, **Multi-Domain Priority 2**, **Offset**, **Mean Path Delay**, **Mean Path Delay Range**, **Mean Path Delay Tolerance Status**, **Mean Path Delay Tolerance**, **Reverse Path Delay tolerance Status**, **Reverse Path Delay Tolerance**, **Steps Removed**, **Clock Class**, **Clock Accuracy**, **Clock Variance**.

This page also contains 2 subpages which can be accessed by clicking the following buttons:

- **Grandmaster Clock:** Displays **PTP Grandmaster Clock** page with the following standalone parameters: **Parent Change Notification**, **Parent Stats**, **Parent Clock ID**, **Parent Port Number**, **Parent Clock Variance**, **Parent Phase Change Rate**, **PTP Grandmaster Capable**, **Grandmaster Change Notification** and **Grandmaster IP Address**, **Grandmaster Clock ID**, **Grandmaster Priority 1**, **Grandmaster Priority 2**, **Grandmaster Clock Class**, **Grandmaster Clock Accuracy**, **Grandmaster Clock Variance**.
- **Time Properties:** Displays **PTP Time Properties** page with the following standalone parameters: **PTP Convergence Time**, **One Step**, **Periodic Update**, **Periodic Update Interval**, **Automatic Clock Synchronization**, **Time Tracing**, **UTC Offset**, **Current UTC Offset** and **Leap 59**, **Leap 61**, **Frequency Tracing**, **Grandmaster Clock Timescale**, **Grandmaster Clock Source**.

### PTP Ports

This page displays the **PTP Ports Table** which contains the following columns: **ID**, **Number**, **Interface**, **State**, **Admin State**, **Transport**, **Delay Mechanism**, **Min Delay Request Interval**, **Asymetric Delay**, **Mean Path Delay**, **IP Address**, **Log Announce Interval**, **Announce Receipt Timeout**, **Log Sync Interval**, **Log Min Permitted Delay Interval**, **Version Number**, **Communication Mode**, **Profile**, **Delay Response**, **Announce Interval Type**, **Announce Timeout Type**, **Sync Interval Type**, **Delay-Request Minimum Interval Type**, **Asymmetric Direction**, **gPTP Propagation Delay Threshold**, **Profile Override**, **PTP Cost**, **PTP MAC Forwarding**, **PTP Interface Domain**, **PTP RX Missmatch**, **Transport Role**, **VLAN** and **Display Key**.

### Explorer

This page is used to access the **NX-API** which allows sending commands, the page contains the following standalone parameters: **API Commands**, **Version**, **Method**, **Format**, **Command Type**, **Error Action** and **API Response**.

This page also contains a subpage which can be accessed by clicking the following button:

- **Request Viewer:** Displays the standalone parameter **API Request** which shows the full Request that is going to be sent based on the commands added by the user.

### Element Settings

On this page, you can configure the **OpenConfig** and **NX-API** settings.

- **OpenConfig Settings** section contains the following standalone parameters: **gRPC Connection State**, **gNMI Version**, **OpenConfig IP Address**, **Port**, **User Name**, **Password** and **Client Certificate**.
- **NX-API Settings** section contains the following standalone parameters: **API Authentication Status**, **API Username** and **API Password**.