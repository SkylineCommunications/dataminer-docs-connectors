---
uid: Connector_help_Generic_2110_to_SDI_Converter
---

# Generic 2110 to SDI Converter

## About

This is a virtual connector that initializes **DCF (DataMiner Connectivity Framework)** connections at startup. It does not communicate with an actual device or expose data pages. Instead, it is used to create an element in DataMiner that provides DCF interfaces. These interfaces allow you to represent and manage connections between **ST 2110 IP inputs** and **SDI outputs** in your system.

## Key Features

- Initializes dedicated **DCF input and output interfaces** at startup.
- Enables you to link those interfaces to a **matrix of inputs and outputs**, allowing routing between IP-based (2110) and SDI signals.
- Does not require communication with any physical hardware.

## When to Use

Use this connector if you need to:

- Represent a **converter node** in your DataMiner System without requiring a real device.
- Model and manage **DCF connections** for 2110 ↔ SDI routing.
- Integrate with external routing control systems (e.g. VSM) by exposing consistent DCF endpoints.

This connector is essential for scenarios where you need a placeholder element to define and manage signal flow, but no actual device polling or data retrieval is required.
