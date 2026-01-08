---
uid: Connector_help_Skyline_EPM_Platform_VSAT_WM_CMDB_Technical
---

# Skyline EPM Platform VSAT WM CMDB

## About

The **Skyline EPM Platform VSAT WM CMDB** connector is a workflow manager that handles file-based provisioning for the CMDB(Customer Management Database) data management within the system. This connector reads device inventory data from JSON files, processes mapping configurations, and generates provisioning output files for connectors.

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

After creating the element, configure the following parameters on the **Configuration** page:

- **File Handling**: Enable this toggle to activate the file provisioning logic.

- **Provisioning Interval**: Set the interval (in seconds) for how often the provisioning logic should run. The default is 20 seconds, with a range of 10 seconds to 1 day.

- **Mapping File Import Path**: Specify the path to the JSON mapping instruction file that defines how source data fields are transformed to output fields.

- **User Name** and **Password**: If using remote file locations, provide the credentials for network share access. The username can be in the format `DOMAIN\username` or just `username`.

#### Import Configuration

Access the **Import Configuration** subpage via the page button on the Configuration page to configure:

- **Connector File Import Directory Type**: Select *Local* or *Remote* depending on where the CC (Circuit Configuration) files are located.
- **Connector File Import Path**: Specify the folder path containing the CC files (XML or CSV format with `_CC` suffix).

- **Global File Import Directory Type**: Select *Local* or *Remote* depending on where the inventory JSON file is located.
- **Global File Import Path**: Specify the path to the inventory JSON file.

#### Export Configuration

Access the **Export Configuration** subpage via the page button on the Configuration page to configure:

- **File Export Directory Type**: Select *Local* or *Remote* depending on where the output CP (Circuit Provisioning) files should be written.
- **File Export Path**: Specify the output folder path where generated JSON files will be saved.

## How to Use

### General Page

The **General** page displays the current provisioning status and allows manual triggering:

- **Provisioning Status**: Shows the current state (Idle, Processing, or Error).
- **Provisioning Execution Timer**: Displays how long the last import/export operation took.
- **Last Execution Time**: Shows when the provisioning logic last ran.
- **Apply Provisioning**: Button to manually trigger the provisioning process.

### Configuration Page

The **Configuration** page contains all settings required for the connector to operate:

- Enable or disable file handling
- Set the provisioning interval
- Configure the mapping file path
- Set up remote access credentials
- Access Import and Export configuration subpages

### Automated Processing

When **File Handling** is enabled, the connector automatically:

1. Reads the inventory JSON file from the configured global import path.
1. Scans the connector import path for CC files (XML or CSV).
1. For each CC file, filters inventory records by matching circuit aliases.
1. Applies the mapping rules to transform data fields.
1. Generates output JSON files with a `_CP` suffix in the export folder.

The process runs at the configured **Provisioning Interval** and can also be triggered manually via the **Apply Provisioning** button.

### File Format Requirements

#### Inventory JSON File

The global inventory file must be a JSON file containing a `records` array with device information:

```json
{
  "records": [
    {
      "circuitAlias": "CIRCUIT-001",
      "circuitId": "01",
      ...
    }
  ]
}
```

#### CC Files (Circuit Configuration)

The connector supports two CC file formats:

- **XML format**: Must contain `Remotes/Remote/Name` elements with the device names.
- **CSV format**: Must include a `Name` column header with the device names.

Files must have a `_CC` suffix in the filename (e.g., `DMA_EID_CC.xml` or `ElementName_CC.csv`).

### Mapping JSON File

The mapping file is a JSON configuration that transforms source inventory data into a structured output format. It controls how fields from the source JSON are mapped to the output JSON.

#### File Structure

```json
{
  "emitArray": "<output_array_name>",
  "fields": [ /* field mapping rules */ ],
  "arrays": [ /* array mapping rules */ ]
}
```

#### Required Top-Level Properties

| Property | Type | Description |
|----------|------|-------------|
| `emitArray` | string | **Required**. The name of the root array in the output JSON (e.g., `"circuits"`). |
| `fields` | array | **Required**. Array of field mapping rules for simple properties. |
| `arrays` | array | **Required**. Array of mapping rules for nested arrays. |

#### Field Mapping Rules

Each entry in the `fields` array defines how a single output property is populated.

##### Option 1: Using `from` (Copy from Source)

Copies a value from the source data to the output:

```json
{ "to": "circuitId", "from": "src.circuitId" }
```

| Property | Type | Description |
|----------|------|-------------|
| `to` | string | **Required**. The output property name. Supports dot notation for nested objects. |
| `from` | string | **Required** (if no `const`). Path to the source value. Must start with `src.` (e.g., `"src.circuitAlias"`) for circuitAlias|
| `default` | any | Optional. Value to use if the source path returns null or is not found. |

##### Option 2: Using `const` (Constant Value)

Sets a fixed value in the output:

```json
{ "to": "found", "const": true }
{ "to": "fande", "const": null }
```

| Property | Type | Description |
|----------|------|-------------|
| `to` | string | **Required**. The output property name. |
| `const` | any | **Required** (if no `from`). A constant value (`true`, `false`, `null`, string, number, array, or object). |

> [!IMPORTANT]
> A field rule must have either `from` OR `const`, but **not both**.

#### Path Syntax

##### Source Paths (`src.`)

Use `src.` prefix to reference the root source record:

```json
{ "to": "customerName", "from": "src.customerName" }
```

##### Nested Output Properties (Dot Notation)

Use dot notation in `to` for nested objects:

```json
{ "to": "serviceAddress.city", "from": "src.city" }
```

This creates:

```json
{ "serviceAddress": { "city": "New York" } }
```

##### Array Index Access (Bracket Notation)

Use brackets to access specific array elements:

```json
{ "to": "outageContact.name", "from": "src.contactInfos[0].name", "default": null }
```

#### Array Mapping Rules

The `arrays` section transforms source arrays into output arrays:

```json
{
  "arrays": [
    {
      "to": "devices",
      "from": "src.devices",
      "itemFields": [
        { "to": "deviceType", "from": "item.type" },
        { "to": "device", "from": "item.device" },
        { "to": "dnsEntityName", "from": "src.dnsEntityNames[0]", "default": null }
      ]
    }
  ]
}
```

| Property | Type | Description |
|----------|------|-------------|
| `to` | string | **Required**. Output array property name. |
| `from` | string | **Required**. Source array path (e.g., `src.devices`). |
| `itemFields` | array | **Required**. Field rules applied to each array item. |

##### Item Field Path Prefixes

| Prefix | Description | Example |
|--------|-------------|---------|
| `item.` | References the current array item | `{ "to": "model", "from": "item.model" }` |
| `src.` | References the root source record | `{ "to": "dnsName", "from": "src.dnsEntityNames[0]" }` |

#### Common Customization Scenarios

##### Adding a New Field from Source

```json
{ "to": "newField", "from": "src.sourceFieldName" }
```

##### Adding a Constant Field

```json
{ "to": "version", "const": "1.0" }
```

##### Renaming a Field

```json
{ "to": "outputName", "from": "src.differentSourceName" }
```

##### Creating Deeply Nested Objects

```json
{ "to": "location.coordinates.lat", "from": "src.latitude" },
{ "to": "location.coordinates.lon", "from": "src.longitude" }
```

##### Handling Missing Data with Defaults

```json
{ "to": "optionalField", "from": "src.mightNotExist", "default": "N/A" }
```

#### Validation Rules

The connector validates the mapping file. The rules must be met:

1. `emitArray` must be a non-empty string
1. `fields` must be present (can be empty)
1. `arrays` must be present (can be empty)
1. Each field rule must have a `to` property
1. Each field rule must have either `from` OR `const` (not both)
1. Each array rule must have `to`, `from`, and `itemFields`

#### Complete Example

```json
{
  "emitArray": "circuits",

  "fields": [
    { "to": "circuitAlias", "from": "src.circuitAlias" },
    { "to": "circuitId", "from": "src.circuitId" },
    { "to": "countryCode", "from": "src.country" },
    { "to": "customerName", "from": "src.customerName" },
    { "to": "status", "from": "src.status" },

    { "to": "found", "const": true },
    { "to": "fande", "const": null },

    { "to": "outageContact.name", "from": "src.contactInfos[0].name", "default": null },
    { "to": "outageContact.telephone", "from": "src.contactInfos[0].telephone", "default": null },
    { "to": "outageContact.email", "from": "src.contactInfos[0].email", "default": null },

    { "to": "serviceAddress.streetAddress1", "from": "src.streetAddress1" },
    { "to": "serviceAddress.city", "from": "src.city" },
    { "to": "serviceAddress.country", "from": "src.country" }
  ],

  "arrays": [
    {
      "to": "devices",
      "from": "src.devices",
      "itemFields": [
        { "to": "deviceType", "from": "item.type" },
        { "to": "device", "from": "item.device" },
        { "to": "model", "from": "item.model" },
        { "to": "serialNumber", "const": null },
        { "to": "attributes.hasDeice", "from": "item.isDeIce", "default": false },
        { "to": "attributes.interfaces", "const": [] }
      ]
    }
  ]
}
```

## Notes

- The connector requires DataMiner version **10.3.0.0 - 12752** or higher.
- When using remote file paths, ensure the configured credentials have appropriate read/write permissions on the network shares.
- Output files are named by replacing the `_CC` suffix with `_CP` (e.g., `Name_CC.xml` generates `Name_CP.json`).
