---
uid: Connector_help_Thales_TDU2K5DD_UHF_DVB-T_Technical
description: "Set up and use the Thales TDU2K5DD UHF DVB-T connector, including the SNMP connection, polling modes, exciter switch-over, commands, and web interface."
---

# Thales TDU2K5DD UHF DVB-T

## About

The Thales TDU2K5DD is a UHF DVB-T transmitter that can be delivered as a single-drive or a dual-drive unit. In a dual-drive unit, two exciters (Exciter A and Exciter B) are installed, one of them is on air, and the other one is the reserve that takes over when a fault occurs.

This connector retrieves information from the transmitter via SNMP and processes the status traps the transmitter sends. It monitors the transmitter status, the functional and structural parameters, both exciters, the amplifiers, transistors, supplies, cooling units, and cabinets, and it allows you to send the main transmitter commands and to manage the supervision settings of the device.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the transmitter.
- **IP port**: The IP port of the transmitter, by default *161*.

SNMP Settings:

- **Get community string**: The community string used when reading values from the transmitter (default: *public*).
- **Set community string**: The community string used when setting values on the transmitter (default: *private*).

### Initialization

No manual steps are required for the SNMP polling. When the element starts, the connector fills in the **Web Interface** parameter with the polling IP of the SNMP connection and the **HTTP Port** with *80* if they are still empty. If the transmitter web server is reached via a different address or port than the SNMP agent, change these values on the **HTTP** subpage of the Supervision page.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

The **Webinterface** page opens the address `http://<Web Interface>:<HTTP Port>`, built from the **Web Interface** and **HTTP Port** parameters on the HTTP subpage. If the page stays empty, check that these two parameters are correct and that the client machine, not the DataMiner Agent, can reach that address.

## How to Use

The element follows the structure of the transmitter. The **General**, **Status**, **Functional**, and **Structure** pages describe the transmitter as a whole, the **Exciter A** and **Exciter B** pages describe the two drives, the **Cabinets**, **Supplies**, **Amplifiers**, and **Cooling** pages describe the amplification chain, and the **Configuration**, **Commands**, and **Supervision** pages are used to change settings on the device.

### General Page

This page shows the **Equipment Family**, **Update Version**, and **System Time** of the transmitter, and the **Software Versions** table with the version of each software subpart.

The **Polling Config** page button opens the subpage with the two polling toggles of the element.

#### Polling Config Subpage

The connector polls the device in three speeds: the functional and status parameters, the Exciter A page, the system time, the agent activity, and the component tables every 10 seconds; the commands, the configuration (including the OFDM settings), and the Exciters table every 5 minutes; and the structure, general, supervision, managers, contacts, profiles, events, and software version information every hour. The Exciter B page is only polled on a dual-drive transmitter: the connector starts the Exciter B polling when the **Drive Type** on the Structure page is *Dual Drive*. On a single-drive transmitter, the Exciter B values are not polled, and they are shown as *Not Available* once the polling mode has been switched.

- **Polling All Active**: Controls the full polling described above. By default, this is set to *Yes*. When you set it to *No*, the connector switches to a **reduced polling mode**: the regular polling stops, and only the **1PPS** and **External 10 MHz** presence of each exciter and the **Insufficient Power** and **Excessive Power** states are refreshed every hour, and the **Type**, **Drive Type**, **Cooling Type**, **Frequency**, and **Transmitter Control** values once a day. The other Exciter B parameters are set to *Not Available*, and all other parameters and tables keep their last value. Use this mode only on sites where the SNMP load has to be kept to a minimum.
- **Fast Polling Active**: Controls a dedicated 10-second poll of the key alarm parameters of the Status page (among others **Transmitter Status**, **Transmitter**, **RF Present**, **Power Reduced**, **Exciter On Antenna**, **Exciter A Fault**, **Exciter B Fault**, **General Amplifier Fault**, **General Supply Fault**, **Cooling Fault**, **Temperature Fault**, **Switch Fault**, **VSWR Amplifier**, and **Change Over Mode**) and of the **Operator** parameter. This poll runs independently of **Polling All Active**, so you can keep it enabled in reduced polling mode to keep the most important alarms up to date. When full polling is active, it is not needed, as these parameters are already polled every 10 seconds.

### Status Page

This page gives the operational picture of the transmitter: the overall **Transmitter Status** and **Transmitter** state, the **Major Fault** synthesis, **RF Present**, **RF Fault**, **Insufficient Power** and **Excessive Power**, **VSWR Antenna Value** and **VSWR Amplifier**, the temperature, switch, synthesizer, and GPS faults, the cooling faults (air, water, breaker, flow pressure, input and output temperature, and load), the synthesis of the cabinet faults (safety, main breaker, main fault, multiplex board), and the SFN-related values (**Network Delay**, **Equalization Delay**, **Maximum Delay**, **Mega-Frame Offset**, and **Quality Level**).

The redundancy-related parameters on this page are **Exciter On Air**, **Exciter On Antenna**, **Reserve Exciter**, **Change Over Mode** (*Manual* or *Automatic*), and **Change Over Occured**. On a dual-drive transmitter, check these first after an exciter fault alarm: if a change-over has occurred, the service is still on air but without redundancy until the faulty exciter is repaired and the transmitter is switched back.

All parameters on this page are monitored, so you can define alarm thresholds for them in an alarm template. **Major Fault** is set by the device when the quality level drops to 13 or lower or when a cabinet interlock alarm is active, which makes it a good single parameter for a site overview.

### Functional Page

This page shows the RF settings and measurements of the transmitter, such as **Tx Frequency** and **Frequency Offset**, **Network Type**, the **Ripple Level** and **Shoulder Level** with their thresholds, **MER**, **BER Before Viterbi** and **BER After Viterbi**, the **Hours Counter**, and the **Pre-Selected Exciter**.

The power values deserve attention. The device reports **Calibrated Power** and **Requested Power** in watts, but **Measured Power**, **Measured Reflected Power**, **Reflected Power Antenna**, and **Requested Power Percent** as a percentage of the calibrated power. The connector therefore calculates **Forward Power (W)**, **Reflected Power (W)**, and **Reflected Antenna Power (W)** from these values each time they are polled. These three parameters are trended, so they are the ones to use in trend graphs and dashboards when you want to follow the actual output power of the transmitter.

### Structure Page

This page describes how the transmitter is built: the supervision **Type**, the **Drive Type** (*Single Drive* or *Dual Drive*), the **Standard**, the **Maximum Power**, the **Length**, the **Family**, the **Cooling Type**, the number of amplifiers, supplies, and cabinets, and which options are fitted (linear correction, digital filter, OLDC, dual ASI, foldback, cooling load, and cooling redundancy).

These values rarely change, so they are polled once an hour. **Drive Type** is also used by the connector itself to decide whether the Exciter B parameters are polled.

### Exciter A and Exciter B Pages

Each exciter has an identical page with its modulator input and type, the DVB-T modulation settings (**Modulation Mode**, **Guard Interval**, **Modulation Type**, **Hierarchic**, **FEC Rate**, **Identifier**, and **Tx Length**), the presence and status of its boards and links (TX board, RX, DAP, CUDC, modulator, TS inputs, dual ASI, extension input, quality of service), its synchronization sources (**1PPS**, **External 10 MHz**, **Modulator 10 MHz**, internal GPS, and GPS monitoring), its correction stages (digital filter, linear correction, LUT non-linear correction, and OLXC), its **Power Reduction** and **Power Reduction [%]**, and its **Software Version** and **Hardware Version**.

The **Exciter A** and **Exciter A State** parameters (and their Exciter B counterparts) summarize the overall status and state of the exciter. On a single-drive transmitter, the Exciter B page is not polled (see [Polling Config Subpage](#polling-config-subpage)).

### Cabinets, Supplies, Amplifiers, and Cooling Pages

These pages each contain one table per component type, with a row per physical component:

- The **Cabinets** table shows the general interlock, safety fault, main breaker, main fault, supply fault, amplifier fault, and multiplex board state of each cabinet, together with the number of amplifiers and supplies it contains.
- The **Supplies** table shows the status, breaker, fuse, presence, on/off, and awaited state of each power supply, with the cabinet it belongs to, its physical location, and the number of amplifiers it feeds.
- The **Amplifiers** table shows the amplifier status, VSWR status, presence, use, current fault, overheating, and AGC gain of each amplifier, with its type, the number of transistors, the cabinet and supply it belongs to, and its physical location. The **Transistors** and **Pre-Amplifiers** page buttons open the subpages with the **Transistors** table (the current state of each transistor and the amplifier it belongs to) and the **Pre-Amplifiers** table (the status and location of each pre-amplifier).
- The **Cooling** table shows the type and status of each cooling unit, with its breaker, circuit, flow pressure, input and output temperature, air flow, load, and change-over state.

The structure information in these tables (type, location, cabinet and supply IDs, and component counts) comes from separate structure tables of the device. The connector retrieves these once right after the first poll of each status table and then once an hour, and merges them into the status tables. The fault columns are monitored, so you can define alarm thresholds for them in an alarm template, which allows an alarm on one amplifier or supply to be located immediately.

### Configuration Page

This page allows you to change the operating settings of the transmitter: the foldback and OLXC settings, the quality settings, the RF alarm and fault thresholds, the ripple and shoulder thresholds, the **Linear Correction Mode** and **Non-Linear Correction Mode**, the mute settings, **Synthesizer Control**, **Fine Frequency Offset**, and **Signal Capture Period**.

The **OFDM** page button opens the subpage with the DVB-T modulation settings of the transmitter, such as **Modulation Mode**, **Guard Interval**, **Modulation Type**, **FEC Rate**, **Input Type**, and **Synchronization**.

Every setting on this page and its subpage is written to the transmitter as soon as you change it. Changing the modulation settings of a transmitter that is on air affects the broadcast signal, so only change them during a maintenance window. These settings are polled every 5 minutes (or every minute while the page is open in DataMiner Cube), so a change made on the device itself can take up to 5 minutes to show in the element.

### Commands Page

This page contains the transmitter commands. All of them act on the live transmitter immediately, and the displayed value is refreshed once the device confirms the change.

- **Transmitter Control**: Switches the transmitter *On* or *Off*.
- **Switch Over Mode**: Sets the exciter change-over to *Manual* or *Automatic*. In automatic mode, the transmitter switches to the reserve exciter by itself when the active exciter fails.
- **Reduced Power**: Reduces the output power to *-3 dB* or *-6 dB*, or restores the full power with *0 dB*. The **Power Reduced** parameter on the Status page shows the current state.
- **Exciter On Antenna Control**: Selects the default exciter (*Exciter A* or *Exciter B*) that drives the antenna. This command is only available on a dual-drive transmitter. The transmitter keeps using this exciter until a fault causes a change-over.
- **Reserve Exciter Control**: Starts (*On*) or stops (*Off*) the reserve exciter. This command is only available on a dual-drive transmitter.
- **Requested Power Control**: Sets the requested output power as a percentage of the calibrated power, between *25* and *112* %.
- **Set Date Time**: Sets the system date and time of the transmitter, in the format `hh:mm:ss-yyyy/mm/dd` (e.g., `23:59:59-2001/12/31`).
- **Reset**: Resets the transmitter. A confirmation message is shown before the command is sent.

The **Exciters** table on this page allows you to set the **Gain Mode** and the **Dual ASI Main TS** of each exciter. Both settings can only be changed when the **Exciter A Type** or **Exciter B Type** (shown on the Exciter A and Exciter B pages) is *Sirius*.

> [!CAUTION]
> These commands directly affect the on-air signal. Switching the transmitter off, resetting it, or changing the exciter on antenna interrupts or disturbs the broadcast. Make sure the DataMiner users who have access to this page are the ones who are allowed to operate the transmitter.

### Supervision Page

This page contains the settings of the SNMP agent of the transmitter. **Agent Activity** shows whether the agent is accessible. **Email DVBTX**, **SMTP Server IP Address**, and **SMTP Server Port** configure the sender address and mail server the transmitter uses to send event emails.

The **Managers** table lists the IP addresses to which the transmitter sends its SNMP traps. To add a manager, enter its IP address in **Add Manager**; to remove one, select it in **Delete Manager**. To make sure DataMiner receives the traps of the transmitter, the IP address of the DataMiner Agent hosting the element must be in this table.

The **Contacts** table lists the email addresses that receive the event emails, with the group each contact belongs to. To add a contact, enter its email address in **Add Contact**; to remove one, select it in **Delete Contact**.

The page buttons on this page open the following subpages:

- **Events**: The **Events** table lists the events the transmitter can report, with their OID. For each event, you can enable or disable the trap (**Trap Valid**) and the email to each of the three contact groups (**Group 1 Email**, **Group 2 Email**, and **Group 3 Email**). If you disable the trap of an event, DataMiner no longer receives it, and the corresponding parameter is only refreshed by polling.
- **Profiles**: The **Profiles** table lists the user profiles of the transmitter, with their name, password, and Telnet and FTP access rights.
- **HTTP**: Contains the **Web Interface** address and the **HTTP Port** used by the Webinterface page (see [Web Interface](#web-interface)).

The Managers, Contacts, Events, and Profiles tables are polled once an hour, so a change made on the device itself can take up to an hour to appear in the element.

### Webinterface Page

This page embeds the web interface of the transmitter, using the address configured on the HTTP subpage of the Supervision page. Use it for settings that are not available through SNMP.

### Trap Handling

The transmitter sends a trap when one of the following changes: transmitter state, transmitter status, change-over occurrence, Exciter A fault, Exciter B fault, switch fault, VSWR amplifier fault, temperature fault, cooling fault, general supply fault, cooling change-over, power reduction, RF presence, and operator. When the connector receives such a trap, it immediately polls the corresponding Status or Functional parameter, independently of the polling mode. The traps themselves are not shown as alarms; the resulting parameter change is.

## Notes

- To receive traps, the IP address of the DataMiner Agent hosting the element must be configured as a manager on the transmitter (see [Supervision Page](#supervision-page)).
- The **Web Interface** address and the **HTTP Port** are filled in automatically when the element starts and they are still empty: the address with the polling IP of the element, and the port with *80*. This was added so that the Webinterface page also works on replicated elements. If the client machine cannot reach the transmitter on that address, enter the correct address and port on the HTTP subpage.
