---
uid: Connector_help_Nokia_Altiplano_Kafka_Analyzer
---

# Nokia Altiplano Kafka Analyzer

## About

The Nokia Altiplano Kafka Analyzer connector processes Kafka-based OLT data within the Altiplano Solution. It works alongside the Nokia Altiplano Manager connector in Slave mode to handle compressed OLT information, extract relevant data, and enable further processing.

The connector receives a reference to the Kafka data file via InterApp messaging, extracts and organizes the contents into individual JSON files per OLT, and then informs the Altiplano Manager that the files are ready for use. Temporary data is automatically removed after processing.

## Key Features

- **Kafka file processing**: Decodes and extracts OLT data from Kafka stream files.
- **JSON file generation**: Creates individual JSON data files per OLT.
- **Automated workflow**: Triggered via InterApp messaging from the Altiplano Manager connector.
- **Notification handling**: Notifies the Altiplano Manager when files are ready.
- **Temporary file cleanup**: Removes decompressed input files after processing.

## Use Cases

### Use Case 1

**Challenge**: Extracting OLT data from Kafka files for further processing.

**Solution**: Use the Kafka Analyzer to receive the file path via InterApp messaging, process it, and generate structured JSON files.

**Benefit**: Simplifies data handling and facilitates downstream automation.

### Use Case 2

**Challenge**: Maintaining a clean processing environment.

**Solution**: The connector automatically deletes temporary decompressed files after task completion.

**Benefit**: Optimizes server performance.

### Use Case 3

**Challenge**: Coordinating processing between connectors.

**Solution**: Automated InterApp messaging confirms readiness of OLT files for the Altiplano Manager Slave.

**Benefit**: Reduces manual interaction and improves workflow efficiency.

## Prerequisites

- Operational **Nokia Altiplano Manager connector in Slave mode**.
- Access to Kafka data storage directory.
- Enabled InterApp communication between both elements.
- File system access for reading, writing, and deleting JSON files.
