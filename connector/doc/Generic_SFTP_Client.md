---
uid: Connector_help_Generic_SFTP_Client
---

# Generic SFTP Client

This connector can be used to access files from an SFTP server and copy them over to a local directory to be accessed by the DataMiner System. This way, you can prevent multiple connectors needing SFTP access logic, and you can keep that logic centralized.

## About

### Version Info

| Range   | Description     | DCF Integration | Cassandra Compliant |
|---------|-----------------|-----------------|---------------------|
| 1.0.0.x | Initial version | No              | Yes                 |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

Once the element has been created, in the **SFTP Configuration** section, fill in the **Host** and **Port** of the SFTP server and the **Username** for authentication.

The connector supports **Credentials** and **Key Pairs** authentication:

- If **Credentials** is selected, fill in the **Password** associated with the **Username**.
- If **Key Pairs** is selected, fill in the path to the key information file in the **Key Pairs Path** parameter.

In the **File Handling Overview** section, specify the **Source Directory Path** that will contain the files on the SFTP server that you want to copy over to the local directory. You can specify a root folder, and the connector will search through all the children folders for files and copy those over. Specify the local directory that will store the copied files in the **Destination Directory Path**. If a remote file directory is used, provide the **System Username** and **System Password** of a user that has access to the remote directory.

To validate the connection and copy all files, use the **Apply** button in the **SFTP Configuration** section. The **Connection Status** on the General page will update to *Connection Valid*.

### How to Use

To automatically copy all files from the SFTP server to the local directory, go to the **Configuration** page and specify the desired time interval in the **Automatic SFTP File Sync** parameter.

If the interval is set to *N/A*, you can use the **Apply** button to manually copy over the files.

The connector also has InterApp capabilities: an external connector can request files from the SFTP server using a file name filter and/or a file time filter. Once the SFTP client has copied all files matching the requested InterApp message filters, it will reply to the requested element with all the copied file names.
