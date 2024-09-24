---
uid: Connector_help_Verizon_WM_DCAT
---

# Verizon WM DCAT

This connector is intended to handle the Verizon Circuit Acceptance (DCAT) workflow. The solution consists of user-driven and DWS-driven tests against VSAT circuits with the purpose of determining if the target entities have the expected performance behavior. The tests are based on predefined profiles, which contain the list metrics and their values to be considered during DCAT iterations.

## About

### Version Info

| Range              | Key Features                                                               | Based on | System Impact |
|--------------------|----------------------------------------------------------------------------|----------|---------------|
| 1.0.0.x            | Initial version.                                                           | -        | -             |
| 1.0.1.x            | Updated minimum DataMiner version to 10.0.10.0 - 9454.                     | 1.0.0.12 | -             |
| 1.0.2.x [SLC Main] | Session ID columns removed from all tables. UI migrated from Visio to LCA. | 1.0.1.8  | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | N/A                    |
| 1.0.1.x   | N/A                    |

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|--|--|--|--|--|
| 1.0.0.x | No | Yes | Automation Scripts: <br>- Verizon DCAT OnAccept <br>- Verizon DCAT OnAcceptExecute <br>- Verizon DCAT OnExecute <br>- Verizon DCAT OnResult <br>- Verizon DCAT OnScheduledExecute <br>- Verizon DCAT OnScheduledExecuteReport <br>Visio file: <br>DM Tools <br>Report template: <br>VRZ RDS DCAT | - |
| 1.0.1.x | No | Yes | Automation Scripts: <br>- Verizon DCAT OnAccept <br>- Verizon DCAT OnAcceptExecute <br>- Verizon DCAT OnExecute <br>- Verizon DCAT OnResult <br>- Verizon DCAT OnScheduledExecute <br>- Verizon DCAT OnScheduledExecuteReport <br>Visio file: <br>DM Tools <br>Report template: <br>VRZ RDS DCAT | - |
| 1.0.2.x | No | Yes | Automation Scripts: <br>- Verizon DCAT OnAccept <br>- Verizon DCAT OnAcceptExecute <br>- Verizon DCAT OnExecute <br>- Verizon DCAT OnResult <br>- Verizon DCAT OnScheduledExecute <br>- Verizon DCAT OnScheduledExecuteReport <br>LCA: <br>- DCAT | - |

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

This connector uses a configuration page that should be set up in order to work with the workflows.

- Report Settings:

  - **DMA Endpoint**: The base URL for the generated report.
  - **Report Endpoint**: The query parameters to append to the DMA endpoint in order to use the report template.
  - **Email List**: Semicolon-separated (;) list of email addresses where the scheduled report will be sent if this is enabled.

- DCAT Settings:

  - **Archive Export Path**: The local path where the DCAT history and DCAT entity history will be offloaded into files.
  - **DCAT Live and DCAT History Aggregated Retention**: Indicates how long the entries remain in the DCAT Live and DCAT History Aggregated tables before they are cleaned up.
  - **DCAT History Retention**: Indicates how long the entries remain in the DCAT History before they are offloaded.
  - **DCAT File Retention**: Indicates how long the entries remain in the offload file before they are cleaned up.

- System Credentials:

  - **System Username**: The system username used to perform API requests to DataMiner, used by the report template.
  - **System Password**: The system password used to perform API requests to DataMiner, used by the report template.

- Topology Import Settings

  - **Topology Import Path**: The path from where the topology configuration file will be imported.
  - **Topology Import Interval**: Indicates how often the topology configuration file will be imported.

> [!NOTE]
> A **Verizon Reports and Dashboards Solution** element has to be available in the DMS, and it needs to be called "RDS_01". Only then will the DCAT Tool be able to retrieve all profiles. This does not mean that no other elements using the same connector can be created, as there can be multiple RDS elements in the environment.

### Automation Scripts

- **Verizon DCAT OnAccept**: This script is triggered by the acceptance button on live reports, parses the information of a circuit, and passes it to the WM DCAT connector in order to update the DCAT Acceptance Status of the circuit.
- **Verizon DCAT OnAcceptExecute**: This script is triggered by the acceptance workflow from the DM Tools visual overview. It parses the information for the acceptance execution (circuits) and passes it to WM DCAT to change the acceptance status of the selected circuits.
- **Verizon DCAT OnExecute**: This script is triggered by the live workflow from the DM Tools visual overview. It parses the information for the live execution (circuits, range of dates, report format, profile, metrics, and faults) and passes it to WM DCAT to perform the profile metric and fault validation for every circuit and generate the report.
- **Verizon DCAT OnResult**: This script is triggered by the history workflow from the DM Tools visual overview. It parses the information for the history execution (circuits, range of dates, and report format) and passes it to WM DCAT to retrieve all previous live executions depending on the range of dates.
- **Verizon DCAT OnScheduledExecute**: This script needs to be triggered via DataMiner Scheduler, which will need to be configured. The script passes blank data to WM DCAT to retrieve new and unprocessed circuits to perform a live execution with a default profile. It generates a report with the results of all validated circuits.
- **Verizon DCAT OnScheduledExecuteReport**: This script is triggered by the Verizon DCAT OnScheduledExecute script. It parses the information of the generated report and sends it by email to the configured email list.

### Low-Code App

- **DCAT**: This app allows users to perform the live and history execution. In addition, circuits can be grouped by NMS, customer, or individual circuit, and users can configure a range of dates for the validation, the report format, the profile, and selected metrics and faults. The low-code app will allow users to trigger the necessary Automation scripts to perform the workflows.

## How to use

The Verizon WM DCAT connector is meant to be used as a way to check the results and history of circuit analysis from the DCAT low-code app.

From the DCAT app, circuits are selected for which the analysis should be run. Once the analysis is complete, entries will be added to the DCAT Live and DCAT History tables.

The **DCAT History** table contains entries that display when each report was executed. It is a more condensed version of the **DCAT Live** table, which contains the same information including the results of the analysis.

There is also a configuration page with **Report Settings** and **DCAT Settings**.

- Under Report Settings, two parameters, **DMA and Report Endpoint**, can be configured, which serve as the final URL for the report displaying the results.
- Under DCAT Settings, you can configure the **DCAT Live and DCAT History Aggregated Retention** parameter, which determines how long rows should be kept in the DCAT Live and DCAT History Aggregated tables, as well as the **DCAT History Retention** parameter, which determines how long rows should be kept in the DCAT History and DCAT Entity History tables.
