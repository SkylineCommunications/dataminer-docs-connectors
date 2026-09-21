---
uid: Connector_help_Sencore_MRD_7000_Technical
---

# Sencore MRD 7000

The **Sencore MRD 7000** is a receiver decoder that supports up to 8 services (16 channels) of audio processing for **MPEG1/2**, **AAC** and **Dolby AC3/AC3+/Dolby E/ATMOS**.

Multichannel decoding allows the MRD 7000 to process up to 4x HD services or 1x UHD service in a 1RU chassis.

Output options include 4x3G-SDI (two sample interleave & four quadrant), 12G-SDI, HDMI 2.0B and SMPTE 2110 via 10 GB or 25 GB fiber.

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the conencted device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.
