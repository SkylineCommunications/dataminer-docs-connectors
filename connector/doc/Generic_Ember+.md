---
uid: Connector_help_Generic_Ember+
---

# Generic Ember+

## About

The Ember+ protocol has been designed to allow communication between two endpoints, one being the data provider and the other being the consumer. The data provider usually is a piece of hardware that offers a set of controllable parameters, while the consumer may be a control or monitoring system that provides access to these parameters and allows users to control them.

The Generic Ember+ connector, which acts as the consumer, is designed to allow monitoring of parameters that are provided via the Ember+ protocol irrespective of the specific device type.

## Key Features

- **Parameters:** Displays all the parameters that are exposed through the Ember+ tree.

## Use Case

**Challenge:** Most of the available DataMiner Ember+ connectors are designed to be used for a specific device. This requires the development of a specific connector for each device with its own alarm and trend templates.

**Solution:** This connector can be used to monitor the parameters of any device that supports the Ember+ protocol.

**Benefit:** Monitor all devices that support the Ember+ protocol using the same protocol and alarm and trend templates.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Generic_Ember%2B_Technical).
