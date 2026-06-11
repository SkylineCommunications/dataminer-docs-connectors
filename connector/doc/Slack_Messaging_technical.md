---
uid: Connector_help_Slack_Messaging_technical
---

# Slack Messaging

## About

This connector can be used to integrate Skyline DataMiner with a **Slack workspace**. It will communicate with Slack and ensure that the configured list of actions is executed. In order to keep this connector as general as possible, these actions are defined in **automation scripts**.

When commands are sent into a Slack channel, these will be picked up by the element running this connector. When the element detects a known command, it will execute the automation script linked to that command.

**HTTP communication** is used to communicate with the Slack API ([http://api.slack.com](http://api.slack.com/)). Two separate connections are made: one connection to the WEB API, and a second Web Socket connection.

The connector periodically retrieves the list of users and conversations via the WEB API (using polling), while messages that users send in a channel are pushed to the connector via the web socket interface.

**Access tokens** are used to authenticate on the API. Such a token can be obtained from the app configuration webpage (see [Installation and configuration](#installation-and-configuration)).

**WebSocket** communication requires that Socket Mode is enabled for the Slack app and an **app-level token** is configured. **App-level tokens** can be obtained from the app configuration webpage. These must have the `connections:write` scope.

Automation scripts that can be executed via Slack must have specific dummies and parameters (see [Automation Scripts](#automation-scripts)).

Users can use the `!list` command to retrieve an overview of all compatible and enabled scripts that can be executed. The command for each script can be customized on the **Automation Scripts** page.

> [!TIP]
> To find out more about how this connector can be used to unify your team's communication between DataMiner and Slack, check out the [Slack Messaging use case](https://community.dataminer.services/use-case/slack-messaging/) on DataMiner Dojo.

## Configuration

### Creation

#### HTTP WEB API connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination. Must be `slack.com`.
- **IP port**: The IP port of the destination, by default *443*.
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy.*

#### HTTP Web Socket API connection

This connector uses an HTTP (web socket) connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination. Must be `slack.com`.
- **IP port**: The IP port of the destination. Default: 443
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy.*

## Initialization

### Setting up the Slack Application and Bot User (Version 1.1.0.X and above)


1. Go to <https://api.slack.com/apps>.

![Slack_Messaging_AppConfig_Step1.png](~/connector/images/Slack_Messaging_AppConfig_Step1.png)

1. Click **Create New App** and select to create it "**From scratch**".

![Slack_Messaging_AppConfig_Step2.png](~/connector/images/Slack_Messaging_AppConfig_Step2.png)

1. Provide a name for the app (i.e., DataMiner), and select the workspace in which you want to integrate the app.

1. Click **Create App**.

![Slack_Messaging_AppConfig_Step3.png](~/connector/images/Slack_Messaging_AppConfig_Step3.png)

1. Go to **OAuth & Permissions**, scroll down to **Bot Token Scopes**, and add the following OAuth Scopes:
  - **channels:read**
  - **chat:write**
  - **files:write**
  - **groups:read**
  - **im:read** 
  - **mpim:read** 
  - **users:read**
  - **app_mentions:read** (For use with the **Automation Scripts** table from channels)
  - **im:history** (For use with the **Automation Scripts** table from direct messages with the bot)

![Slack_Messaging_AppConfig_Step5_Pt1.png](~/connector/images/Slack_Messaging_AppConfig_Step5_Pt1.png)

![Slack_Messaging_AppConfig_Step5_Pt2.png](~/connector/images/Slack_Messaging_AppConfig_Step5_Pt2.png)

1. On the **OAuth & Permissions** page, scroll to the **OAuth Tokens** section and click on the **Install to {Insert your Workspace Name here}** button in green. Make sure to allow whatever app permissions it shows you on the next page. 

![Slack_Messaging_AppConfig_Step6.png](~/connector/images/Slack_Messaging_AppConfig_Step6.png)

1. Copy the **Bot User OAuth Token** that now appears underneath **OAuth Token**, and put it under the **OAuth Access Token** parameter on the **Authentication** page for the Slack Messaging element. 

![Slack_Messaging_AppConfig_Step7_Pt1.png](~/connector/images/Slack_Messaging_AppConfig_Step7_Pt1.png)

![Slack_Messaging_AppConfig_Step7_Pt2.png](~/connector/images/Slack_Messaging_AppConfig_Step7_Pt2.png)

1. Go to **Socket Mode**, click on the toggle next to **Enable Socket Mode**, assign it a name (i.e., DataMiner Socket), and keep the scope **connection:write**

![Slack_Messaging_AppConfig_Step8_Pt1.png](~/connector/images/Slack_Messaging_AppConfig_Step8_Pt1.png)

![Slack_Messaging_AppConfig_Step8_Pt2.png](~/connector/images/Slack_Messaging_AppConfig_Step8_Pt2.png)

1. Copy the Socket Token and put it on the **App Level Token** parameter on the **Websocket** page for the Slack Messaging Element. 

![Slack_Messaging_AppConfig_Step9.png](~/connector/images/Slack_Messaging_AppConfig_Step9.png)

1. On the Slack channels within your Workspace that you want the bot present in, go to the **Channel's Settings**, go to **Integrations**, then click on **Add Apps** and select it. 

![Slack_Messaging_AppConfig_Step10.png](~/connector/images/Slack_Messaging_AppConfig_Step10.png)


The Slack Messaging Element will now connect to the Slack API and the bot user will come online on your workspace. 


## How to Use

Below you can find more information on how to use the different pages of the connector.

### General

This page displays general information on the Slack team to which the element is currently connected.

### Users

This page contains a table with all users that are part of the Slack team.

![Users.jpg](~/connector/images/Slack_Messaging_Users.jpg)

### Conversations

This page contains a table listing all possible conversations (public channels, private channels, instant messaging) that messages can be sent to. The "Send Message" column allows you to quickly send a message to a specific conversation. The last received message is shown in the "Last Message" column.

![Conversations.jpg](~/connector/images/Slack_Messaging_Conversations.jpg)


### Tracked Messages

Added in version 1.0.0.3.

This page contains a table with all tracked messages. These messages are linked with a unique tag (identifier), which can be used to update the message inside the Slack channel.

The number of days that messages should remain in the table can be customized.

### Automation Scripts

This page contains a table with all existing automation scripts in DataMiner that can be executed via commands in Slack.

![Scripts.jpg](~/connector/images/Slack_Messaging_Scripts.jpg)

To refresh the content of this table, use the **Refresh** button.

The **Description** column contains user-defined text that is presented when the list command is requested from a conversation.

In the **Command** column, a command can be assigned to each automation script. When a user sends one of these commands in one of the channels that include the bot, the connector will run the linked automation script. This allows the administrator to freely configure the name of the commands associated with each automation script.

The **State** column allows you to enable or disable the possibility to execute a particular script.

Only scripts that were adapted to be compatible with this Slack integration are shown in the table. In order for a script to be valid, it must have the following dummy and parameters:

- Dummy `SLACK`: The Slack DataMiner element that is executing the script.
- Parameter `CONVUSERNAME`: The end user name. This can be used by the script to reply with messages referring to the name of the Slack user that invoked a command.
- Parameter `CONVID`: The ID of the Slack conversation in which the command was invoked.
- Parameter `SLACKARGUMENTS`: The plain text after the command name that was provided by the Slack user when the command was invoked.

### Authentication

On this page, the **OAuth access token** that should be used to communicate with the Slack API must be configured. The page also contains some parameters that display the current status of the authentication.

![authentication.jpg](~/connector/images/Slack_Messaging_authentication.jpg)

### Websocket

On this page, the **App-Level Token** that should be used to connect to the Slack Web Socket must be configured. The page also contains some parameters that display the current status of the web socket connection.

![websocket.png](~/connector/images/Slack_Messaging_websocket.png)

### Web Interface

This page displays the app configuration page on the Slack API website which you can log into with the account that created the app. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.

## Notes

> [!TIP]
> To find out more about how this connector can be used to unify your team's communication between DataMiner and Slack, check out the [Slack Messaging use case](https://community.dataminer.services/use-case/slack-messaging/) on DataMiner Dojo.

### External sets

The connector provides the functionality to send a message from an external source in DataMiner (i.e., an automation script) to a channel in Slack. This can be done in two different ways:

- Simple XML:

  - Set to parameter with **ID 50**.

  - Only basic formatting.

  - Format is XML:

    ```xml
    <Message>
       <Channel>name or ID of the channel</Channel>
       <Text>the text to send to the channel</Text>
       <Tag>unique identifier</Tag>
    </Message>
    ```

  - The tag can be chosen by the sender to be able to uniquely identify the message. This can be used later to send an update of this message to the Slack channel.

- Raw JSON string:

  - Set to parameter with **ID 51**.

  - Allows more advanced formatting and attachments.

  - Format: see <https://api.slack.com/methods/chat.postMessage>.

  - JSON is sent directly to the chat.postMessage WEB API method, without modifications.

From version 1.0.0.3 onwards, it is also possible to update a message that was previously sent to a Slack channel with a unique tag assigned:

- Set to parameter with **ID 52**

- Format is XML:

  ```xml
  <Message>
     <Tag>unique identifier of the message</Tag>
     <Text>new message</Text>
  </Message>
    ```

From version 1.1.0.1 onward, there is a new method of sending any file (i.e. images, documents) to Slack: 

- Sending a File to Slack: 

  - Set to parameter with **ID 40**.

  - Format is a serialized JSON with this class:

    ```c#
     public class SlackFileRequest
    {
        // The path to your file. Please note that this path is specific to the DMA that's running your automation script
        public string FilePath { get; set; }
        // The name of your file
        public string FileName { get; set; }
        // The channel ID of the specific channel of the workspace you want to send the file to. This can be found from the "ID" column in the "Conversations" page on the Slack Messaging element or by viewing the Channel Details on Slack.
        public string ChannelId { get; set; }
    }
    ```