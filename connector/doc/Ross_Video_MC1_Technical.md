---
uid: Connector_help_Ross_Video_MC1_Technical
---

# Ross Video MC1

The Ross Video MC1 is a versatile master control switcher designed for streamlined broadcast operations. It provides frame-accurate video and audio transitions, branding capabilities, and automated workflows for live production environments. The MC1 supports a range of video formats and integrates seamlessly with automation systems, enabling precise playout control. Features include internal audio processing, multi-channel keying for branding elements, and failover redundancy to ensure uninterrupted broadcasts. With an intuitive interface and remote configuration options, the MC1 enhances operational efficiency while maintaining high broadcast quality.

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

The element created with this connector has the following data pages:

- **General**: Contains **Product**, **Hardware**, and **Network** parameters.
- **Program Fail-Over**: Contains parameters related to the **Auto Return** and **Mode**.
- **Video**: Contains the **Inputs Status** table, with information about all the inputs and the format of the inputs.
- **Audio**: Contains the **AES Video Status** table, with information about Channel A and B for each EAS input.
- **GPI/Tally**: Contains a table with information for each tally in the system, such as the **Number** and **Function**.
- **On Air Control**: Contains several standalone parameters like **EAS Status**, **Program Bus**, and **Audio Level**, as well as the **Keyers** table; with the **Status** and **Description** for each Keyer.
