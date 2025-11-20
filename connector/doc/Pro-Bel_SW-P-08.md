---
uid: Connector_help_Pro-Bel_SW-P-08
---

# Pro-Bel SW-P-08

## About

The Pro-Bel SW-P-08 connector can be used to monitor and control any router that supports the Pro-Bel SW-P-08 protocol. A serial connection is used in order to successfully retrieve and configure the matrix. A matrix is used in order to easily connect a destination with a source.

## Key Features

- **Monitoring crosspoints**: Provides an overview of current crosspoint connections in form of Sources and Destinations.

- **Crosspoint management**: Supports setting the crosspoints, allowing the management of connections.

- **Extended support**: Supports use of extended commands, making it easy to utilize routers of any size.

### Use Case 1

**Challenge**: Managing routers from different vendors.

**Solution**: Create a dedicated element in DataMiner for all of your routers.

**Benefit**: Pro-Bel SW-P-08's implementation of generic remote control protocol allows user to interact with wide variety of devices, free from limitations of any specific vendor. On top of that, because protocol is implemented at the lowest possible level, the communication is guaranteed to be fast, responsive and light-weight, ensuring smooth operations and easy management of all of your routers.

## Technical Reference

In order to improve the performance, reliability and to future-proof the connector we are currently in the process of moving to range 2.0.0.X. As this is work in progress not all features available on the previous range are yet implemented in the new one. 

Features that are only available in the previous range are:
- Matrix view of crosspoints
- DCF support
- CSV label import/export
- Dual controller

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_technical_Pro-Bel_SW-P-08_2.0.0.X). For previous range refer to [technical documentation(1.0.0.X)](xref:Connector_technical_Pro-Bel_SW-P-08_1.0.0.X)
