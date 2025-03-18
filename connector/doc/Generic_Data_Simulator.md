---
uid: Connector_Generic_Data_Simulator
keywords: simulator, data simulator
---

# Generic Data Simulator

## About

The **Generic Data Simulator** is a DataMiner connector designed to simulate any type of data with configurable trending capabilities. It allows users to generate artificial data streams that mimic real-world conditions, making it useful for testing, development, and training purposes. The simulator can be configured to produce static, random, or trending values over time, providing flexibility for various use cases.

## Key Features (1.0.0.X)

- **CPU and network interfaces simulations**: Simulating 4 network interfaces and CPU load (only on 1.0.0.X branch)

## Key Features (2.0.0.X)

- **Numeric parameter simulation**: Simulating different types of trends for numeric parameters.
- **String parameter simulation**: Static simulation of textual parameters.
- **Parameter classification**: Option of assigning fully customizable categories to parameters.

## Use Cases

Easy way to simulate all sorts of parameters, trends and polling rates makes this connector very useful for all sorts of use cases such as:
- IoT device simulation
- Various management services with lots of KPIs (fleet management, smart city management, etc.)
- Broadcast and Media monitoring
- API simulation

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_Generic_Data_Simulator_Technical).