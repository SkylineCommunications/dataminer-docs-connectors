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

On the **Alarm Storm Prevention** subpage, you can configure the parameters for alarm storm prevention.

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
