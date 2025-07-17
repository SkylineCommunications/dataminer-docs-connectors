---
uid: Connector_help_Evertz_Magnum_SDVN_Router
---

# Evertz Magnum SDVN Router

The Evertz Magnum SDVN Router connector for DataMiner provides deep integration with the Evertz Magnum control system, enabling operators to manage video and audio routing across distributed matrix configurations. By bridging serial and HTTP-based communication, the connector enables end-to-end routing control, nameset visualization, and system feedback directly from the DataMiner platform.

## Key Features

- **Crosspoint Management**: Execute source-to-destination routing with support for locking, notes, and Quartz mapping.

- **OAuth2 & Credential Authentication**: Support for secure login using either Authorization Code or Client Credentials.

- **Nameset & Salvo Retrieval**: Display up to 5 namesets and retrieve salvos configured in the Magnum application.

## Use Cases

### Unified Control of Distributed Matrices

**Challenge**:Using hardware router panels or Magnum's native UI may be too technical or unfamiliar to broadcast operators.

**Solution**: Expose only the required sources, destinations, and salvos in the DataMiner interface with intuitive labeling, view filtering, and nameset grouping.

**Benefit**: Lower learning curve and improved operator confidence with tailored views.

### Simplified Operator Training and Workflow

**Challenge**: Managing transitions between incoming contribution feeds and outgoing distribution channels across multiple locations requires manual configuration, which is slow and error-prone.

**Solution**: Use the connector’s Flow Engineering interface to visualize and manage connections between incoming and outgoing flows. InterApp messaging ensures real-time updates and logic tracking.

**Benefit**: Streamlined flow control, less human error, and improved responsiveness during live broadcast operations.

### Audio Breakaway Routing

**Challenge**: Routing video and audio signals independently or in quad-channel groupings is difficult in generic control systems.

**Solution**: The connector supports breakaway mode and configurable channel counts, with full Quartz mapping compatibility.

**Benefit**: Simplifies complex audio routing tasks and aligns perfectly with multi-channel workflows.

## Technical info

> [!NOTE]
> For more information on how to configure and use the DataMiner connector for Evertz Magnum SDVN Router, refer to the [Technical help page](xref:Connector_help_Evertz_Magnum_SDVN_Router_Technical).
