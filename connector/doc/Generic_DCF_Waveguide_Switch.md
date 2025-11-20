---
uid: Connector_help_Generic_DCF_Waveguide_Switch
---

# Generic DCF Waveguide Switch

This virtual connector can be used to represent a waveguide switch. The connector displays a **Position** parameter with two possible values: *Position A* and *Position B.* Operators can switch between the two positions by clicking the **Toggle Position** button.

This connector does not actually poll any data from a device. Instead it connects to an already existing element using the **Element Connections** module of DataMiner.

Multiple ranges of the connector exist in parallel to support the different position values.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main] | Initial version. Position values read/write:<br>- Position A = A<br>- Position B = B | - | - |
| 1.1.0.x [SLC Main] | Position values read/write:<br>- Position A = 1<br>- Position B = 3 | 1.0.0.1 | - |
| 1.2.0.x [SLC Main] | Position values read/write:<br>- Position A = 2<br>- Position B = 3 | 1.0.0.1 | - |
| 1.3.0.x [SLC Main] | Position values read/write:<br>- Position A = 1<br>- Position B = 2 | 1.0.0.1 | - |
| 1.4.0.x [SLC Main] | Position values read/write:<br>- Position A = 0<br>- Position B = 1 | 1.0.0.1 | - |
| 1.5.0.x [SLC Main] | Position values read:<br>- Position A = 0<br>- Position B = 1<br>Position values write:<br>- Position A = 31<br>- Position B = 32 | 1.0.0.1 | - |
| 1.6.0.x [SLC Main] | Position values read:<br>- Position A = 0<br>- Position B = 1<br>Position values write:<br>- Position A = A<br>- Position B = B | 1.0.0.1 | - |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | Yes                 | Yes                     | -                     | -                       |
| 1.1.0.x   | Yes                 | Yes                     | -                     | -                       |
| 1.2.0.x   | Yes                 | Yes                     | -                     | -                       |
| 1.3.0.x   | Yes                 | Yes                     | -                     | -                       |
| 1.4.0.x   | Yes                 | Yes                     | -                     | -                       |
| 1.5.0.x   | Yes                 | Yes                     | -                     | -                       |
| 1.6.0.x   | Yes                 | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

## How to Use

This connector is a switch controller connector. The correct connections with the actual element (the element to be managed) have to be configured in the **Element Connections** module of DataMiner.

The connector displays a **Position** parameter with two possible values: *Position A* and *Position B.* The operator can switch between the two positions by clicking the **Toggle Position** button.

## DataMiner Connectivity Framework

All ranges of the **Generic DCF Waveguide Switch** connector supports the usage of DCF.

### Interfaces

#### Fixed interfaces

Virtual fixed interfaces:

- **In_1_A**: is created to parameter **In_1_A** and interface type is **in**.
- **In_1_B**: is created to parameter **In_1_B** and interface type is **in**.
- **Out_1_A**: is created to parameter **Out_1_A** and interface type is **out**.
- **Out_1_B**: is created to parameter **Out_1_B** and interface type is **out**.

### Connections

#### Internal Connections

The connector has the following possible internal connections:

- between interface In_1_A and Out_1_A
- between interface In_1_A and Out_1_B
- between interface In_1_B and Out_1_A
- between interface In_1_B and Out_1_B
