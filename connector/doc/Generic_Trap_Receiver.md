---
uid: Connector_help_Generic_Trap_Receiver
---

# Generic Trap Receiver

## About

The **Generic Trap Receiver** is a tool used to capture and display SNMP traps for a specific IP addresses.
The overview of the captured traps will be displayed in the **Traps** table alongside **Traps Number**, which captures the number of traps on the table. Information like **Source IP**, **Trap OID**, and 20 different **Bindings** are available for display for each trap in the **Traps** table.


![Generic Trap Receiver Overview](~/connector/images/GenericTrapReceiver_Overview.png)

## Key Features

- **Displays Traps**: Displays traps coming from the configurable parameter **Trap IP Sources**
- **Create Information Events**: By Enabling the **Information Events** parameter, it creates an Information Event on the DMA for every trap received. 
- **Lookup Table**: Be able to configure incoming trap OIDs and replace them with an alias names. For this purpose, the parameter Lookup Table State must be enabled.

## Technical info

> [!NOTE]
> The complete list of supported modules and additional technical details are available on the [Technical help page](xref:Connector_help_Generic_Trap_Receiver_Technical).