---
uid: Connector_help_DNF_Controls_USP-8D
---

# DNF Controls USP-8D

The **DNF Controls USP-8D** can be configured by and can configure the DNF Controls USP-8D **Control Console**.

## About

The DNF Controls USP-8D connector is polled by the DNF Controls USP-8D Control Console.
Since the latter device cannot be accessed by SNMP, the device polls the element instead of the other way around.
Sets can be performed from the connector, and will be updated, depending on the interval between gets on the Control Console.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|------------------|-----------------|---------------------|-------------------------|
| 1.0.0.x          | Initial version | No                  | Yes                     |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | V 2.2                       |

## Installation and configuration

### Creation

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

### Configuration of ...

It is, however required to enable the **SNMP Agent** in **Advanced element settings** in the **edit** menu.

- Virtual IP Address - The IP address you will access with the device.
- Subnet Mask - The subnet mask for this IP

## Usage

### Controls

The controls page contains the **Operation Status** and **Config Status** parameters.

The DNF Timeout Time has a range of 10s to 60s and its default timeout duration is set to the maximum of 60s. This should be adjusted to a shorter duration if timeouts of the device are not being picked up by the element quickly enough. However, do note that this also increases the risks of false timeouts being caught if there are network connectivity issues.

### Web Interface

The device's web page. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.

## Notes

The **Config Status** parameter is dependent on the **Thomson Netprocessor 9030** protocol's **Current Config** parameter.
