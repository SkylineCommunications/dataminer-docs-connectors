---
uid: Connector_help_Eutelsat_Path_Detection_Service_Protocol
---

# Eutelsat Path Detection Service Protocol

This advanced service connector empowers users to monitor the signal path of a service efficiently.

## About

This connector leverages the fundamental service definition used to create enhanced services and augments it with path detection logic.

Enhanced services require a DataMiner version of **9.0.3.0** or higher.

### Version Info

| **Range** | **Description** | **DCF Integration** | **Cassandra Compliant** |
|------------------|-----------------|---------------------|-------------------------|
| 1.0.0.x          | Initial version | No                  | Yes (1.0.0.6+)          |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | DataMiner 9.0.3.0           |

## Installation and configuration

### Creation

When editing a service, open the **Advanced** tab and select the desired **Definition**, in this case *Eutelsat Path Detection Service Protocol*. Also select the desired **Version**.

### Configuration

On the general page, the user need to input the desired CGL TNM-7222-D Amethyst III and CISCO DCMs for monitoring.
A context menu is available to facilitate the input of necessary information in the DCM I/O Configuration table.

## Usage

### General

Once the user provides the correct configuration for monitoring, the DCM Active Input table will closely monitor the active DCM input and the Amethyst active input. 
Additionally, it will calculate and display the currently active path, which could be TH1, TH2, or a Warning state.
