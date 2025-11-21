---
uid: Connector_help_Pro-Bel_SW-P-08
---

# Pro-Bel SW-P-08

## About

The Pro-Bel SW-P-08 connector can be used to monitor and control any router that supports the Pro-Bel SW-P-08 protocol. A serial connection is used in order to successfully retrieve and configure the matrix. A matrix is used in order to easily connect a destination with a source.

## Key Features

- **Monitoring crosspoints**: Provides an overview of current crosspoint connections in the form of sources and destinations.

- **Crosspoint management**: Allows you to manage connections by setting crosspoints.

- **Extended support**: Supports the use of extended commands, making it easy to utilize routers of any size.

### Use Case

**Challenge**: Managing routers from different vendors.

**Solution**: Create a dedicated element in DataMiner for all your routers.

**Benefit**: Pro-Bel SW-P-08's implementation of generic remote control protocol allows you to interact with wide variety of devices, free from limitations of any specific vendor. On top of that, because the protocol is implemented at the lowest possible level, the communication is guaranteed to be fast, responsive and lightweight, ensuring smooth operations and easy management of all of your routers.

## Prerequisites

The minimum required DataMiner version for range 2.0.0.x of this connector is **10.3.0**.

## Technical Reference

This connector has two ranges: 1.0.0.x and 2.0.0.x. The 2.0.0.x range is currently still being developed. It will improve the performance and reliability of the connector and make it more future-proof. However, not all features from the 1.0.0.x range are currently already available in the 2.0.0.x range.

At present, the following features are only available in the 1.0.0.x range:

- Matrix view of crosspoints
- DCF support
- CSV label import/export
- Dual controller

> [!NOTE]
> For detailed technical information about the 2.0.0.x range, refer to our [technical documentation (2.0.0.x)](xref:Connector_technical_Pro-Bel_SW-P-08_2.0.0.X). For the 1.0.0.x range, refer to the [technical documentation (1.0.0.x)](xref:Connector_technical_Pro-Bel_SW-P-08_1.0.0.X).
