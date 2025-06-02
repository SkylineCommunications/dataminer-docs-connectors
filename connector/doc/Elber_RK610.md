---
uid: Connector_help_Elber_RK610
---

# Elber RK610

## About

The Elber Cleber (RK610) connector offers a powerful, flexible, and modular hardware and software platform for broadcasting and contribution networks where users can install up to six boards with no limitation in terms of position or number.

This connector exports connectors of type RFSW04A and RFSW CU 06 and creates elements for each card in its chassis. Data is polled via **SNMP** and traps are used.

### Version Info

| Range              | Description                                                  | DCF Integration | Cassandra Compliant |
|--------------------|--------------------------------------------------------------|-----------------|---------------------|
| 1.0.0.x            | Initial version                                              | No              | Yes                 |
| 1.0.1.x            | Update DVE removal mechanism                                 | No              | Yes                 |
| 1.0.2.x [SLC Main] | Refactoring of code. Addition of support to RFSW CU 06 card. | No              | Yes                 |

### Exported connectors

| Exported Connector                   | Description                     |
|--------------------------------------|---------------------------------|
| Elber RK610 - Elber RK610 RFSW04     | Used for the RFSW04A module.    |
| Elber RK610 - Elber RK610 RFSW_CU_06 | Used for the RFSW CU 06 module. |

## Configuration

### Connections

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device, e.g. *10.10.15.1*.

SNMP Settings:

- **Port number**: The port of the connected device, by default: *161*.
- **Get community string**: The community string used when reading values from the device, by default: *public*.
- **Set community string**: The community string used when setting values on the device, by default: *private*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use - Range  1.0.2.X

#### Modules

This page contains the **Modules Info** Table. This table contains all the cards and offers the ability to display these cards or make them invisible. When modules are no longer available, these rows will be marked as deleted, and the **Delete** button will be enabled in the **Modules Info** table. A toggle button is also available to auto-delete these DVEs.

#### Controller

This page contains the parameters for the controller. This page is divided in the **status** parameters, the **alarm** parameters, the **configuration** parameters, and the **network configuration** parameters, e.g. PSU 1 Voltage, Date Time, IP Address, etc.

#### RFSW04

This page contains all the available information about the RFSW04 cards. This page will only be available if any RFSW04 cards are available.

#### RFSW CU 06

This page contains configuration, status, and alarm information for the RFSW CU 06 cards. This page will only be available if any RFSW CU 06 cards are available.

#### RFSW CU 06 ESSPx

This page contains configuration, status, and alarm information for the ESSPx on RFSW CU 06 cards. This page will only be available if any RFSW CU 06 cards are available.

#### SNMP

This page contains the general and SNMP parameters, e.g. **Customer Name**, **Customer Location**, etc.

## How to Use - Range 1.0.1.x and Older

### Modules

This page contains the **Modules Info** Table. This table contains all the cards and offers the ability to display these cards or make them invisible. The page button **Modules \[DEL\]** contains a table with the cards that have been removed from the chassis. In case a card broke and has to be removed from the chassis, then this card is moved to this table. When a new card of the same type is plugged in, then this will move back. This ensures that trending/alarm history is not deleted. If you do not want to keep this histor,y you can delete this card in the **Modules Info \[DEL\]** table.

From 1.0.1.x onwards, the **Modules \[DEL\]** table is removed, and this logic is transferred to the **Modules Info** table. When modules are no longer available, these rows will be marked as deleted, and the **Delete** button will be enabled. A toggle button is also available to auto-delete these DVEs.

### General

This page contains the general parameters, e.g. **Customer Name**, **Customer Location**, etc.

### Controller

This page contains the parameters for the controller. This page is divided in the **status** parameters, the **alarm** parameters, the **configuration** parameters, and the **network configuration** parameters, e.g. Controller Status PSU 1 Voltage, Controller Config Date Time, Controller Config Network Ip Address, etc.

### Traps

This page lists all the traps.
