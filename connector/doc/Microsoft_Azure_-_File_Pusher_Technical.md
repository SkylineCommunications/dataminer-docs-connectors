---
uid: Connector_help_Microsoft_Azure_-_File_Pusher_Technical_Page
---

# Microsoft Azure - Storage Accounts

## Description

Azure File Pusher connector is used to automate files synchronization from local storage to Azure Blob Storage. 
Azure File Pusher acts as an enhanced Azure Storage Upload wrapper, giving an easy and intuitive way to configure links between the local and Azure storages. It allows periodic uploads of local files to Azure Storage, where their content can be used for further analysis or online access.

Credentials for authentication are securely stored withing the collector, and used every time files are uploaded. Credentials can also be tested within the connector, to make sure a valid token for file uploads is received when authenticating.

You can configure multiple file path combinations, each with dedicated upload settings, allowing flexible file transfers to the Azure Storage that best fits your use case. File paths are added, edited or deleted through the right-click context menu in the File Paths table.

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection. However, it requires no input from the user regarding the connection configuration, but only Azure Storage credentials (Tenant ID, Client ID, and Client Secret) and Storage URL, to which the files are uploaded. 

## How to use

### General Page

On the **General** page, authentication parameters and storage URL are to be configured:
- Tenant ID: a unique identifier associated with an Azure Active Directory (Azure AD) instance that represents a specific organization or tenant in Azure's directory structure. It can be found in the Overview section of Azure Active Directory under the Tenant Information.
- Client ID, also known as Application ID, is a unique identifier assigned to an application registered in Azure Active Directory (Azure AD). It is linked to the application registered in Azure and can be found in the application overview.
- Client Secret: a password-like credential used by applications registered in Azure Active Directory (Azure AD) to securely authenticate.

- Blob Storage URL: the endpoint used to access resources within an Azure Storage account (e.g. https://dataminer.blob.core.windows.net).

**Test Authentication** button is used to test whether the provided credentials can retrieve the valid token used to access the blob storage. **Authentication Test** parameter indicates successful (OK) or unsuccessful (Error) authentication test.

### File Paths Page

**File Paths** page contains a File Paths table containing source-destination information and settings for file uploads. Table rows can be added, edited, or deleted through the right-click context menu.
- Source Path: Local absolute source path, from which the files are being uploaded.
- Container: Azure container name, relative to storage mentioned in the Storage URL parameter, to which files are uploaded.
- Custom Path Prefix: The prefix path, added to the original file path, when the file is uploaded to Azure..
- Timer: Timer defining a frequency of File Paths table row upload to Azure.
- Recursive: Defines if files in the source path are searched recursively in all directories or only in the top directory of the path.
- Overwrite: Defines if the same files that are already uploaded should be overwritten.
- Tries: Specifies the number of attempts to retry uploading a file if the initial upload fails.
- Auto Delete on Success: Delete successfully pushed files from the source path.
- Upload: Triggers upload of files from selected local path to container path.

**Upload All** button triggers upload of all files from File Paths table.

## Notes

For better user experience, this connector can be used together with the [**Microsoft Azure Cloud Platform**](xref:Connector_help_Microsoft_Azure) connector, which allows you to monitor relevant resource metrics available in Azure.
