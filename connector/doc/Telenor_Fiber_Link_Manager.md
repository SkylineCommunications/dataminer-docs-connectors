---
uid: Connector_help_Telenor_Fiber_Link_Manager
---

# Telenor Fiber Link Manager

## About

With this connector, it is possible to provision fiber link information from a formatted (CSV) file and generate **DataMiner resources**.

Each of these resources will represent the fiber link with a mapping to the corresponding **EPM object** found in the **Telenor EPM frontend manager**.

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

On the **General** \> **Config** page, configure the provisioning file and the **DataMiner Element Name** for the used frontend manager.

### Redundancy

There is no redundancy defined.

## How to use

Once the provisioning file has been selected, click the **Provision** button to start the lookup of **EPM objects** and the generations of the **resources**.

The resources will be stored under the **Telenor FiberLink pool** and can be accessed via the **Resources module** in DataMiner Cube.

## Notes

This connector must be used in combination with the **Telenor EPM Manager**.

The provisioning file must be a CSV (comma-separated) containing the following header: `Fiberlink_ID,Type,Address_1,ConPoint1,Address_2,ConPoint2`
