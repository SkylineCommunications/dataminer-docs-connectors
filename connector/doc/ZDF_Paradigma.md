---
uid: Connector_help_ZDF_Paradigma
---

# ZDF Paradigma

The Paradigma manages program plans as well as broadcast schedules for all live-streamed, linear programs. It also processes VPS triggers that reflect the current broadcast status of previously scheduled programs.

Paradigma provides a SOAP API for **VPS label delivery**. A VPS label is used so that a program-controlled registration (linear broadcast) can be clearly assigned and tracked throughout the entire chain — from program planning to realization. The VPS label consists of the time and the channel, meaning a program is clearly identified from start to finish and can always be assigned accurately during planning, rescheduling, cancellation, and realization. These VPS labels are stored as Events in [ZDF Bluestream Live](xref:Connector_help_ZDF_Bluestream_Live).

ZDF Paradigma acts as **middleware**, listening to VPS triggers and delivering VPS labels to Bluestream Live. Based on the VPS label, Bluestream Live executes actions upon events and responds to Paradigma, where we create XML results based on these actions and provide them to the end system.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Initialization

On the **General** page, configure the **User Name** and **Password** to be able to access the API. Next to User Name and Password, we need to configure **Hostname**, **URI** and **Port** to be able to connect to the Paradigma API for receiving EVS triggers.

