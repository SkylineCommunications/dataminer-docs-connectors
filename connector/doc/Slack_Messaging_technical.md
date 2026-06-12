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

#### Authentication Setup


1. Go to <https://api.slack.com/apps>.

![Slack_Messaging_AppConfig_Step1.png](/connector/images/Slack_Messaging_AppConfig_Step1.png)

1. Click **Create New App** and select to create it "**From scratch**".

![Slack_Messaging_AppConfig_Step2.png](/connector/images/Slack_Messaging_AppConfig_Step2.png)

1. Provide a name for the app (i.e., DataMiner), and select the workspace in which you want to integrate the app.

1. Click **Create App**.

![Slack_Messaging_AppConfig_Step3.png](/connector/images/Slack_Messaging_AppConfig_Step3.png)

1. Go to **OAuth & Permissions**, scroll down to **Bot Token Scopes**, and add the following OAuth Scopes:
  - **channels:read**
  - **chat:write**
  - **files:write**
  - **groups:read**
  - **im:read** 
  - **mpim:read** 
  - **users:read**
  - **channels:history** (For Websocket data)
  - **im:history** (For Websocket data)
  - **app_mentions:read** (For Websocket Data)
  - **im:history** (For use with the **Automation Scripts** table from direct messages with the bot)
  

![Slack_Messaging_AppConfig_Step5_Pt1.png](/connector/images/Slack_Messaging_AppConfig_Step5_Pt1.png)

![Slack_Messaging_AppConfig_Step5_Pt2.png](/connector/images/Slack_Messaging_AppConfig_Step5_Pt2.png)

1. On the **OAuth & Permissions** page, scroll to the **OAuth Tokens** section and click on the **Install to {Insert your Workspace Name here}** button in green. Make sure to allow whatever app permissions it shows you on the next page. 

![Slack_Messaging_AppConfig_Step6.png](/connector/images/Slack_Messaging_AppConfig_Step6.png)

1. Copy the **Bot User OAuth Token** that now appears underneath **OAuth Token**, and put it under the **OAuth Access Token** parameter on the **Authentication** page for the Slack Messaging element. 

![Slack_Messaging_AppConfig_Step7_Pt1.png](/connector/images/Slack_Messaging_AppConfig_Step7_Pt1.png)

![Slack_Messaging_AppConfig_Step7_Pt2.png](/connector/images/Slack_Messaging_AppConfig_Step7_Pt2.png)

#### Web Socket Setup

If you want to utilize Tracked Messages and active Automation Scripts through Slack, you will need to follow the Web Socket setup steps below:

1. Go to **Event Subscriptions**, go to **Subscribe to bot events** and add the following 3 events:
- **app_mention**
- **messages.channels**
- **message.im**

![Slack_Messaging_AppConfig_Step8.png](/connector/images/Slack_Messaging_AppConfig_Step8.png)


1. Go to **Socket Mode**, click on the toggle next to **Enable Socket Mode**, assign it a name (i.e., DataMiner Socket), and keep the scope **connection:write**. If you want to configure elements of the **App-Level Token** later, you can go to the **Basic Information** section on the Slack API to configure it. 

![Slack_Messaging_AppConfig_Step9_Pt1.png](/connector/images/Slack_Messaging_AppConfig_Step9_Pt1.png)

![Slack_Messaging_AppConfig_Step9_Pt2.png](/connector/images/Slack_Messaging_AppConfig_Step9_Pt2.png)

1. Copy the Socket Token and put it on the **App-Level Token** parameter on the **Websocket** page for the Slack Messaging Element. 

![Slack_Messaging_AppConfig_Step10.png](/connector/images/Slack_Messaging_AppConfig_Step10.png)

1. On the Slack channels within your Workspace that you want the bot present in, go to the **Channel's Settings**, go to **Integrations**, then click on **Add Apps** and select it. 

![Slack_Messaging_AppConfig_Step11.png](/connector/images/Slack_Messaging_AppConfig_Step11.png)


1. Finally, go to **Install App** and click the **Reinstall to {Workspace Name}** button for your Websocket changes to take affect. 

![Slack_Messaging_AppConfig_Step12.png](/connector/images/Slack_Messaging_AppConfig_Step12.png)

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

## Additional Resources

-  To find out more about how this connector can be used to unify your team's communication between DataMiner and Slack, check out the [Slack Messaging use case](https://community.dataminer.services/use-case/slack-messaging/) on DataMiner Dojo.

- If you want to send Slack messages or files through Automation Scripts, refer to [Sending Messages to Slack | Developer Guide](xref:Connector_help_Slack_Messaging_sending_messages_developer)

