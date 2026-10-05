---
uid: Connector_help_Harmonic_NSG9000_40G_Technical
---

# Harmonic NSG9000 40G Technical

## About

The Harmonic NSG 9000-40G is a high-density universal edgeQAM (EQAM) system designed to serve as a digital video gateway for cable operators. It multiplexes on-demand content over IP networks and is capable of reaching up to 648 QAM-RF output transport streams.

The **Harmonic NSG9000 40G** is an HTTP connector designed to provide comprehensive control and monitoring for the Harmonic NSG9000 40G EdgeQAM device.

## Configuration

### Connections

#### HTTP Connection – HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

**HTTP CONNECTION**:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The port of the destination.
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy*.

### Initialization

The NSG9000 devices have a default authentication setup that requires login details for a session. These details should be entered on the **Authentication Settings** subpage of the **General** page. These default login details can be different depending on the device type, and consequently they are different for the NSG9000 3G version.

- **Username:** The username or login of the corresponding access level.
- **Password:** The password of the user or access level.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### Alarm

The Alarm Overview table is a live mirror of what the chassis itself is reporting, one row per active fault, showing when the device raised it, which module is complaining, the severity, and the device's own description. Sorting by Alarm Module is the fastest way to tell a single failing card from a chassis-wide problem. If SNMP traps are enabled, the alarm severity updates immediately. For example, when a fault recovers, the row briefly shows Cleared before disappearing on the next polling cycle. How often the table refreshes is set in the Poll Manager table, row Status/Alarms, 60 seconds by default, but worth raising to 5–10 minutes if the device is sending traps to your DMA, since traps already deliver changes within seconds.
 
Alarm Storm Prevention exists because one real fault can produce hundreds of alarms in seconds, burying the actual cause under its own symptoms. It runs automatically in the background, there's nothing to enable, and sets Alarm Storm State (parameter 8000) to Active, Active (Only Warning Alarms), or Inactive. 
 
On the Alarm Storm Prevention subpage, you can configure the parameters for alarm storm prevention. It comes down to four saved settings: a storm is declared when the device is either loud  (more than 50 concurrent alarms), or suddenly loud (more than 100 new alarms in 60 seconds). Setting Rate Amount to 0 disables the rate check and leaves only the concurrent-alarm limits in play.

### CAS Settings

The **ECM Group Table** lists the ECM groups. To delete one or more rows, set the value in the **Delete ECM** column to *true* and then click the **Delete Selected** button below the table. To add a row, use the **Add ECM** subpage, enter new values, and click the **Set ECM** button.

> [!NOTE]
> When you **edit, add, or remove rows**, you may need to **wait** some time for each action to be **synchronized**. Otherwise, if new changes are received in the element before the updates, the previous **changes might be lost**.

### ECMG

On this page, you can find the communication parameters sent to the ECMG. Up to 10 ECMGs are supported.

> [!NOTE]
> The row must be active for the settings to be saved. The NSG9000 clears inactive rows.

### Overview

A tree view sorts all the **QAMs** by **RF** and **Module**. If you select an element, the status parameters are shown on the right. A list of the sub-elements and their information is shown at the bottom.

### SNMP Traps

> [!NOTE]
> SNMP Traps are supported starting from version 1.0.2.1

SNMP traps can be configured on the device to allow DataMiner to receive alarms in real-time. No additional configuration is required on DataMiner. The connector will automatically listen for traps from the same IP as the HTTP Connection.
