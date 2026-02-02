---
uid: Connector_help_DNF_Controls_USP-8D
---

# DNF Controls USP-8D

## About

The **DNF Controls USP-8D** can be configured by and can configure the DNF Controls USP-8D **Control Console**.

This connector is polled by the DNF Controls USP-8D Control Console. Since the latter device cannot be accessed by SNMP, the **device polls the element** instead of the other way around.

Sets can be performed from the connector and will be updated, depending on the interval between gets on the Control Console.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|------------------|-----------------|---------------------|-------------------------|
| 1.0.0.x          | Initial version | No                  | Yes                     |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | V 2.33F                       |

## Configuration

### Connections

#### SNMP Connection

This connector uses an SNMP connection to do SNMP sets on the device. For this, the **IP address you will access with the device** must be specified during element creation.

In addition, in the **advanced element settings**, the **SNMP agent** must be enabled, with the following settings:

- **Port number**: The port number you will access with the device.
- **Include timeout**: This setting needs to be **disabled** to prevent unnecessary timeouts on the main connection. The timeouts on the element will still occur when the device stops sending traps.

## Usage

### Controls

The controls page contains the **Operation Status** and **Config Status** parameters.

The **DNF Timeout Time** has a range of 10s to 60s, and its default timeout duration is set to the maximum of 60s. This should be adjusted to a shorter duration if timeouts of the device do not get picked up quickly enough by the element. However, do note that this also increases the risks of false timeouts being caught if there are network connectivity issues.

### Web Interface

The device's web page. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.

## Notes

The **Config Status** parameter is dependent on the **Thomson Netprocessor 9030** protocol's **Current Config** parameter.
