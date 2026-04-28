---
uid: Connector_help_Generic_sFlow_Agent
---

# Generic sFlow Agent

## About

The purpose of this connector is to analyze the information received via **sFlow** packets to give network operators a better understanding of the flows of **data crossing the network**.

**Every minute**, the connector reads the files from the **Collector connector**. It then processes these packets and writes the information to a table.

## Installation and configuration

### Creation

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: Agent IP.

SNMP Settings:

- **Port number**: 161
- **Get community string**: public
- **Set community string**: private

## Usage

### Flows Overview

This is the **default page** of the connector. It contains the **Flows Table**, which contains all the **sflow packets** for a user-specified period of time.
