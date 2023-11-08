---
uid: Connector_help_Skyline_Dependency_Checker
---

# Skyline Dependency Checker

This connector aims to scan npm and NuGet projects for vulnerable/outdated/deprecated dependencies.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |-         |-         |-         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |-   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

Indicate if additional configuration of parameters is necessary in a newly created element.

### Redundancy

There is no redundancy defined.

## How to use

Start by the **Configuration** page, where the following parameters should be defined:

- **Npm Command File:** Directory path to the **'npm.cmd'** should be specified in order to allow npm audit scans of the projects present beloging to the defined repositories.
- **GitHub API:** GitHub API Bearer Token, which should be defined in order to retrieve vulnerability details, which will be retrieved via HTTP calls to the [https://api.github.com](url)
- **Logging Directory:** Directory path to store the logs related to the scans.

The connector supports scan of projects belonging to the directories added to the **Repositories** table in order to detect vulnerable/outdated/deprecated dependencies, 
being the results displayed in the **Scan Results** page.

It provides a **Control Center** that allows to configure which repositories are enabled for scanning, as well as other options such as: scheduler times, scan frequencies or execution information.

A **Log Visualizer** is also present in order to facilitate the consult of the log files generated upon scaning.

## Notes

- The logging files are being overwritten upon a new scan of the same repository.
- For large directories, the scan operation might take a considerable amount of time. 

