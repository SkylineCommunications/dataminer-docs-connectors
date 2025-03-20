---
uid: Connector_help_InfluxData_Kapacitor
---

# InfluxData Kapacitor

Underneath the title of the help page, add one short paragraph in which you describe the **function of the connector**.
Try to also include some **information about the data source**. Note that if you copy this information from the vendor website, you may need to change it a little so it fits in an informative context rather than a marketing context (e.g. remove meaningless praise like "best-of-breed", "top-of-the-line", etc.).

## About

### Version Info

**This subsection can only be omitted for an exported connector**

In this subsection, insert a table with four columns, listing the different ranges of the connector. In the second column, add a short **description** of the key new features or improvements versus the previous "based on" version:

- What has been changed.
- Why has it been changed.

The last column must indicate what the impact will be on the system when the user updates from an older range to this range:

- What is the impact on the system.
- Which actions have to be taken.

In case the explanation of what has been changed and which actions need to be taken is too long to fit in the table, refer to the "Notes" section of the help page for further information.

In the following example, the initial version had the range 1.0.0.x. A new firmware version was no longer compatible with the initial connector range, so a new range was created: 1.1.0.x. Based on this firmware, a branch (custom version) was made: 2.1.0.x. That version also got new firmware that was no longer compatible with previous versions: 2.2.0.x.

In the Range column, you must indicate which range is the **main range** of the connector and is being maintained by default at SLC, by adding **[SLC Main]**. This is also the range that should be used by default for any new installation. In the example below, the 1.1.1.x branch is the main range.

In case a specific range/branch was created and should **no longer be used**, indicate this by adding **[Obsolete]** in the Range column. Only add [Obsolete] in case there is an approved reason for no longer maintaining this range.

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Feature1</li><li>Feature2</li></ul>         |-         |-         |

### Product Info

**This subsection can only be omitted for a virtual connector**

In this subsection, insert a table with two columns. In the table, list the firmware versions that are fully compatible with the connector, together with the connector ranges. If multiple firmware versions are compatible with one connector range, add them in the same row, but on different lines.

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |2.9.2.r1.588         |

> [!NOTE]
> For a **parent DVE** connector, the parent help should mention the firmware of the "Main device", e.g. the chassis. The help for a derived DVE should mention the firmware of the device it represents, e.g. the card. In case the DVE is not a different or real device, it should contain the same overview as the parent element.

### System Info

In this subsection, insert a table with five columns. Indicate whether the range features **DCF integration** and whether it is **Cassandra compliant**.

In the "Linked Components"; column, list all DataMiner components that have a link, in any way, with this connector range, e.g. mediation connectors, Automation scripts, custom report, etc.

In the "Exported Components" column, list all the connectors that are exported by the parent connector in question.
**This can only be omitted for an exported connector or for a connector that cannot have exported connectors.**

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination.]
  - **Device address**: [The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.]


### Initialization

Indicate if additional configuration of parameters is necessary in a newly created element.

### Redundancy

There is no redundancy defined.



## How to use

In this section, provide a more detailed description of **how the connector functions**.

Also specify the **communication method**. Example: "SOAP calls are used to retrieve the device information. SNMP traps can be retrieved when this is enabled on the device."

It must be clearly mentioned in case no data traffic will be seen in the **Stream Viewer**.

Note:

- In case of a parent connector (e.g. DVE), mention that it exports connectors. Example: "This connector will export different connectors based on the retrieved data. A list can be found under 'Exported Components'.
- In case of a child connector (e.g. DVE), refer to the parent connector. Example: "This connector is automatically generated by connector ZZZZZZ range A.B.C.X"

Make sure you always specify something in this section, keeping in mind what users may be looking for when they consult the help page. This should **not** be just an enumeration of the different pages and parameters, because users can see that just by looking at the element. Instead, the focus must be on what users can/should do with the connector. To figure out what should be included, these questions can help you:

- Which information is the most important for the users and where can they find it?
- Are there any parameters of which the purpose isn't obvious?
- If the connector allows configuration, which settings are the most important?
- Are there any potential problems that users should watch out for?

### Examples

For a really simple connector that contains only one "General" page with a couple of read-only parameters, you can write something like this:

*You can find all the information you need to monitor [the data source in question] on the General data page.*

For a relatively simple connector with a couple of pages, you can mention the most important pages and what their purpose is. For example:

*On the **General** page of this connector, you can configure the username and password to access the device.*

*The **Instance Settings** page contains basic information about the existing instances, as well as specific logs for every instance. This page has multiple subpages, which can among others be used to add new instances or edit existing ones.*

If you need to add more than just a couple of lines of text because the connector is quite complicated or you need to go into a lot of detail for some of the features, use **subtitles** (using the same format as the "Examples" subtitle above: Heading 3 with Accent 1) to create structure in your text. These subtitles can either reflect the different pages you want to discuss, or the different topics, e.g. General settings, Import and export, Logging.


## Notes

In this section, you can provide additional information about the connector that does not fit in the other sections. Remove this section if it does not contain any info.
