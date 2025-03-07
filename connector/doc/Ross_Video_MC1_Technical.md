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

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *5253*)]
  - **Bus address**: [The **Slot Number** for the card which we are connecting to.]


### Initialization

At the moment of creating the element, the user needs to configure the Bus Address by putting the slot number of the card that we are going to request the information from.

### Redundancy

There is no redundancy defined.

## How to use

### General Page

You can find parameters related to **Product**, **Hardware** and **Network**

### Program Fail-Over
Contains parameters related with the **Auto Return** and **Mode**.

### Video
The **Inputs Status** table is found here with information for all the inputs and the formart of the input.


### Audio Page
The **AES Video Status** table with information about Channel A and B is found here for each EAS Input.

### GPI/Tally
For each tally in the system information such as the **Number** and **Function** is found here on this table.

### On Air Control
Few stand-alone parameters like **EAS Status**, **Program Bus** and **Audio Level**. You will also find the **Keyers** table with the **Status** and **Description** for each Keyer.

## Notes