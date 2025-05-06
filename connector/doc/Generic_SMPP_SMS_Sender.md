---
uid: Connector_help_Generic_SMPP_SMS_Sender
---

# Generic SMPP SMS Sender

## About

This connector is used to set up a (TCP/IP) connection with an SMS Center using the open, industry-standard Short Message Peer to Peer Protocol (**SMPP v3.4**). In this setup, DataMiner acts as the **ESME** (External Short Message Entity). DataMiner acts as the ESME, sending and receiving SMS messages via the SMSC, which forwards outgoing messages to their destination and routes incoming ones back to DataMiner.

As such, this connector can be used to interface with any SMS Center that supports and is based on the standard SMPP specification v3.4.

## Key Features

- **Sending Messages**: Allows users to send SMS messages to specified destination numbers.
- **Receiving Messages**: Supports receiving incoming SMS messages from the SMSC.


## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation page](xref:Connector_help_Generic_SMPP_SMS_Sender_Technical).