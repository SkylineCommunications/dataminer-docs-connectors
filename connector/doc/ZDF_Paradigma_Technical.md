---
uid: Connector_help_ZDF_Paradigma_Technical
---

# ZDF Paradigma

## About

The Paradigma manages program plans as well as broadcast schedules for all live-streamed, linear programs. It also processes VPS triggers that reflect the current broadcast status of previously scheduled programs.

Paradigma provides a SOAP API for **VPS label delivery**. A VPS label is used so that a program-controlled registration (linear broadcast) can be clearly assigned and tracked throughout the entire chain — from program planning to realization. The VPS label consists of the time and the channel, meaning a program is clearly identified from start to finish and can always be assigned accurately during planning, rescheduling, cancellation, and realization. These VPS labels are stored as Events in [ZDF Bluestream Live](xref:Connector_help_ZDF_Bluestream_Live).

ZDF Paradigma acts as **middleware**, listening to VPS triggers and delivering VPS labels to Bluestream Live. Based on the VPS label, Bluestream Live executes actions upon events and responds to Paradigma. This connector creates XML results based on these actions and provides them to the end system.

## Configuration

### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

To be able to access the API, go to the **General** page of the element, and configure the **User Name** and **Password**. In addition, to be able to connect to the Paradigma API to receive EVS triggers, configure **Hostname**, **URI**, and **Port**.

## How to Use

Once the element is fully configured and running, it will automatically listen for incoming VPS triggers from the Paradigma API. Incoming message will be parsed and displayed in the dedicated parameter along with the timestamp of last received message time and status code. This allows users to monitor incoming EVS triggers in real time and verify that communication with the API is working.
