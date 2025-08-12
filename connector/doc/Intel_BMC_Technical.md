---
uid: Connector_help_Intel_BMC_Technical
---

# Connector technical documentation template

## About

The Intel Integrated Baseboard Management Controller (BMC) is a critical component of server management, providing remote monitoring and control capabilities for Intel® Server Systems powered by the Intel® Xeon® Scalable processor family.

This controller implements the OpenBMC Redfish API Specification*, supporting industry-standard Redfish schemas for system management. These schemas define available resources, including their URIs, supported HTTP methods, properties, links, and actions, enabling seamless integration with automation and orchestration tools.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- IP address/host: The polling IP of the device.
- IP port: The device API IP Port (default 443)
- Bus address: ByPassProxy

### Usage

#### General

This page displays the device generic information, which contains the following parameters: **Product Name**, **Manufacturer**, **Server Name**, **UUID**, **Serial Number**, **Product ID**, and **System ROM**.

#### Connection Setup

The Connection Setup page displays the **User Name** and **Password** text boxes where the credentials information are filled for the HTTP API polling. Also we have the **Connection Status** which can be Connected and Not Connected.

#### System Information

This page displays the **State**, **Health**, **Server Power**, **UID Indicator**, **Manager Description**, **Manager UUID**, **Manager State**, **Manager Health**.

#### Processors

Displays the **Processors Table** which contains the following columns: **Index**, **Name**, **State**, **Health**, **Instruction Set**, **Manufacturer**, **Max Speed**, **Total Cores**, **Total Threads**, and **Model**.

#### Memory

Displays the **Memory Summary Table** which has the following parameters: **Index**, **State**, **Health**, **DIMM Type**, **Slot**, **Module Type**, **Type**, **Size GiB**, **Maximum Frequency**, **Part Number**, and **Manufacturer**.

#### Storage

Displays the Processors Table which contains the following columns: **Index**, **Name**, **Protocol**, **Serial Number**, **Media Type**, **Rotation Speed**, **Model**, **Revision**, and **Capacity MiB**.

#### Chassis

Displays the Chassis Information Table which contains the following columns: **Index**, **Name**, **Part Number**, **Power State**, **LED Indicator**, **Location**, **Height**, **Serial Number**, **Health**, **State**, **Manufacturer**, **Model**, **Chassis Type**, **Min Power Watts**, **Max Power Watts**, **Average Consumed Power**, **Current Consumed Power**, and **Period**.

#### Power

This page contains the Power Supplies Table which has the following parameters: **Index**, **Name**, **Health**, **State**, **Firmware**, **Model**, **Serial Number**, **Part Number**, and **Manufacturer**.

#### Fans

Displays the Fans Table which has the following parameters: **Index**, **Name**, **Health**, **State**, **Speed** and **Max Speed**.

#### Temperatures

Displays the Temperature Table which has the following parameters: **Index**, **Name**, **Health**, **State**, and **Temperature**.

### Web Interface

This page displays the Web Interface of the device. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
