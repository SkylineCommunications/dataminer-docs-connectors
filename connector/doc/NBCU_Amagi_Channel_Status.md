---
uid: Connector_help_NBCU_Amagi_Channel_Status
---

# NBCU Amagi Channel Status

## About

The **NBCU Amagi Channel Status Connector** provides real-time monitoring and status tracking of Amagi channels. It enables seamless integration with DataMiner, offering automated data retrieval and visualization of channel health states, ensuring optimal operational efficiency.

## Key Features

- **Real-time Channel Monitoring**: Continuously tracks the status of channels to provide up-to-date health information.
  
- **Automated Data Polling**: Configurable polling intervals ensure the latest data is always available.

- **Seamless HTTP Integration**: Connects to the Amagi system using secure HTTP requests to retrieve essential channel metrics.

- **User-Configurable Token Authentication**: Ensures secure access by requiring an API token during setup.

- **Detailed Channel Status Insights**: Displays critical data such as **channel name** and **agent state**, allowing for rapid issue detection.

## Use Cases

### **Use Case 1: Automated Status Reporting**

**Challenge**: Manually tracking channel health across multiple endpoints is time-consuming and inefficient.  

**Solution**: The connector automates the data retrieval process, storing real-time statuses in DataMiner for easy reporting.  

**Benefit**: Reduces manual workload and ensures accurate, up-to-date reporting on channel performance.  

### **Use Case 2: Customizable Polling for Optimized Performance**

**Challenge**: Different environments require varying levels of status update frequency, but manual adjustments are inefficient.  

**Solution**: The connector allows users to define their preferred polling intervals, optimizing data refresh rates based on specific needs.  

**Benefit**: Balances system performance with real-time monitoring requirements, ensuring efficient data handling.  

## Technical Reference

### Prerequisites

- **Amagi API Access**: A valid API token is required to authenticate HTTP requests.
- **DataMiner Platform**: Must be installed and configured to integrate with the NBCU Amagi Channel Status Connector.
- **Network Connectivity**: The system must have an active internet connection to retrieve real-time data.

> [!NOTE]  
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_NBCU_Amagi_Channel_Status_Technical).
