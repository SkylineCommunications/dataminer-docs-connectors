---
uid: Connector_help_Skyline_EPM_Platform_FTTH_Collector
---

# Skyline EPM Platform FTTH Collector

## About

FTTH (Fiber to the Home) networks use optical fiber to provide connectivity to customer locations. At each location, an ONT (Optical Network Terminal) connects the customer to the fiber network.

DataMiner Experience and Performance Management (EPM) organizes and monitors large numbers of ONTs. It allows operators to navigate through the FTTH network structure, from a network location down to an individual ONT, and to view the operational and optical condition of the network.

The **Skyline EPM Platform FTTH Collector** maintains the information for the ONTs assigned to it. This includes:

- Where each ONT is located in the network.
- Whether each ONT is **In Service** or **Out of Service**.
- Whether power loss or loss of signal has been reported.
- The latest received (Rx) and transmitted (Tx) optical power measurements.

A POP (Point of Presence) represents a network location and groups the ONTs served from that location. Each collector must be assigned one or more complete POPs. All ONTs belonging to the same POP must be assigned to the same collector. Do not divide a POP across multiple collectors.

## How the connector fits into the FTTH EPM Solution

The solution uses the following components:

- **Telenet EPM Platform FTTH WM**: Sends each ONT status or optical measurement to the collector responsible for that ONT. It identifies an ONT by its NCPID (NetCo Connectivity Product ID). For more information, see [Telenet EPM Platform FTTH WM](xref:Connector_help_Telenet_EPM_Platform_FTTH_WM).
- **Skyline EPM Platform FTTH Collector**: Stores the assigned ONT inventory and keeps the status and optical measurements of those ONTs up to date.
- **Skyline EPM Platform FTTH backend**: Combines information from multiple collectors and calculates summary values for different parts of the network.
- **Skyline EPM Platform FTTH frontend**: Provides the main operational view of the FTTH network and coordinates the distribution of inventory across the collectors. For more information, see [Skyline EPM Platform FTTH](xref:Connector_help_Skyline_EPM_Platform_FTTH).

The operational flow is as follows:

1. The FTTH frontend assigns one or more complete POPs to each collector and generates an inventory file for that collector.
1. The collector imports the file and displays the assigned ONTs in the **ONT Overview** table.
1. The workflow manager sends new ONT statuses and optical measurements to the collector responsible for each ONT.
1. The collector updates the ONT information. The backend and frontend then use this information to present detailed and summarized network views.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

The connector does not connect directly to an ONT or another network device. It receives its inventory and ONT updates from the other components of the FTTH EPM Solution.

### Prerequisites

- DataMiner version **10.4.0.0 - 16516** or later is required.
- The collector must be added to the FTTH EPM Solution.
- One or more complete POPs must be assigned to the collector. A POP must not be divided across multiple collectors.
- The FTTH frontend and workflow manager must be configured to send the correct inventory and ONT updates to this collector.
- The configured DataMiner Agent must be able to access the inventory directory.

### Initialization

After creating the element:

1. Open the **Configuration** page and select **Frontend Inventory File**.
1. Configure the inventory directory type and path.
1. If the directory is remote, configure an account that can access the share.
1. Open **Optical Thresholds** and configure the accepted ranges and reporting thresholds for the Rx and Tx optical measurements.
1. Verify that the collector has been assigned one or more complete POPs and that the FTTH frontend and workflow manager refer to the correct collector.
1. Start the inventory generation and import process from the FTTH frontend.
1. On the collector's **General** page, verify that the inventory was imported successfully.

### Frontend Inventory File

- **Import Directory Type**: Select **Local** when the inventory directory is on the same DataMiner Agent as the collector element. Select **Remote** when the directory is on another server.
- **Inventory File Directory**: Enter the directory containing the structured inventory file generated for this collector.
- **Network Share Username** and **Network Share Password**: For a remote directory, enter an account that can access the share. The username can be entered as `DOMAIN\username` or `username`. These credentials are not used for a local directory.

Example paths:

```text
Local: C:\FTTH\Inventory
Remote: \\RemoteServer\FTTH\Inventory
```

### Optical Thresholds

- **Rx Threshold**: The received optical power level used to group ONTs above and below that level.
- **Tx Threshold**: The transmitted optical power level used to group ONTs above and below that level.
- **Rx Boundary Min** and **Rx Boundary Max**: The lowest and highest accepted Rx values. The defaults are -28 dBm and -8 dBm.
- **Tx Boundary Min** and **Tx Boundary Max**: The lowest and highest accepted Tx values. The defaults are 0.5 dBm and 5 dBm.

If either value in an incoming Rx/Tx measurement is outside the accepted range, the collector rejects the complete measurement. Configure the thresholds before using the summarized optical information in the EPM views.

### Debug Mode

Enable **Debug Mode** on the **Configuration** page to write additional diagnostic information to the element log. Enabling it also makes the **Debug** page visible.

## How to use

### Loading the ONT inventory

The FTTH frontend generates a separate inventory file for each collector. The file contains the ONTs belonging to the complete POPs assigned to that collector. The file name identifies the DataMiner Agent (DMA) hosting the collector and the collector element that must import it:

```text
inventory_<collector DMA ID>_<collector element ID>.csv
```

The inventory file represents the complete inventory that the collector must manage; it is not a list of only the latest changes. After a successful import, the collector adds new ONTs, refreshes existing ONTs, and removes ONTs that are no longer present in the file.

All ONTs belonging to the same POP must be included in the inventory of the same collector. Do not distribute the ONTs of one POP across different collectors.

If the file is empty or invalid, the import fails and the previously loaded inventory remains available. Use **Last Inventory Load Result** and **Last Inventory Load Message** to verify the outcome.

### Supported ONT events

| Event | Purpose |
|---|---|
| Status change | Reports that an ONT changed to **In Service** or **Out of Service**, optionally because of power loss or loss of signal. |
| Status synchronization | Periodically confirms whether an ONT is currently **In Service** or **Out of Service**. |
| Optical measurement | Provides the latest received (Rx) and transmitted (Tx) optical power measurements. |

Only ONTs present in the imported inventory are updated. Invalid or unknown events are logged and ignored.

### ONT operational status

When an ONT reports **In Service**, the collector clears its Power Loss and Loss of Signal indications. When an ONT reports **Out of Service**, the update can identify power loss or loss of signal as the reason.

The collector also checks the ONT information every hour. If it has not received a status update for an ONT in more than 48 hours, it marks that ONT **Out of Service**.

### Optical measurements and reference values

The collector processes the received (Rx) and transmitted (Tx) optical power as one measurement. If either value is outside its accepted range, neither value is stored.

The collector uses a *birth certificate* as the reference measurement for an ONT. It compares later measurements with this reference so that operators can see how much the optical levels have changed. The first accepted measurement after a birth certificate is cleared becomes the new reference:

- **Birth Certificate Rx** and **Birth Certificate Tx** store the reference measurements.
- **Birth Certificate Created** stores the event timestamp of the reference pair.
- **Birth Certificate Rx Delta** is the current Rx minus the reference Rx.
- **Birth Certificate Tx Delta** is the current Tx minus the reference Tx.

Use the **Birth Certificate** configuration page to:

- Clear the certificate for one ONT by entering the exact NCPID and selecting **Clear Selected Birth Certificate**.
- Clear the certificates for every ONT managed by the collector by selecting **Clear Birth Certificates**.

Clearing a birth certificate does not remove the current Rx or Tx measurement. The next accepted Rx/Tx measurement becomes the new reference.

## Operation and monitoring

### General page

Use the following parameters to verify inventory provisioning:

- **Inventory File Import Status**: Indicates whether an import is idle or processing.
- **Loaded Inventory File Name**: Shows the file used by the last successful import.
- **Last Inventory Load**: Shows when the last successful import completed.
- **Last ONT Count**: Shows the number of ONTs loaded by the last successful import.
- **Last Inventory Load Result**: Shows whether the latest import attempt succeeded or failed.
- **Last Inventory Load Message**: Provides the result details or failure reason.

A failed import updates the result and message but does not overwrite the file name, timestamp, or ONT count from the last successful import.

### ONT page

The **ONT Overview** table contains:

- Identity and topology: NCPID, AAP, Headend/HUB, POP, splitter, POC, label, and operator.
- Address information: House number, street, postal code, and town.
- Operational status: In Service or Out of Service, Power Loss, and Loss of Signal.
- Optical measurements: Rx, Tx, birth-certificate reference values, and the difference between the current and reference values.
- Event timing: Last Seen, Last Event, Last Metrics Time, and Birth Certificate Created.

**Last Stale ONT Offline Check** shows when the most recent hourly status check completed.

### Summarized EPM information

The collector provides summary information to the FTTH EPM backend and frontend. This allows an operator to assess a complete network area instead of checking every ONT individually. Depending on the selected level of the network, this information includes:

- Total ONT counts.
- Out-of-service counts and percentages.
- Power Loss and Loss of Signal counts or percentages.
- Average Rx and Tx levels.
- Percentages above and below the configured Rx/Tx thresholds.
- Average difference between current Rx/Tx measurements and the birth-certificate reference values.

The available grouping scopes are Headend/HUB, POP, splitter, label, operator, and supported combinations with operator.

## Troubleshooting

1. Check **Inventory File Import Status**, **Last Inventory Load Result**, and **Last Inventory Load Message**.
1. Confirm that the requested file name exactly matches the collector's DataMiner Agent ID and element ID.
1. Confirm that **Inventory File Directory** points to the directory containing that file.
1. For a remote directory, verify the share permissions and configured credentials from the DataMiner Agent hosting the collector.
1. If events are not updating an ONT, confirm that the NCPID exists in **ONT Overview** and in the workflow manager's routing table.
1. For missing optical updates, verify that both Rx and Tx are present and within the configured validity boundaries.
1. Enable **Debug Mode** and inspect the collector element log for rejected inventory rows, invalid events, unknown NCPIDs, or ignored measurements.
