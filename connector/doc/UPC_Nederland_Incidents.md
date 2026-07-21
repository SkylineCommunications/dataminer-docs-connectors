---
uid: Connector_help_UPC_Nederland_Incidents
---

# UPC Nederland Incidents

## About

This connector shows a table listing the elements for which the **Event Property** trap is set to *Yes*.

The table will be populated automatically in two situations:

- **Automatically**: For each alarm in the system where the alarm property was set to **Yes**, which is done via a correlation rule (CR)/automation script (AS).
- **Manually**: An information event created manually that will follow the same flow as explained before, done via a specific Visio file that will load an interactive automation script (IAS). It will ask for the event details.

## Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

## Usage

### General

On the General page, you have access to the **Alarm Information** table. Also available is the **Command Parameter**. It shows the information about the **Alarm/Information Event** that was generated.

The **Properties Set Interactively** parameter is set with the details that will be asked in the IAS.

To test adding a row with static information use the **Generate Static Alarm To Test** parameter. First create an **alarm template** on top of this parameter. Then create a **CR** that will trigger on the generated alarm. Set the **CR Action** to trigger the **Add Static Row To Table AS**.

## Notes

This connector works in conjunction with two automation scripts and one correlation rules. They are the **Add Static Row To Table** and the **Create Alarm**.
