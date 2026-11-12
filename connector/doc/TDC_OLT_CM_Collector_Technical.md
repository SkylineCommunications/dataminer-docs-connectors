---
uid: Connector_help_TDC_OLT_CM_Collector_Technical
---

# TDC OLT CM Collector

## About

The **TDC OLT CM Collector** uses SNMP to collect cable-modem and DOCSIS channel data from cable modems and Huawei MA5800-MA5633 equipment. The [TDC CPE Manager](xref:Connector_help_TDC_CPE_Manager) brings the data together and provides the operator interface.

The instructions and defaults below apply to the **1.1.0.x main branch** of the connector. Use the CPE Manager for day-to-day monitoring and configuration; the collector's data pages are not intended for routine operator use.

## Configuration

### Connections

The connector uses two SNMPv2 connections. Set the loopback address in both connection fields when creating the element; provisioning and polling supply the actual device addresses.

#### SNMP Connection - Main

Use this connection for cable-modem collection. Enter these values when you create the element:

- **IP address/host**: `127.0.0.1`. This is a placeholder, not a cable-modem address.
- **Port number**: The SNMP port, default *161*.
- **Get community string**: The SNMP read community for the deployment, default *public*.
- **Set community string**: Default *private*. This setting is not used for the documented data-collection workflow.

#### SNMP Connection - CMTS

Use this connection for OLT/CMTS collection. Enter these values when you create the element:

- **IP address/host**: `127.0.0.1`. This is a placeholder, not an OLT/CMTS address.
- **Port number**: The SNMP port, default *161*.
- **Get community string**: The SNMP read community for the deployment, default *public*.
- **Set community string**: Default *private*. This setting is not used for the documented data-collection workflow.

### Initialization

After creating the collector, configure provisioning through the CPE Manager:

1. Associate the collector with the appropriate CPE backend manager.

2. Configure access to the IAM provisioning database through the CPE Manager.

   The collector uses **Provisioning DB Name**, **Provisioning DB Server**, **Provisioning DB Username**, and **Provisioning DB Password**.

3. Run full provisioning for the collector.

   This loads the assigned cable modems and retrieves the associated **OLT Name** from the provisioning data.

4. Confirm that the expected modems have been provisioned and that **OLT Name** is populated.

> [!IMPORTANT]
> Complete full provisioning before enabling CM offload. The collector cancels an offload attempt if **OLT Name** is empty because it uses this value to organize the output files.

## How to Use

### Monitor Modems and Channels

Use the CPE Manager to access the collected data. The collector combines modem information, such as registration status and reachability, with downstream and upstream channel measurements.

You can collect data for QAM downstream, QAM upstream, OFDM downstream, and OFDMA upstream channels. The measurements available for each modem depend on its capabilities and the data exposed by the equipment.

### Configure CM Offload

CM offload saves selected measurements as CSV files. Set it up through the CPE Manager or **multiple set**; you do not need to use the collector's data pages.

1. Choose an output folder and enter it in **CM Offload Directory**.

   This can be a local directory on the DataMiner Agent or a network share. The collector creates a subfolder named after **OLT Name**. Set the path for your deployment; the connector does not define a default.

2. If you use a network share, configure **PNM Share Username** and **PNM Share Password**.

   Use the `DOMAIN\USERNAME` format if needed. The account must be able to create and write files in the destination, and delete them if cleanup is enabled.

3. Configure the export columns for the required datasets as described under [Select Export Columns](#select-export-columns).

4. Set **File Age Threshold** to the required retention period.

   Choose a value from *8* to *8760 hours*, in *8-hour* increments. The default is *360 hours* (*15 days*).

5. Set **Cleanup State** to *Enabled* if the collector should remove expired CSV files.

   The default is *Disabled*. Check the effective value after you apply the CPE Manager settings.

6. Set **CM Offload State** to *Enabled*.

   The default is *Disabled*. Offload runs every *15 minutes* after a randomized initial delay.

7. Check **CM Offload Status** and verify that new files appear in the OLT subfolder.

   The status is *OK*, *OK with errors*, or *Fail*. If files are missing or the status shows an error, check the element log.

To start an export immediately, select **Force Offload**. This works even when **CM Offload State** is disabled, but still requires a valid OLT name, output folder, and export configuration. If **Cleanup State** is enabled, cleanup runs during a forced export too.

#### Select Export Columns

Enter a comma-separated list of column names in each configuration string. Use the column names from the connector, without any parenthesized table name. Parameter IDs and renamed information-template labels are not supported. Match the names' spelling and capitalization.

For example, **CM Config String** can contain:

```text
Last Successful Poll,IP,Registration Status Group,CM Uptime
```

The primary key is always the first output column. The connector ignores unrecognized column names, so check the generated header after changing a configuration string. An empty string or `N/A` skips that dataset.

| Configuration Setting | Source Data | Output Dataset |
|-----------------------|-------------|----------------|
| **CM Config String** | General modem measurements from the **CM** table (1000). | `CM_DATA` |
| **CM Interface Config String** | Interface data from **CMs Interface Tables** (5000). | `CM_INTERFACES` |
| **CM QAM DS Channels Config String** | Per-modem downstream summaries from the **CM** table (1000), not individual rows from the QAM downstream channel table. | `QAM_DS_DATA` |
| **CM QAM US Channels Config String** | **CM QAM US Channels** (9400). | `QAM_US_DATA` |
| **CM OFDM DS Channels Config String** | **CM OFDM DS Channels** (9600). | `OFDM_DS_DATA` |
| **CM OFDMA US Channels Config String** | **CM OFDMA US Channels** (9800). | `OFDMA_US_DATA` |

By default, the QAM downstream summary includes **CM QAM DS Avg Rx Power**, **CM QAM DS Avg Rx MER**, **CM QAM DS Sum Codewords**, **CM QAM DS Sum Corrected Codewords**, and **CM QAM DS Sum Uncorrected Codewords**.

#### Output Files and Cleanup

For each configured dataset, the collector writes a separate UTF-8 CSV file with semicolon-separated fields and a header row. The filename includes the OLT name, dataset name, and a local timestamp in `yyyyMMdd HHmmss` format. Files from the same offload cycle share a timestamp.

When enabled, cleanup runs during an offload cycle. It searches the collector's OLT folder and its subfolders for `.csv` files older than **File Age Threshold**. It does not clean the other OLT folders under the offload root.

> [!CAUTION]
> Cleanup does not check whether a CSV file was created by this connector. Keep unrelated CSV files out of the collector's OLT subfolder and its subfolders.

### Import Amplifier-Chain Data

The CPE backend manager can export amplifier-chain mappings for the collector. Import these mappings to associate cable-modem channels with amplifier paths in views and dashboards.

1. Make sure that the CPE backend manager has exported an AMP Chain file for this collector.

2. Set **CM AMP Chain Import Folder** to the directory containing the exported files.

   Use the folder configured for your deployment.

3. If the directory is a network share, configure **PNM Share Username** and **PNM Share Password** with an account that can read the files.

   The collector also uses these credentials for CM offload. Make sure the account can read the import files and has any access needed for offload.

4. Set **CM AMP Chain Import State** to *Enabled*.

   The default is *Disabled*.

5. Use **Import AMP Chain Files** to request an import.

6. Check **CM AMP Chain Import Status**.

   A completed import reports *OK* or *Failed*. If the import fails, check the element log, folder access, and the availability of a matching file.

When enabled, import also runs after full provisioning and once about *35 minutes* after the element starts. It is not a recurring 35-minute schedule. If you enable the feature later, use **Import AMP Chain Files** or run full provisioning to start an import.

The collector picks the matching file with the latest modification time in **CM AMP Chain Import Folder**. The filename must start with `AMPChains ` followed by the collector's DataMiner Agent ID, an underscore, its element ID, and a space. The collector checks only the configured folder, not its subfolders or backup folders.

Use the backend manager's original UTF-8, semicolon-separated export file. The imported mappings fill the amplifier-chain columns in **CM QAM DS Channels**, **CM QAM US Channels**, **CM OFDM DS Channels**, and **CM OFDMA US Channels**.
