---
uid: Connector_help_Intelsat_Flex_Platform_VSAT
---

# Intelsat Flex Platform VSAT

The IntelSat Flex Platform VSAT functions as a virtual connector designed to streamline the presentation of critical data sourced from Intelsat terminals. This platform offers an intuitive front-end interface that enables users to conveniently interact with the data. To facilitate this process, a separate connector known as the Generic Kafka Consumer operates autonomously to ingest data from the Intelsat Kafka broker. This consumer collects the data and saves it in files at a designated location. Subsequently, the IntelSat Flex Platform VSAT injects these saved files, populating the corresponding data tables. This integrated approach ensures that the data is efficiently organized and instantly accessible via the interface of the connector.

## About

### Version Info

| Range              | Key Features             | Based on | System Impact |
|--------------------|--------------------------|----------|---------------|
| 1.0.0.x            | KAFKA files injection.   | -        | -             |
| 1.0.1.x [SLC Main] | REST API implementation. | -        | -             |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

A Generic KAFKA Consumer element must be created and configured before an IntelSat Flex Platform VSAT element is started.

### Configuration Page

#### Topic Settings

On the **Topic Settings** subpage, you can configure specific parameters related to importing data from KAFKA files.

#### REST API Endpoints

The **REST API Endpoints** subpage of this connector contains the REST API Authentication table and the REST API Endpoints Configuration table.

In the REST API Authentication table, you can specify the Username, Password, and API Key needed to authenticate the REST API calls.

An endpoint in the REST API Endpoints Configuration table with category "Remote" will be used to populate the Remotes table.

An endpoint in the REST API Endpoints Configuration table with category "Stats" will be used to populate stats metrics in the Terminals Table. The use of wildcards is possible for category "Stats" to be able to query through all the Terminal IDs and Metric IDs that are needed.

### Collector Setup Page

This page contains the settings to manage the **provisioning files** mechanism. The connector periodically exports configuration data for remotes, by updating an XML provisioning file on the DMA server, and retrieves information from the database contained in another provisioning file in JSON format. These mechanisms can be configured using the controls on this page.

For each process, file path controls allow you to specify the directory where the provisioning files should be located, and a processing timer parameter allows you to configure the interval for automatic processing.

The page also contains buttons that can be used to manually trigger each of the provisioning mechanisms.

On the right-hand side of the page, you can find the controls for the ID Notify mechanism:

- The ID Import Settings section contains controls to enable/disable the process of importing IDs from CSV files, as well as the path where the files are located and the current status of this process.
- The ID Export Settings section is similar to the ID Import Settings section, except that its controls apply to the process of exporting CSV files with ID requests.

## How to use

### Remotes Page

On the **Remotes** page of this connector, you will find the Remotes Overview table. This table is populated with data retrieved from the Intelsat Flex REST API.

### Remote Stats Page

On the **Remotes Stats** page of this connector, you will find the Terminals and SSPCs tables.

The Terminals table is populated with data retrieved both from the KAFKA broker via the Generic KAFKA Consumer and from the Intelsat Flex REST API.

The SSPCs Table is populated with data retrieved from the KAFKA broker via the Generic KAFKA Consumer.

### Circuits Page

On the **Circuits** page of this connector, you will find the Circuits Overview table, which contains all the information related to the circuits. This table is populated with data retrieved from the provisioning files, which contain information from the database.
