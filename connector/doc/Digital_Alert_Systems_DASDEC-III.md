---
uid: Connector_help_Digital_Alert_Systems_DASDEC-III
---


# Digital Alert Systems DASDEC-III

## About

The Digital Alert Systems DASDEC-III is a professional Emergency Alert System (EAS) encoder/decoder used by FCC-licensed TV and radio broadcasters to receive, decode, and forward mandatory and voluntary emergency alerts, including Required Monthly Tests (RMT), Required Weekly Tests (RWT), Amber Alerts, and severe weather warnings. The DASDEC-III connector integrates the device into DataMiner over EAS-NET (TCP), SSH/SCP, HTTP, and SNMP, giving operators a unified place to review incoming alerts, enforce FCC compliance deadlines, and maintain a complete, searchable audit trail — without logging into the DASDEC device directly.

## Key Features

- **Alert Triage and Operator Decision Control:**: Presents incoming EAS alerts in DataMiner categorized as mandatory or voluntary, and lets operators approve, hold, deny, or ignore each alert from the DataMiner interface, eliminating the need to interact with the DASDEC device's web interface.
- **Automated Compliance Safeguards**: Starts a countdown timer when a mandatory alert such as an RMT arrives and automatically forwards the alert to the DASDEC-III before the FCC deadline expires, ensuring compliance even when no operator is available to act.
- **Compliance Deadline Tracking**: Exposes RMT and RWT countdown parameters that feed the DataMiner Alarm Console with escalating severity alarms as deadlines approach, replacing manual checks and email-based reminders with automated alarm escalation.
- **Complete EAS Audit Trail:**: Logs every alert event and operator action — with the DataMiner username, timestamp, and outcome — to the indexing database or a local file path, producing the searchable record that FCC audits require.
- **Connection Health Monitoring**:  Raises a DataMiner alarm when no EAS-NET message is received within a configurable time window, alerting operators to potential communication issues with the DASDEC-III before a missed alert creates a compliance risk.

## Use Cases

### Preventing EAS Alerts from Interrupting Paid Programming

**Challenge**: Broadcasters using the DASDEC-III for voluntary alert forwarding face unpredictable on-air interruptions. Non-critical EAS alerts — such as coastal flood advisories or winter storm watches — can go to air automatically over paid advertising spots. When that happens, the station typically owes a make-good, returning the revenue from that spot. Mandatory alert types, by contrast, carry strict FCC time windows that cannot be missed.

**Solution**: The connector receives every incoming EAS-NET alert and holds voluntary alerts in a pending queue surfaced in the DataMiner Alarm Console, where operators can approve or deny each one before it reaches air. Mandatory alerts, such as RMT messages, receive a built-in countdown and are automatically forwarded by the DataMiner element if the operator has not acted before the FCC deadline. The DASDEC-III can be configured to bypass the DataMiner queue entirely for specific alert types — tornado warnings and Emergency Action Notifications, for example — so those forward to air immediately regardless of DataMiner state.

**Benefit**: Operators control the timing of voluntary alerts to protect high-value programming and advertising spots. Mandatory alerts always meet their FCC deadlines, with or without operator intervention.

### Replacing Manual FCC Compliance Logging

**Challenge**: FCC-licensed broadcasters must maintain records of all received and forwarded EAS alerts — including alert type, timestamp, and how each alert was handled — to demonstrate compliance during regulatory audits. At many stations, this record is built manually from DASDEC-generated email notifications copied into spreadsheets, a process that is inconsistent, time-consuming, and difficult to maintain across multiple stations or call signs.

**Solution**: The connector logs every alert event and operator action automatically as alerts move through the DataMiner element. Each log entry captures the DataMiner username of the operator who acted, the timestamp, and the full alert payload. System-initiated actions — such as auto-forwarding an alert before its deadline — are logged under a separate system identity so they are distinguishable from human decisions. Logs can be stored on the DataMiner Agent, written to a network file path, or offloaded to Elasticsearch/OpenSearch with configurable retention. DataMiner's scheduling and reporting tools can generate PDF summaries on a recurring schedule and distribute them by email.

**Benefit**: Stations replace email tracking and manual spreadsheet entries with an automatic, structured log that grows with every alert event. Responding to an FCC audit request becomes a database query rather than a manual document assembly task.

### Automating Required Weekly Test Management

**Challenge**: FCC regulations require broadcasters to conduct a Required Weekly Test (RWT) every seven days — unless a qualifying EAS alert has already aired within that period, in which case the test can be skipped. Tracking this window manually across multiple DASDEC units and station call signs creates scheduling complexity and leaves stations exposed to missed tests or unnecessary ones run in error.

**Solution**: The connector maintains two countdown parameters: time since the last RWT was run, and time since any qualifying alert aired. Operators configure which countdown drives automatic test execution. When the selected countdown reaches zero, the DataMiner element sends an RWT command directly to the DASDEC-III via SSH/SCP without requiring any operator action. Stations that configure the "last alert aired" countdown source benefit from intelligent test suppression: the connector skips the weekly test automatically when FCC rules permit, because a recent alert already satisfies the requirement.

**Benefit**: Weekly test compliance runs without manual scheduling or operator action. Stations that see frequent alert activity avoid running redundant tests, reducing unnecessary interruptions to programming.

## Technical Reference

### Prerequisites
 - **EAS-NET connectivity**: Network access between the DataMiner Agent and the DASDEC-III on the EAS-NET TCP port is required for alert reception in DataMiner.
 - **SSH/SCP connectivity**: The DataMiner Agent must reach the DASDEC-III over SSH to send alert forwarding commands. An SSH key pair must be generated within the connector and installed on the DASDEC-III during initial setup.
 - **DASDEC software**: The DASDEC-III running v5 software with EAS-NET and Plus Package licenses is required.
 - **SNMP aux pass package (optional)**: Basic device health monitoring via SNMP requires the aux pass package to be installed on the DASDEC unit.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Digital_Alert_Systems_DASDEC-III_Technical).
