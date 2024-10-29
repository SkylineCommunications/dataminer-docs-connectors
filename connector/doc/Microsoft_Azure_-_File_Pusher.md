---
uid: Connector_help_Microsoft_Azure_-_File_Pusher
---

# Microsoft Azure - File Pusher

## About

**Azure File Pusher** is used to enable periodic or manually triggered uploads of local files to Azure Blob Storage, where their content can be used for further analysis or online access. It helps automate file synchronization from local storage to Azure Blob Storage in an easy and intuitive way.
<br>
<br>
Credentials for authentication are securely stored within the collector, and used every time files are uploaded.
<br>
You can configure multiple file path combinations, each with dedicated upload settings, allowing flexible file transfers to the Azure Blob Storage that best fits your use case.
<br>
<br>
For the detailed technical information, please refer to our technical documentation [page](Connector_help_Microsoft_Azure_-_File_Pusher_Technical.md).

## Key Features

- Configure Azure Storage Authentication.
<br>
![General Page](~/connector/images/MicrosoftAzure_FilePusher_General_Page.png "General")<br>
- Add, edit, and delete source and remote file path pairs in the File Paths table.
![File Paths Page](~/connector/images/MicrosoftAzure_FilePusher_FilePaths_Page.PNG "File Paths")<br>
- Configure upload interval for each pair.
- Configure upload options (Overwrite, Recursive, Auto Delete on Success, Tries) for each pair.
- Trigger manual upload for one or all pairs.

## Prerequisites
To deploy this integration, you’ll need:

- DataMiner version 10.2.0.14 or higher

## Notes

For better user experience, this connector can be used together with the [**Microsoft Azure Cloud Platform**](xref:Connector_help_Microsoft_Azure) connector, which allows you to monitor relevant resource metrics available in Azure.
