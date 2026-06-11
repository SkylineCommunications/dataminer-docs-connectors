---
uid: Connector_help_Slack_Messaging_external_sets
---

# External sets

It's possible to utilize Automation Scripts to send messages, update previous messages, or send files to Slack. Below are the requirements for each of the types of sets. 

## Sending a Message

The connector provides the functionality to send a message from an external source in DataMiner (i.e., an automation script) to a channel in Slack. This can be done in two different ways:

### Simple XML

  - Perform a Set to the parameter with **ID 50** on a Slack Messaging Element.

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

### Raw JSON string

  - Perform a Set to the parameter with **ID 51** on a Slack Messaging Element.

  - Allows more advanced formatting and attachments.

  - Format: see <https://api.slack.com/methods/chat.postMessage>.

  - JSON is sent directly to the chat.postMessage WEB API method, without modifications.

## Update Previous Messages

From version 1.0.0.3 onwards, it is also possible to update a message that was previously sent to a Slack channel with a unique tag assigned:

  - Perform a Set to the parameter with **ID 52** on a Slack Messaging Element.

- Format is XML:

  ```xml
  <Message>
     <Tag>unique identifier of the message</Tag>
     <Text>new message</Text>
  </Message>
    ```

## Send a File

From version 1.1.0.1 onward, there is a new method of sending any file (i.e. images, documents) to Slack: 

  - Perform a Set to the parameter with **ID 40** on a Slack Messaging Element.

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