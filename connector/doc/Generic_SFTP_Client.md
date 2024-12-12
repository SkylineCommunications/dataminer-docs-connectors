---
uid: Connector_help_Generic_SFTP_Client
---

# Generic SFTP Client

This connector access files from an SFTP server and copies them over to a local directory to be accessed by the Dataminer system. This is to prevent multiple drivers needing SFTP access logic and keep that logic centralized.

## About

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|------------------|-----------------|---------------------|-------------------------|
| 1.0.0.x          | Initial version | No                  | Yes                     |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

Once element is created, fill in parameters in the **SFTP Configuration** section which contains the **Host** and **Port** of the SFTP server and the Username to authenticate access. The driver supports *Credentials* and *Key Pairs* authentication. If *Credentials* is selected, fill in the **Password** associated to the **Username**. If *Key Pairs* is selected, put the path with the key information file in the **Key Pairs Path**.

In the **File Handling Overview** section, put the **Source Directory Path** that will contain the files in the SFTP server that you wish to copy over to the local directory. You can put a root folder and the driver will search through all the children folders for files and copy those over. Put the local directory that will store the copied files in the **Destination Directory Path**. If using a remote file directory, provide the **System Username** and **System Password** to a user that has access to the remote directory.

To validate the connection and copy all files, hit the **Apply** button in the **SFTP Configuration** section. The **Connection Status** will update *Connection Valid* on the General page.

### How to Use

To automatically copy all files from the SFTP server to the local directory, put the time interval desired in the **Automatic SFTP File Sync** parameter in the **Configuration** page. If the interval is set to *N/A*, then you may hit the **Apply** button to manually copy over the files. The driver also has Interapp capabilites, where an external driver may request files from the SFTP server using a File name filter and/or a file time filter. Once the SFTP client copies all files matching the requested Interapp message filters, it will reply with all the file names copied over to the requested element.

### Redundancy

There is no redundancy defined.
