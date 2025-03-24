---
uid: Connector_help_Ross_Video_MC1_Technical
---

# Ross Video MC1

## About

The Ross Video MC1 is a versatile master control switcher designed for streamlined broadcast operations. It provides frame-accurate video and audio transitions, branding capabilities, and automated workflows for live production environments. The MC1 supports a range of video formats and integrates seamlessly with automation systems, enabling precise playout control. Features include internal audio processing, multi-channel keying for branding elements, and failover redundancy to ensure uninterrupted broadcasts. With an intuitive interface and remote configuration options, the MC1 enhances operational efficiency while maintaining high broadcast quality.

This is a DataMiner connector for the **Ross Video MC1 cards**. With this connector, you can monitor the card's parameters using DataMiner's alarm and trending features. The connector is only capable of monitoring one card at a time. When you create an element using this connecter, the specified slot number determines which card is monitored.

## Configuration

### Connections

#### Serial Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination (default: *5253*).
  - **Bus address**: The **slot number** of the card you want to connect to.

## How to use

The connector is read-only at the moment, so every parameter you see can be monitored. Each page contains parameters or tables related to a specific aspect of the card. All of these parameters are retrieved using single serial commands. Status parameters are retrieved every ten seconds, while everything else is updated via a one-minute timer.
