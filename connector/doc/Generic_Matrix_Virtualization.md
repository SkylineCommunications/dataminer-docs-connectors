---
uid: Generic_Matrix_Virtualization
---

# Generic Matrix Virtualization

## About

The Generic Matrix Virtualization connector makes it possible to visualize multiple matrices in a single (virtual) matrix, so that you can abstract low-level matrices into one matrix.

## Key Features

- **Matrix Abstraction**: Combines multiple physical matrices into a single virtual routing matrix.

- **Concatenation Support**: Maps and joins inputs/outputs from various matrices to form an extended matrix.

- **Tie-Line Handling**: Manages internal and inter-matrix connections with automated failover and status reporting.

- **DCF Integration**: Supports the DataMiner Connectivity Framework To read out Processing Unit connectivity.

## Use Cases

### Use Case 1

**Challenge**: An operator needs to control and route across several physical matrices (SDI and IP) from different vendors as one logical unit.

**Solution**: Using the Generic Matrix Virtualization connector, a unified virtual matrix is created over multiple physical ones.

**Benefit**: Reduced complexity and increased routing flexibility.

### Use Case 2

**Challenge**: Tie lines between matrices must be optimized to ensure redundancy and performance.

**Solution**: Tie-line configuration and prioritization are handled automatically by the connector, with fallback strategies in place.

**Benefit**: Increased reliability and smarter routing decisions in complex deployments.

## Technical Reference

### Prerequisites

- **DataMiner version 8.5.4 or higher** is required for compatibility.


> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Generic_Matrix_Virtualization_Technical).