---
uid: Connector_help_Skyline_Logical_Layer
---

# Skyline Logical Layer

With this connector you can subscribe on parameter values, parameter alarms, element alarms and view alarms in DataMiner.

These values are updated in real time, and you can define conditions that will be evaluated as soon as a change happens. The results of these conditions can then be reused in DataMiner.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | N/A                |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

## How to Use

To use this connector you will need to install the Skyline Logical Layer package. This package contains the connector and an Interactive Automation Script (IAS).
The script is used to fill in data in the tables of the element. It is an interactive script that helps you to easily select and populate the tables.

The first thing you will need to do in the script is define Parameter Value, Element Alarm or View Alarm Monitors. Next to that you can also define your own user-defined Static Variables which can be used to compare against in the Conditions. After that you will need to define conditions using these Monitors and Static Variables.

Once you have set up the element as detailed above it will show the following information:

- The **Conditions** page displays a table with the defined conditions and their result (True or False) and settings.
- The **Monitors** page displays three tables for the Parameter Value, Element Alarm, and View Alarm Monitors.
- The **User-Defined Variables** page displays a table with the defined Static Variables.
  
The connector supports **importing** CSV files in order to easily provision Monitors and Conditions.

### Adding/Editing/Deleting a Parameter Monitor

In this table you can define Monitors which can subscribe to a single parameter, so either on a standalone parameter or on a specific index of a table parameter.

On the Monitors page click the **Add Parameter Value Monitor** button. This will launch the IAS in which you can define the Parameter Monitor Name. Select an element from the Element Name drop-down list and a parameter from the Parameter Name drop-down list. In case the selected parameter is a table column an Index drop-down list will be displayed from which you must select the required index. Once done click Add and the Monitor will be added and its Value and (if applicable, i.e. for discreet parameters) Display Value will be displayed.
Note that you cannot add a Parameter Monitor which is already present (i.e. an Element/Parameter/Index combination which already exists as a Parameter Monitor). Note also that each Monitor name (across all Monitor tables) needs to be unique. If the Monitor name already exists in any of the three tables it will not be added.

In the Documentation column you can describe the particular usage of this Monitor.

To edit a Parameter Monitor right-click on the Parameter Monitor and select Edit item... from the context menu. This will open the IAS with the Paramter Monitor configuration which can then be modified. Once done click Update which will update the Parameter Monitor. Note that you cannot modify the Parameter Monitor name.

To delete one or more Parameter Monitors select one or more Parameter Monitors using the Shift or Ctrl keys and right-click and select Delete selected item(s) from the context menu. This will pop-up a confirmation window. Click OK if you are sure to delete the Monitor(s). In case however that any of the to be deleted Parameter Monitors is being used in a Condition none of the to be deleted Parameter Monitors will be deleted. So only Parameter Monitors which are not used in any Condition can be deleted.

### Adding/Editing/Deleting an Element Alarm Monitor

In this table you can define Alarm Monitors which can subscribe to an overall element alarm state or to a single parameter alarm state. Note that this of course requires the configuration of appropriate Alarm Templates monitoring the related element and/or parameters.

On the Monitors page click the **Add Element Alarm Monitor** button. This will launch the IAS in which you can define the Element Alarm Monitor Name. Select an element from the Element Name drop-down list. In case you want to create an Element Alarm Monitor for an overall element alarm state select [Element Alarm State] from the Parameter Name drop-down list. If you want to create an Element Alarm Monitor for a single parameter alarm state select one of the parameters from the Parameter drop-down list. Note that this list will only contain monitored parameters (i.e. which are being monitored by an Alarm Template). In case the selected parameter is a table column an Index drop-down list will be displayed from which you must select the required index. Once done click Add and the Element Alarm Monitor will be added and its alarm Value will be displayed.
Note that you cannot add an Element Alarm Monitor which is already present (i.e. an Element Alarm Level or Parameter/Index combination which already exists as an Element Alarm Monitor). Note also that each Monitor name (across all Monitor tables) needs to be unique. If the Monitor name already exists in any of the three tables it will not be added.

In the Documentation column you can describe the particular usage of this Monitor.

To edit an Element Alarm Monitor right-click on the Element Alarm Monitor and select Edit item... from the context menu. This will open the IAS with the Element Alarm Monitor configuration which can then be modified. Once done click Update which will update the Element Alarm Monitor. Note that you cannot modify the Element Alarm Monitor name.

To delete one or more Element Alarm Monitors select one or more Element Alarm Monitors using the Shift or Ctrl keys and right-click and select Delete selected item(s) from the context menu. This will pop-up a confirmation window. Click OK if you are sure to delete the Element Alarm Monitor(s). In case however that any of the to be deleted Element Alarm Monitors is being used in a Condition none of the to be deleted Element Alarm Monitors will be deleted. So only Element Alarm Monitors which are not used in any Condition can be deleted.

### Adding/Editing/Deleting a View Alarm Monitor

In this table you can define View Alarm Monitors which can subscribe to a view alarm state.

On the Monitors page click the **Add View Alarm Monitor** button. This will launch the IAS in which you can define the View Alarm Monitor Name. Select a view from the View Name drop-down list. Then select [View Alarm State] from the Parameter Name drop-down list. Once done click Add and the View Alarm Monitor will be added and its alarm Value will be displayed.
Note that you cannot add a View Alarm Monitor which is already present (i.e. a View which already exists as a View Alarm Monitor). Note also that each Monitor name (across all Monitor tables) needs to be unique. If the Monitor name already exists in any of the three tables it will not be added.

In the Documentation column you can describe the particular usage of this Monitor.

To edit a View Alarm Monitor right-click on the Element Alarm Monitor and select Edit item... from the context menu. This will open the IAS with the View Alarm Monitor configuration which can then be modified. Once done click Update which will update the View Alarm Monitor. Note that you cannot modify the View Alarm Monitor name.

To delete one or more View Alarm Monitors select one or more View Alarm Monitors using the Shift or Ctrl keys and right-click and select Delete selected item(s) from the context menu. This will pop-up a confirmation window. Click OK if you are sure to delete the View Alarm Monitor(s). In case however that any of the to be deleted View Alarm Monitors is being used in a Condition none of the to be deleted View Alarm Monitors will be deleted. So only View Alarm Monitors which are not used in any Condition can be deleted.

### Adding/Editing/Deleting a User-Defined Static Variable

In the Static Variables table you can define user-defined static variables which can be used in Conditions.

On the User-Defined Variables page click the **Add Static Variable** button. This will launch the IAS in which you can define the Static Variable Name and its Value. Once done click Add and the Static Variable will be added. If the Static Variable name already exists it will not be added.

In the Documentation column you can describe the particular usage of this Static Variable.

To edit a Static Variable Value just click on the pencil, modify the value and save it.

To delete one or more Static Variables select one or more Static Variables using the Shift or Ctrl keys and right-click and select Delete selected item(s) from the context menu. This will pop-up a confirmation window. Click OK if you are sure to delete the Static Variable(s). In case however that any of the to be deleted Static Variables is being used in a Condition none of the to be deleted Static Variables will be deleted. So only Static Variables which are not used in any Condition can be deleted.

### Adding/Editing/Deleting Conditions

In the Conditions table you can define Conditions.

On the Conditions page click the **Add Condition** button. This will launch the IAS in which you can define the Condition Name and the Condition. In the Condition definition you will use the Monitors as defined in the Monitors page. Note that you can easily navigate to these monitors with the IAS window open and right-click on a specific Monitor entry, select Other => Copy 'Monitor Name' and paste it in the Condition definition. This will prevent typos and speeds up the configuration. And it's great fun! Once done click Add and the Condition will be added and the Result will be updated to True or False. If the Condition name already exists it will not be added.
Note that no validation is done on the Condition definition and it is added as you defined it. The logic will only try to resolve it taking into account the expected correct syntax and the configured Monitors and Static Variables. If all is well the logic will resolve the Condition to True or False. If not it will result in Unknown or even possibly Infinite Loop. Most likely you then made a syntax error or made a typo in one of the monitor names or compare values.

Explain Visualize
Explain Corrective Action Text - Automatic Correction - Corrective Action Script - Owner - Timestamp

### Condition Syntax

Every comparison has to start with a `<` and closed with `>`. Any of the configured monitors can be used in a condition.

A typical comparison will compare a monitor against a value. This value can be a hardcoded numeric (integer or analog) or string value or a Display Value (if applicable for that monitor), an alarm severity (Normal, Warning, Minor, Major, Critical, Undefined) or a Static Variable (to be prefixed by a @ sign). Note that you cannot compare a monitor against another monitor.

Examples (everything between the `` represents a Condition definition, Number is a Parameter Monitor having a numeric value, State is a Parameter Monitor for a discreet value, RateAlarmState is an Element Alarm monitor for a parameter, IRDAlarmState is an Element Alarm Monitor for an element, MAX is a static variable):
- `<Number==5>`
- `<Number > 5.5>`
- `<Number > @MAX>`
- `<State == 1>`
- `<State == Running>`
- `<RateAlarmState == Major>`
- `<IRDAlarmState == Critical>`

The following operators can be used for comparisons:

- `=`
- `!`
- `<`
- `>`

You can also use the following combinations:

- `==`
- `!=`
- `<=`
- `>=`

Combining multiple comparisons is possible with the keywords `and`, `or`, and `not` (`not` will be translated to `and not`). Conditions can be reused inside other conditions. In this case you simply use the condition as such without comparing it against True or False. In order to invert a condition use an exclamation mark. Brackets are also supported in order to overrule the logical evaluation order.

Examples:

- `<Number==5>and<String==Test>`

- `<Number==5>not<ConditionName>` => Note that this can also be written as `<Number==5>and<!ConditionName>`

- `<String==Test>or<Discreet==Disconnected>`

- `(<Condition1> or <Condition2>) and <Condition3>`


### Import of Parameter Monitors

By Importing Parameter Monitors you can easily create large amounts of new Parameter Monitors by copy/pasting/editing existing ones. This is very effective in case you need to define similar monitors for different elements or for multiple indexes. Note that an import will never modify or delete any of the existing monitors.

The easiest way to start using the Parameter Monitor import functionality is to first create a number Parameter Monitors as described above. Then perform a standard table export of the Parameter Value Monitors table by right clicking on a table entry, then select Other and then Export table.... Choose an Export location by browsing to a folder and defining a File name (for example TheMonitors.csv) and click Save. Tick the Include hidden columns check-box and click on Export.
Now you can edit the file by removing all but one of the present monitors. Edit the first monitor by removing the first value which is the Key (do not remove the first comma. Now edit the Name (second column), if needed the Documentation (third column), the Element (fourth column), the Parameter (fifth column) and if needed the Index (sixth column).
Now upload the file to the DataMiner Documents under the Skyline Logical Layer protocol folder (if it is not yet present add it first).
Now click the Import Parameters... button on the Monitors page and enter the full path into the Parameter CSV File Path (here this will be C:\Skyline DataMiner\Documents\Skyline Logical Layer\TheMonitors.csv). Now click the Import Parameters button. This should add all the defined monitors. Note that no validation is done on the imported monitors and that it is the responsability of the user to verify if what he/she/they/ze/xe import is correct (so that the element, parameter and index exist). The only checks that are done are to prevent that existing monitors would get corrupted (i.e. changed or get duplicated). In any case when importing monitors it is good practice to always check the element logging and verify if there are no errors being reported. Also check on the Parameter Value Monitors table if all expected monitors have been added and if they obtain a valid Value. Only in this way you can be sure the the import was fully successful.

### Import of Condition Monitors

Proceed in the same way as for the import of Parameter Monitors editing at minimum the Name (second column) and Condition (fourth column). Also here no validation is being performed. The only thing which is prevented is to overwrite or delete existing conditions.
