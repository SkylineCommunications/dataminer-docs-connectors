---
uid: Connector_help_META_WhatsApp_Messaging
---

# META WhatsApp Messaging

The META WhatsApp Messaging connector acts as a link between the DataMiner System Alarm Console and the WhatsApp API. It allows users to receive the alarms they want directly in their WhatsApp apps.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 20.0                   |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination. For this connector, it should be set to `https://graph.facebook.com`.
- **IP port**: The IP port of the destination. For this connector, it should be set to 443.

### Initialization

#### Prerequisites

##### 1. Register on the Meta Developers Platform

1. Follow the steps on the following page to register: <https://developers.facebook.com/docs/development/register>.
1. When you have registered, go to *My Apps* and then click *Create App*.
1. Select *I don't want to connect a business portfolio yet*.
1. As the use case, select *Other*.
1. Make sure the app type is set to *Business*.
1. Specify a name for the app and attach an email address to it.

##### 2. Create a Business Manager Account

1. Go to the Meta Business Suite at <https://business.facebook.com/>.
1. Create a new account by specifying a business name, the owner name, and the email that should be associated with the business.
1. Set the required details of the business.
1. Confirm the business email address.

##### 3. Add WhatsApp to the App and Send a Test Message

1. Back on the developer page, in the *Add Products* section, locate WhatsApp, and click *Set up*.
1. Go to the WhatsApp *Quick Start* and select the commercial portfolio you created in the previous step.
1. In the *API Configuration* section, add a new recipient’s phone number.
1. Enter the verification code you received in the recipient's WhatsApp app to verify the phone number.
1. Select the recipient's phone number and send the test message by clicking the *Send Message* button.
1. Save the **Phone Number Identifier** and the **WhatsApp Business Account ID** located just below the sender's number for later steps.

> [!NOTE]
> At this point, make sure to add all the recipient numbers to which you want to send the WhatsApp alarm notifications.

##### 4. Create a System User

1. Go to the Meta Business Suite again (at <https://business.facebook.com/>).
1. In the *Users > System Users* section, add a new system user, specifying a name and a role (*Employee* or *Admin*).
1. Select the user you created, click the "..." button, and select *Assign assets*.
1. Assign your app and give the user the appropriate permissions.
1. Click *Generate token*.
1. Select the app.
1. Select the desired time for the token to expire (for security reasons, 60 is recommended).
1. Assign the following permissions: *business_management*, *whats_app_business_messaging*, *whats_app_business_management*.
1. Save the **generated token** in a safe place, as it will be needed in later steps.

#### Installation

1. Install this connector along with the corresponding Automation script (META Alarm Detection) using the installation package.
1. Create a new element running the **META WhatsApp Messaging** connector.
   1. Set the IP address/host to `https://graph.facebook.com`.
   1. Set the IP Port to `443`.
1. Once the element is running, fill in the *Phone Number ID*, *WhatsApp Business ID*, and *Token* parameters on the **Configuration** page with the values you saved earlier.
1. Create a Correlation rule. For more information, see [DataMiner Correlation](https://aka.dataminer.services/Correlation) or the [Orchestration & Automation learning course](https://community.dataminer.services/learning/courses/orchestration-automation/).
   1. Set the alarm filter that should trigger the rule.
   1. Set an action to run the **META Alarm Detection** script, which you installed earlier.
1. In the Contacts table, add the phone numbers that should receive WhatsApp alarm notifications.

   The numbers must start with the country code and exclude any non-numeric characters.

## How to Use

If everything went well during the installation and configuration, and an alarm occurs that matches the filtering criteria defined in the Correlation rule, the people in the Contacts table will receive an alarm message in their WhatsApp apps, informing them about the generated alarm.
