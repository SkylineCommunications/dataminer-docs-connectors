---
uid: Connector_help_Avcom_of_Virginia_EVO-RSA
---

# Avcom of Virginia EVO-RSA

## About

The Avcom of Virginia EVO-RSA is a spectrum analyzer. With this connector, you can retrieve the spectrum traces captured by the analyzer.

## Key Features

- **Real-time spectrum monitoring**: The captured traces are displayed in real time using [DataMiner Spectrum Analysis](https://aka.dataminer.services/Spectrum_Analysis). The user can configure the common analyzer settings: start and stop frequencies, video and resolution bandwidth, etc.

## Technical Reference

This connector uses a **serial connection**. When you [create an element](https://aka.dataminer.services/adding_elements) with this connector in DataMiner, you will need to specify the polling IP and the IP port of the device.

The library *aovsbs2.dll*, which is needed to establish communication with the spectrum analyzer, is included in the connector package and will be installed in the *C:\Skyline DataMiner\ProtocolScripts\DllImport* directory.
