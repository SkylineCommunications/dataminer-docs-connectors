---
uid: Connector_help_Newtec_Dialog_Local_Infrastructure_Host
---


# Newtec Dialog Local Infrastructure - Host

Newtec Dialog Local Infrastructure is software that monitors numerous PDU device parameters of a network.

## About

This is an **HTTP** connector that connects to the Zabbix API to retrieve data from the Zabbix platform. The Zabbix API is a web-based API and is shipped as part of the web front end. It uses the JSON-RPC 2.0 protocol. This connector is created by the **Newtec Dialog Local Infrastructure** connector. For more information on the device, refer to <https://www.zabbix.com/documentation/3.0/manual/api>.

## Installation and configuration

### Creation

The element using this protocol is **automatically created** by the parent connector (Newtec Dialog Local Infrastructure). The name of the element consists of the name of the parent connector + host.

### Configuration

To be able to retrieve data from the API, the **Username, Password** and **URL** must be provided on the Configuration page of the parent element.

## Usage

### General

This page displays information about the host.

### PDU

This page displays all the **PDU information** that occurs on the current host.