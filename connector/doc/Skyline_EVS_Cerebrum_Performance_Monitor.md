---
uid: Connector_help_Skyline_EVS_Cerebrum_Performance_Monitor
---

# Skyline EVS Cerebrum Performance Monitor

This virtual connector enables users to perform a speed test on an EVS Cerebrum element, assessing its connection performance. It provides insights into how quickly the system establishes connections.

## About

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | EVS Cerebrum      | -                   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

## How to use

1. Set up the **test parameters**:

   1. Navigate to the **General** page.

   1. Enter the **element ID** of the EVS Cerebrum element you want to test.

   1. Configure additional test parameters, such as:

       - **Duration**: Specify how long the test should run.
       - **Iterations**: Define the number of test cycles.

1. Select **crosspoints** for testing:

   1. Go to the **Crosspoints** page.

   1. Right-click the **Crosspoints Table** and select **Add**.

   1. Ensure that the crosspoint values exactly match those in the **Routes** table of the Cerebrum element specified earlier.

   1. Use the enable/disable options to choose which crosspoints will be active during the test.

1. Run the **test**:

   1. Go back to the **General** page.

   1. Click the **Start** button to begin the performance test.

1. Monitor the **results**:

   - During the test, intermediate results are added to the **Metrics Table** after each iteration. These include:

     - Average Time
     - Minimum Time
     - Maximum Time

   - Once the test is completed, a final summary will display the overall average, minimum, and maximum times for creating a new crosspoint on the Cerebrum.

A simple performance setup can for example look like this:

- General

  - DataMiner Element ID: 305/450
  - Test Cycle Duration: 60s
  - Number of Test Cycles: 3
  - Time between Test Cycles: 15s
  - Crosspoint Set Mode: Single
  - Number of Crosspoints Per Take: 3

- Crosspoints:

  | Instance            | Device Name    | Source Name | Source Level | Destination Name | Destination Level Name | Levels      | Park ID | Enabled |
  |---------------------|----------------|-------------|--------------|------------------|------------------------|-------------|---------|---------|
  | 0.0.0.0-ROUTER-14-1 | 0.0.0.0-ROUTER | MCM-05      | Video        | SNP C5           | Video                  | Video;Video | MCM-01  | Enabled |
  | 0.0.0.0-ROUTER-15-1 | 0.0.0.0-ROUTER | MCM-06      | Video        | SNP C6           | Video                  | Video;Video | MCM-01  | Enabled |
  | 0.0.0.0-ROUTER-16-1 | 0.0.0.0-ROUTER | MCM-07      | Video        | SNP C7           | Video                  | Video;Video | MCM-01  | Enabled |
