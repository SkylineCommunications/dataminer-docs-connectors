---
uid: Connector_help_Digital_Alert_Systems_DASDEC-III
---


# Digital Alert Systems DASDEC-III

## About

The Digital Alert Systems DASDEC-III is a professional Emergency Alert System (EAS) decoder and encoder used by broadcasters to receive, manage, and forward emergency alerts across radio, TV, and IP networks. It handles mandatory and voluntary EAS messages and supports alert forwarding over TCP/IP networks using the EAS NET protocol.

The DASDEC-III connector integrates the device into DataMiner by acting as a smart-serial server, receiving EAS alerts pushed from the DASDEC-III over TCP/IP. It also uses SNMP for device status monitoring and HTTP for interaction with the device's web interface. Received alerts can be logged to an Elasticsearch database for historical records. Alert forwarding back to the DASDEC-III is handled securely via SCP using public-private key authentication.

## Key Features

- **EAS Alert Monitoring**: Allows you to monitor EAS alerts, including mandatory and voluntary messages, so you can easily stay informed about alert activity.
- **Alert Forwarding**: Supports secure alert forwarding back to the DASDEC-III via SCP using public-private key authentication.
- **Historical Logging**: Logs received alerts to an Elasticsearch database for historical records, enabling operators to review past alert activity.

## Use Cases

### EAS Alert Monitoring and Management

**Challenge**: Operators need to monitor and manage EAS alerts in real-time to ensure tests, duplicates, and alerts that do not apply to the coverage area do not go to air.

**Solution**: DataMiner acts as a control gate between the DASDEC-III and On-Air, receiving EAS alerts pushed from the DASDEC-III over TCP/IP. The connector allows operators to monitor alert activity, log received alerts to an Elasticsearch database for historical records, and manage alert forwarding back to the DASDEC-III securely.

**Benefit**: Operators become quickly aware of any EAS alerts, enabling them to take appropriate action in a timely manner. This ensures compliance with regulatory requirements and enhances public safety.

### Regulatory Compliance and Alert Audit Trail

**Challenge**: Broadcasters are required by regulators to maintain accurate records of all received and forwarded EAS alerts, including timestamps and alert outcomes, to demonstrate compliance during audits.

**Solution**: The DASDEC-III connector logs all received mandatory and voluntary alerts to an Elasticsearch database, capturing alert details, countdown outcomes, and forwarding status directly from DataMiner.

**Benefit**: Operators have a complete, searchable audit trail of EAS alert activity, reducing the effort required to respond to regulatory inquiries and demonstrate compliance.

### Automated Required Weekly Test (RWT) Management

**Challenge**: Broadcasters must conduct regular EAS tests (RWT) on a weekly basis to verify that the emergency alert chain is functioning correctly. Manually triggering these tests is error-prone and easy to overlook.

**Solution**: The DASDEC-III connector supports automatic RWT scheduling, triggering a test every 7 days directly from DataMiner without requiring manual intervention. Test results are visible within the DataMiner element.

**Benefit**: Ensures consistent and timely EAS testing with minimal operator involvement, reducing the risk of missed tests and keeping the broadcaster compliant with mandatory testing requirements.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Digital_Alert_Systems_DASDEC-III_Technical).
