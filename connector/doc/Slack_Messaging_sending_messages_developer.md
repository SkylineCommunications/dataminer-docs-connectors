---
uid: Connector_help_Slack_Messaging_sending_messages_developer
---

# Sending Messages to Slack — Developer Guide

You can use automation scripts to send messages, update previous messages, or send files to Slack. The message format is customizable using the rich Slack API. Below are the requirements for each set type.

## Sending a Message

The connector provides the functionality to send a message from an external source in DataMiner (i.e., an automation script) to a channel in Slack. This can be done in two different ways, as explained below.

### Simple XML

- Perform a set on the parameter with **ID 50** of a Slack Messaging element.

- Use only basic formatting.

- Use XML format:

  ```xml
  <Message>
     <Channel>name or ID of the channel</Channel>
     <Text>the text to send to the channel</Text>
     <Tag>unique identifier</Tag>
  </Message>
  ```

- Choose a tag to make sure the message can be uniquely identified. This can be used later to send an update of this message to the Slack channel.

### Raw JSON string

- Perform a set on the parameter with **ID 51** of a Slack Messaging element.

- Allows more advanced formatting and attachments.

- JSON Format: see <https://api.slack.com/methods/chat.postMessage>.

- Message Format: see <https://docs.slack.dev/messaging/formatting-message-text/>

- JSON is sent directly to the chat.postMessage WEB API method, without modifications.

## Updating Previous Messages

From version 1.0.0.3 onwards, you can update a message that was previously sent to a Slack channel with a unique tag assigned:

- Perform a set on the parameter with **ID 52** of a Slack Messaging element.

- Use XML format:

  ```xml
  <Message>
     <Tag>unique identifier of the message</Tag>
     <Text>new message</Text>
  </Message>
    ```

## Sending a File

From version 1.1.0.1 onward, you can send any file (i.e., images, documents) to Slack:

- Perform a set on the parameter with **ID 40** of a Slack Messaging element.

- Use serialized JSON format with the following class:

    ```c#
     public class SlackFileRequest
    {
        // The path to your file. Please note that this path is specific to the DMA that is running your automation script
        public string FilePath { get; set; }

        // The name of your file
        public string FileName { get; set; }

        // The channel ID of the specific channel of the workspace you want to send the file to. This can be found from the "ID" column in the "Conversations" page on the Slack Messaging element or by viewing the Channel Details on Slack.
        public string ChannelId { get; set; }
    }
    ```
