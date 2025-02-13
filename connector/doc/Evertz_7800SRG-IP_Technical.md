---
uid: Connector_help_Evertz_7800SRG-IP_Technical
---

# Evertz 7800SRG-IP

The 7800SRG-IP is a PTP Slave Sync Generator designed to provide precise synchronization for hybrid IP and baseband broadcast environments.

The 7800SRG-IP acts as a reliable timing source by locking to an upstream PTP Grandmaster Clock over Ethernet and generating six independently configurable sync outputs. It supports various timing signals, including black burst, tri-level sync, continuous wave signals, and word clock, ensuring seamless synchronization across diverse broadcast and production workflows.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination.]

SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]

### Initialization

No other info is require to start pollling info.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### General Page

You can find all the information related to the device general parameters in this page. 

### Sync Page

You would find the Sync table with the following columns

- **Mode** – Sets the sync output mode (e.g., black burst, tri-level sync, CW signals).
- **VITC Control** – Enables Vertical Interval Timecode (VITC) on PAL or NTSC outputs.
- **VITC Line <1-2>** – Defines the VITC insertion lines (PAL: 6-31, NTSC: 10-30).
- **Drop Frame Control** – Enables the drop frame bit for NTSC timecode.
- **Color Frame** – Enables color frame reference for PAL or NTSC outputs.
- **Set Jam Time** – Sets the jam time for video output.
- **Jam Output** – Forces the output VITC time to match the reference.
- **Time Offset** – Adjusts the timecode offset in frames for video outputs.
- **Time Zone** – Sets the time zone for video outputs (-12:00 to +12:00 in 30-min steps).
- **DST Control** – Enables automatic Daylight Saving Time (DST) adjustment.
- **Ten Field Control** – Enables a ten-field pulse on NTSC outputs.
- **Color Phase** – Adjusts the color frame phase (PAL: 1-4, NTSC: 1-2).
- **Vertical Phase** – Adjusts the vertical sync phase.
- **Horizontal Phase** – Adjusts the horizontal sync phase.
- **Fine Phase** – Allows fine-tuning of sync phase as a percentage (0.00% to 99.4%).
- **Word Clock Level** – Selects 5V CMOS or ±1V sinusoidal output for word clock.
- **Timecode Source** – Defines timecode behavior:

### PTP

You woudl find the **PTP Port** and **PTP List** tables in this section along with **PTP Priority** parameters

### Fault

The **Managment Fault** table can be found here which can be alarmed to know if there is a fault present or not.

## Notes