---
uid: Connector_help_Generic_API_Listener_Technical
---

# Generic API Listener

## About

This connector provides the ability for users to listen for incoming API called from a user-defined address. The received request are processed and stored in table with all the meaningful data.

The user has the ability to forward the received request data for further processing, such as script defined on the DataMiner system.

## Configuration

### Connections

### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### General

On the following page the user is able to see a general **Status** parameter of the listener, which indicates whether the listener is currently active or not.

Underneath the **Status** parameter, the user is presented with the listener **API Configuration** parameters.

Following parameters are available for user to define:

- **API Mode**: This parameter allows the user to select the mode of the API listener. The options are:
  - **HTTP**: The listener will listen for HTTP requests.
  - **HTTPS**: The listener will listen for HTTPS requests. (For HTTPS request to function correctly the user needs to select the necessary certificate on subpage **Configuration**)
- **API Address**: The address on which the listener will listen for incoming requests. This is a read-only parameter which is composed of all the other configuration parameters.
- **API IP/Hostname**: The IP address or hostname on which the listener will listen for incoming requests.
- **API Path**: The path on which the listener will listen for incoming requests.
- **API Port**: The port on which the listener will listen for incoming requests.

At the bottom of the page, in the right corner there is a page button **Configuration** which opens a page with other configuration.

### Configuration

This page contains extra configuration the API listener supports.

#### HTTPS Certificates Configuration

Firstly, at the top of the page the user is able to select the **HTTPS Certificate** to be used for the HTTPS requests. The user can select a certificate from the list of available certificates on the DataMiner system.

> [!NOTE]
> The user needs to manually add the necessary certificates on the system.

Button to refresh the certificates is present underneath the certificate selection.

#### Script Configuration

Following the **HTTPS Certificates Configuration**, the user is able to select a **Script** which will be executed when **Execution Interval** has elapsed. The script can be used to process the request data or perform any other custom logic.
The user is able to select a script from all the of available scripts on the DataMiner system, as well as manually refresh the list by pressing the **Refresh** button.

Besides the script selection the user is also able to define the **Script Parameter Unprocessed Keys** parameter name. This parameter allows the user to specify which parameter in the script is going to accept the unprocessed keys from the request data table. The keys are passed to the script as a comma-separated list.
This parameter can be disabled as well.

Finally, the user can define the **Execution Interval** for the selected script. This parameter allows the user to specify how often the script is going to be executed.

#### Access Tokens

Lastly, the user is able to define **Access Tokens** which are used to authenticate the incoming requests. The user can add, edit or delete access tokens from the table of available access tokens.

Access token table contains the following columns:

- **Name**: The name of the access token.
- **Token**: The value of the access token.
- **Expiry Date**: The expiry date of the access token.

### Requests Data

This page contains a table with an overview of all received requests.

The table contains the following columns:

- **Received Id**: The unique identifier of the received request.
- **URL**: The URL of the received request.
- **HTTP Address**: The HTTP address of the received request.
- **HTTP Action**: The HTTP action of the received request.
- **HTTP Headers**: The HTTP headers of the received request.
- **HTTP Body**: The HTTP body of the received request.
- **Received Time**: The time when the request was received.
- **Status**: The status of the received request.
- **Action**: Button to delete the specific row from the table.

At the top-right corner, the **Clear Table** button can be used to clear data from the table.