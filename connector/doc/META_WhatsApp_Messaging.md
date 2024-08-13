---
uid: Connector_help_META_WhatsApp_Messaging
---

# META WhatsApp Messaging

The **META WhatsApp Messaging** connector acts as a link between the DataMiner system Alarm Console and the WhatsApp API, used for the users to receive the alarms they want directly on their WhatsApp apps.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 20.0                    |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses a HTTP connection and requires the following input during element creation:

##### HTTP CONNECTION

- **IP address/host**: The polling IP or URL of the destination. For this connector, it should be set to <https://graph.facebook.com>.
- **IP port**: The IP port of the destination. For this connector, it should be set to 443.

### Initialization

#### Prerequisites

##### 1. Register on Meta Developers platform

- Follow the steps described in the following page to register: <https://developers.facebook.com/docs/development/register>.
- Once registered, go to “*My Apps*” and then, press “*Create App*”.
- Select “*I don't want to connect a business portfolio yet*”.
- For use case, select “*Other*”.
- The app type should be “*Business*” in this case.
- Give a name to the app and attach an email to it.

##### 2. Create a Business Manager account

- Go to the Meta Business Suite <https://business.facebook.com/>.
- Create a new account by specifying a business name, the owner name, and the email desired to be associated with the business.
- Set the required details of the business.
- Confirm the business email address.

##### 3. Add WhatsApp to the App and send Test Message

- Back on the developer page, in the "*Add Products*" section, find WhatsApp and press "*Set up*".
- Go to the WhatsApp “*Quick Start*” and select the commercial portfolio you created in the previous step.
- In the “*API Configuration*” section, add a new recipient’s phone number.
- Enter the verification code you received in the recipient's WhatsApp app to verify the phone number.
- Select the recipient's phone number and send the test message by pressing the "*Send Message*" button.
- Save the "**Phone Number Identifier**" and the “**WhatsApp Business Account ID**” located just below the sender's number for later steps.

***Note that here you need to add all the recipient numbers to which you want to send the WhatsApp alarm notifications.**

##### 4. Create a System User

- Go to Meta Business Suite again (<https://business.facebook.com/>).
- In the *Users > System Users* section, add a new system user giving it a name and a role (*Employee* or *Admin*).
- Select the user you created, press the three dots button and select the “*Assign assets*”.
- Assign your app and give the user the appropriate permissions.
- Then press “*Generate token*”.
- Select the app.
- Choose the desired time for the token to expire (60 recommended for security).
- Assign the following permissions: *business_management, whats_app_business_messaging, whats_app_business_management*
- Save the **generated token** in a safe place, as it will be needed in later steps.

#### Installation

1. This connector should be installed along with the corresponding automation script (**META Alarm Detection**) through the installation package provided.
1. Create a new element running the recently added connector “**META WhatsApp Messaging**”.
    1. Set the IP Address/Host to **<https://graph.facebook.com>**.
    1. Set the IP Port to **443**.
1. Once the element is running, fill the *Phone Number ID, WhatsApp Business ID* and *Token* parameters in the *Configuration page* with the values previously saved.
1. Create a correlation rule.
    1. Set the alarm filter desired to trigger the correlation.
    1. Set an action to run the “**META Alarm Detection**” script recently included in the proper DMA.
1. In the Contacts table, add the phone numbers you want to receive WhatsApp alarm notifications. The number must start with the country code and exclude any non-numeric characters.

## How to use

- If everything went well with the installation and configuration, and an alarm occurs that matches the filtering criteria defined in the correlation rule, the people in the Contacts table should receive an alarm message in their WhatsApps informing about the generated alarm.
