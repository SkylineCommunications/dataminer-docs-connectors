---
uid: Connector_help_Microsoft_Azure_-_File_Pusher
---

# Microsoft Azure - File Pusher

## About

**Azure File Pusher** is used to enable periodic or manually triggered uploads of local files to Azure Blob Storage, where their content can be used for further analysis or online access. It helps automate file synchronization from local storage to Azure Blob Storage in an easy and intuitive way.

Credentials for authentication are securely stored within the collector and used every time files are uploaded.

As a safety measure to prevent file uploads from getting stuck, you can configure the number of failures or the duration after which the upload will be terminated on the configuration page.

You can configure multiple file path combinations, each with dedicated upload settings, allowing flexible file transfers to the Azure Blob Storage that best fits your use case.

> [!TIP]
> For a better user experience, this connector can be used together with the [**Microsoft Azure Cloud Platform**](xref:Connector_help_Microsoft_Azure) connector, which allows you to monitor relevant resource metrics available in Azure.

## Key Features

- Configure Azure Storage Authentication.

  ![General Page](~/connector/images/MicrosoftAzure_FilePusher_General_Page.png)

- Manage file path combinations and their configurations in the File Paths table.

  ![General Page](~/connector/images/MicrosoftAzure_FilePusher_Configuration_Page.png)

- Set the number of failures or the duration (in minutes) after which uploads will be terminated and considered failed.

  ![File Paths Page](~/connector/images/MicrosoftAzure_FilePusher_FilePaths_Page.png)

- Configure an upload interval for each file path combination.

- Configure upload options (*Overwrite*, *Recursive*, *Auto Delete on Success*, *Tries*) for each file path combination.

- Trigger a manual upload for one or all file path combinations.

## Prerequisites

To deploy this integration, you will need:

- DataMiner version **10.2.0 CU15 or higher**

> [!NOTE]
> For detailed technical information, refer to our [technical documentation page](xref:Connector_help_Microsoft_Azure_-_File_Pusher_Technical).
