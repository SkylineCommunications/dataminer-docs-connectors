---
uid: Connector_help_Orange_Orion
---

# Orange Orion

The Orange Orion connector facilitates the integration of Orange Orion platform into a DataMiner system. This connector enables users to configure and poll various endpoints from the Orion platform, retrieving and displaying information about remote devices, file status, and downloaded content.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial release. Supports basic API integration, including file download and authentication.         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     | -     |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

**HTTP CONNECTION**:

  - **IP address/host**: https://afi-obs.apibackbone.api.intraorange (the polling URL of the Orion platform).
  - **IP port**: 443 (default).

### Initialization

When you have created an element with this connector, you will need to configure the authentication and eFiles settings.

#### Authentication Settings

- **Client ID**: Input the client ID provided for API access.
- **Client Secret**: Input the client secret.
- **Maximum login retries**: This value is set to 3 by default but can be changed as needed.

#### eFiles Settings

- **eFiles Endpoint**: Define the eFiles endpoint (e.g., efiles_demo or efiles).
- **eFiles Polling Timer**: Set the interval at which the connector polls for new files.
- **Download Files URL**: Input the URL to download files from.

Once these fields are configured, the connector will use the credentials to request an authentication token. If the **Authorization Token Expiration** indicates that the token has expired, a new token will be requested automatically.

## How to use

The Orange Orion connector communicates with the Orion API via HTTP calls to authenticate, request files, and download data.

1. **Authentication Process**: The connector retrieves an authentication token using the **Client ID** and **Client Secret**. If the token expires, the system will automatically request a new one.

2. **File Download Process**: After authentication, the connector requests a list of files from the specified **eFiles Endpoint** and populates the **Files List** table with the results.

3. **JWT Token and File Retrieval**: For file download, the connector retrieves a JWT token and uses it with the operation IDs from the file list and the **Download Files URL** to send API requests for file downloads.

4. **File Status and Parsing**: Once a file is downloaded, the **Files List** table is updated with the download timestamp, and the contents of the file are parsed and added to the **Remotes Table**.

### Files List Page

The **Files List** page displays the status of files downloaded from the Orion platform, showing timestamps for when files were downloaded and allowing users to track the operation IDs used for API calls.