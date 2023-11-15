---
uid: Connector_help_Skyline_Dependency_Checker
---

# Skyline Dependency Checker

This connector can be used to scan NPM and NuGet projects for vulnerable, outdated, or deprecated dependencies.

## About

### Version Info

| Range              | Features | Based on | System Impact |
|--------------------|----------|----------|---------------|
| 1.0.0.x [SLC Main] | -        | -        | -             |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

When you have created the element, go to the **Configuration** page and configure the following parameters:

- **Npm Command File**: Specify the directory path to the **npm.cmd** file to allow NPM audit scans of the projects belonging to the defined repositories.
- **GitHub API**: Specify the GitHub API Bearer token to retrieve vulnerability details, which will be retrieved via HTTP calls to <https://api.github.com>.
- **Logging Directory**: Specify the directory where logs related to the scans should be stored.

## How to use

With this connector, you can scan projects in the directories added to the **Repositories** table in order to detect vulnerable, outdated, or deprecated dependencies. The results of a scan are displayed in the **Scan Results** page.

The connector provides a **Control Center** that allows you to configure which repositories are enabled for scanning. You can also configure scheduler times, scan frequencies, and execution information.

A **Log Visualizer** is also present, so you can easily consult the log files generated upon scanning.

Finally, you can use the **Overview** page to easily navigate from repositories to projects, to dependencies, and to vulnerabilities.

## Notes

- The log files are overwritten when a new scan of the same repository happens.
- For large directories, the scan operation may take a considerable amount of time.
