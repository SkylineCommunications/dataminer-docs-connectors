---
uid: Connector_help_Generic_Trap_Receiver
---

# Generic Trap Receiver

## About

The **Generic Trap Receiver** is a tool used to capture and display SNMP traps for a specific IP address. The overview of the captured traps will be displayed in the **Traps** table alongside the **Traps Number**, which shows the number of traps in the table. Information like **Source IP**, **Trap OID**, and 20 different **bindings** are available for display for each trap in the Traps table.

![Generic Trap Receiver Overview](~/connector/images/GenericTrapReceiver_Overview.png)

## Key Features

- **Displays Traps**: Displays traps coming from the configurable parameter **Trap IP Sources**.
- **Create Information Events**: If you enable the **Information Events** parameter, an information event will be created on the DMA for every trap received.
- **Lookup Table**: If the **Lookup Table State** parameter is enabled, you can configure incoming trap OIDs and replace them with alias names.

## Technical info

> [!NOTE]
> For detailed technical information, refer to the [Technical help page](xref:Connector_help_Generic_Trap_Receiver_Technical).

