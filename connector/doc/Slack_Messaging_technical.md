---
uid: Connector_help_Slack_Messaging_technical
---

# Slack Messaging

## About

This connector links DataMiner with a Slack workspace through two HTTP connections: a **Web API** to the Slack Web API (polling) and a **WebSocket API** for real-time message delivery via Socket Mode. This allows two-way communication between DataMiner and Slack; DataMiner can send messages to Slack channels, while Slack users can message DataMiner to request information and trigger entire workflows.

**HTTP Web API** is used to communicate with the Slack API ([http://api.slack.com](http://api.slack.com/)), retrieving the list of users and conversations.

**Access tokens** are used to authenticate on the API. Such a token can be obtained from the app configuration webpage (see [Slack Application and Bot User Setup](#slack-application-and-bot-user-setup-version-110x-and-above)).

**HTTP WebSocket API** communication requires that Socket Mode is enabled for the Slack app and an **app-level token** is configured. **App-level tokens** can be obtained from the app configuration webpage. These must have the `connections:write` scope.

The WebSocket connection is used to notify DataMiner when users send messages using any of the built-in commands (e.g., **!list**) or custom commands that have been configured in the element. Each of these custom commands will trigger the execution of a predefined script in DataMiner (see [Automation Scripts](#automation-scripts)).

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

#### HTTP WebSocket API connection

This connector uses an HTTP (WebSocket) connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination. Must be `slack.com`.
- **IP port**: The IP port of the destination. Default: 443
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy.*

### Slack Application and Bot User Setup (Version 1.1.0.X and Above)

#### Authentication Setup

1. Go to <https://api.slack.com/apps> and click **Create New App**.

   ![Slack_Messaging_AppConfig_Step1.png](~/connector/images/Slack_Messaging_AppConfig_Step1.png)

1. Select to create your new app **From scratch**.

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
   - **channels:history** (for WebSocket data)
   - **im:history** (for WebSocket data)
   - **app_mentions:read** (for WebSocket data)
   - **im:history** (for use with the **Automation Scripts** table from direct messages with the bot)

   ![Slack_Messaging_AppConfig_Step5_Pt1.png](~/connector/images/Slack_Messaging_AppConfig_Step5_Pt1.png)

   ![Slack_Messaging_AppConfig_Step5_Pt2.png](~/connector/images/Slack_Messaging_AppConfig_Step5_Pt2.png)

1. On the **OAuth & Permissions** page, scroll to the **OAuth Tokens** section and click the **Install to {Insert your Workspace Name here}** button in green. Make sure to allow whatever app permissions it shows you on the next page.

   ![Slack_Messaging_AppConfig_Step6.png](~/connector/images/Slack_Messaging_AppConfig_Step6.png)

1. Copy the **Bot User OAuth Token** that now appears underneath **OAuth Token**, and put it under the **OAuth Access Token** parameter on the **Authentication** page of the Slack Messaging element.

   ![Slack_Messaging_AppConfig_Step7_Pt1.png](~/connector/images/Slack_Messaging_AppConfig_Step7_Pt1.png)

   ![Slack_Messaging_AppConfig_Step7_Pt2.png](~/connector/images/Slack_Messaging_AppConfig_Step7_Pt2.png)

#### WebSocket Setup

If you want to utilize tracked messages and run DataMiner automation scripts through Slack, you will need to follow the WebSocket setup steps below:

1. Go to **Event Subscriptions** > **Subscribe to bot events** and add the following events:

   - **app_mention**
   - **messages.channels**
   - **message.im**

   ![Slack_Messaging_AppConfig_Step8.png](~/connector/images/Slack_Messaging_AppConfig_Step8.png)

1. Go to **Socket Mode**, click the toggle button next to **Enable Socket Mode**, specify a token name (i.e., DataMiner Socket), and keep the scope set to **connections:write**.

   If you want to configure elements of the **App-Level Token** later, you can go to the **Basic Information** section on the Slack API to configure it.

   ![Slack_Messaging_AppConfig_Step9_Pt1.png](~/connector/images/Slack_Messaging_AppConfig_Step9_Pt1.png)

   ![Slack_Messaging_AppConfig_Step9_Pt2.png](~/connector/images/Slack_Messaging_AppConfig_Step9_Pt2.png)

1. Copy the Socket Token, go to the **Websocket** page of the Slack Messaging element in DataMiner, and enter the token under the **App-Level Token** parameter.

   ![Slack_Messaging_AppConfig_Step10.png](~/connector/images/Slack_Messaging_AppConfig_Step10.png)

1. On the Slack channels within your workspace where you want the bot to be present, go to the **channel settings**, select the **Integrations** tab, click **Add Apps**, and select the bot.

   ![Slack_Messaging_AppConfig_Step11.png](/connector/images/Slack_Messaging_AppConfig_Step11.png)

1. Finally, go to **Install App** and click the **Reinstall to {Workspace Name}** button for your WebSocket changes to take effect.

   ![Slack_Messaging_AppConfig_Step12.png](~/connector/images/Slack_Messaging_AppConfig_Step12.png)

The Slack Messaging element will now connect to the Slack API and the bot user will come online on your workspace.

## How to Use

Below you can find more information on how to use the different pages of the connector.

### General

This page displays general information on the Slack team to which the element is currently connected.

### Users

This page contains a table with all users that are part of the Slack team.

![Users.jpg](~/connector/images/Slack_Messaging_Users.jpg)

### Conversations

This page contains a table listing all possible conversations (public channels, private channels, instant messaging) that messages can be sent to. The **Send Message** column allows you to quickly send a message to a specific conversation. The last message received is shown in the **Last Message** column.

![Conversations.jpg](~/connector/images/Slack_Messaging_Conversations.jpg)

### Tracked Messages

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

On this page, the **App-Level Token** that should be used to connect to the Slack WebSocket must be configured. The page also contains some parameters that display the current status of the WebSocket connection.

![websocket.png](~/connector/images/Slack_Messaging_websocket.png)

### Web Interface

This page displays the app configuration page on the Slack API website, where you can log in with the account that created the app. Note that the web interface is only accessible when the client machine has network access to the product.

## Native Commands

List of native commands that are available in Slack when the bot is present in a channel. These commands can be invoked to interact with the bot and perform various actions.

### !List

Sends a list of all available commands to the Slack channel where the command was invoked.

## Additional Resources

- To find out more about how this connector can be used to unify your team's communication between DataMiner and Slack, check out the [Slack Messaging use case](https://community.dataminer.services/use-case/slack-messaging/) on DataMiner Dojo.

- If you want to send Slack messages or files through automation scripts, refer to [Sending Messages to Slack — Developer Guide](xref:Connector_help_Slack_Messaging_sending_messages_developer)
