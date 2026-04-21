# ENENSYS IPGuardV3 & DataMiner Connector Overview

## 1. The Device: ENENSYS IPGuardV3
The **IPGuardV3** is a high-availability "safety switch" designed for digital TV and video broadcasting over IP. Its primary mission is to ensure that a television signal never goes dark, even if a network path fails or a piece of equipment malfunctions.

### Core Capabilities
* **1+1 Redundancy:** The device takes in two identical streams (Main and Backup) and monitors them in real-time.
* **Seamless Switching:** Using advanced buffering and alignment technology, it can switch between two streams without a single lost packet or visual glitch on the viewer's screen.
* **Stream Resynchronization:** It can automatically compensate for network delay differences between the two inputs, "lining them up" perfectly before a switch occurs.
* **Broadcast Standards:** Full support for DVB-T/T2, ISDB-T, and ATSC 3.0 (STLGuard).

---

## 2. The Connector: DataMiner Integration
While the IPGuardV3 handles the physical switching, the **DataMiner Connector** acts as the brain for the operator. It allows an engineer to manage the device remotely and integrate it into a larger broadcast ecosystem.

### What the Connector Does:
* **Centralized Monitoring:** Instead of logging into the device's local web page, operators see the status of all IPGuard units in a single DataMiner dashboard.
* **Alarming & Notification:** It translates the internal hardware errors and stream glitches into actionable alarms, notifying the right people via email, SMS, or visual alerts.
* **Performance Tracking:** It logs historical data (like bitrates and switch counts) so that engineers can analyze trends and find recurring network issues.
* **Automation:** DataMiner can use the connector to perform automated tasks, such as switching to a third backup path if both local inputs fail.

---

## 3. Key Operational Parameters
The following parameters are the most critical metrics monitored by the connector to ensure service continuity:

### Switching & Status
* **Switch Status (Active Input):** Shows whether the Main (IP1) or Backup (IP2) is currently "on-air."
* **Switch Mode:** Indicates if the device is in 'Auto' mode or if an operator has manually forced it to stay on one specific input.
* **Counter Switch:** Tracks how many times the device has had to flip between sources, which is a key indicator of network stability.

### Stream Health
* **Bitrate (IP1/IP2):** The speed of the incoming data. A sudden drop in bitrate is often the first sign of a problem.
* **Synchronization Status:** Confirms if the two inputs are aligned. If they aren't, a "seamless" switch might not be possible, leading to a visible glitch.
* **ETR 290 Errors:** Standardized broadcast health checks. These parameters flag technical errors deep inside the video data that simple IP checks might miss.

### System Logging
* **Alarm Log:** A historical record of every problem the device has encountered, including the severity (Critical, Major, Minor) and the exact time it happened.