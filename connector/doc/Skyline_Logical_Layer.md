---
uid: Connector_help_Skyline_Logical_Layer
---

# Skyline Logical Layer

With this connector, you can subscribe on parameter values, parameter alarms, element alarms, and view alarms in DataMiner.

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

To use this connector, you will need to install the Skyline Logical Layer package. This package contains the connector and an interactive Automation script (IAS). The script is used to fill in data in the tables of the element. It is an interactive script that helps you to easily select and populate the tables.

The first thing you will need to do in the script is define parameter value, element alarm, or view alarm monitors. Next to that, you can also define your own user-defined static variables, which can be used to compare against in the conditions. After that, you will need to define conditions using these monitors and static variables.

Once you have set up the element as detailed above, it will show the following information:

- The **Conditions** page displays a table with the defined conditions and their result (*True* or *False*) and settings.
- The **Monitors** page displays three tables for the parameter value, element alarm, and view alarm monitors.
- The **User-Defined Variables** page displays a table with the defined static variables.
  
The connector supports **importing** CSV files in order to easily provision monitors and conditions.

### Adding/Editing/Deleting a Parameter Monitor

In the **Parameter Value Monitors** table, you can define monitors that can subscribe to a single parameter. This can be either a standalone parameter or a specific index of a table parameter.

To **add** a parameter monitor:

1. On the **Monitors** page, click the **Add Parameter Value Monitor** button.

   This will open an IAS in a pop-up window.

1. In the pop-up window, define the parameter monitor name.

1. Select an element from the **Element Name** dropdown list and a parameter from the **Parameter Name** dropdown list.

1. In case the selected parameter is a table column, select the required index in the **Index** drop-down list.

1. Click **Add**.

   The monitor will be added and its value and (if applicable, i.e. for discrete parameters) display value will be displayed.

> [!NOTE]
>
> - You cannot add a parameter monitor that is already present (i.e. an element/parameter/index combination that already exists as a parameter monitor).
> - Each monitor name (across all monitor tables) needs to be unique. If the monitor name already exists in any of the three tables, it will not be added.

In the **Documentation** column, you can describe the particular usage of this monitor.

To **edit** a parameter monitor:

1. Right-click the parameter monitor and select **Edit item** in the context menu.

1. In the pop-up window, modify the parameter monitor configuration as necessary.

1. Click **Update**.

> [!NOTE]
> It is not possible to modify a parameter monitor name.

To **delete** one or more parameter monitors:

1. Select the parameter monitor(s) you want to delete.

   Use the Shift or Ctrl keys in case you want to select several parameter monitors.

1. Right-click your selection and select **Delete selected item(s)** in the context menu.

1. In the confirmation box, click **OK** if you are sure you want to delete the selected items.

> [!NOTE]
> Only parameter monitors that are not used in any condition can be deleted. If you try to delete parameter monitors, and one or more of the selected parameter monitors is used in a condition, none of the selected parameter monitors will be deleted. In such a case, a pop-up message will be displayed clearly indicating this.

### Adding/Editing/Deleting an Element Alarm Monitor

In the **Element Alarm Monitors** table, you can define alarm monitors, which can subscribe to an overall element alarm state or to a single parameter alarm state. Note that this requires the configuration of appropriate alarm templates that monitor the related element and/or parameters.

To **add** an element alarm monitor:

1. On the **Monitors** page, click the **Add Element Alarm Monitor** button.

   This will open an IAS in a pop-up window.

1. In the pop-up window, define the element alarm monitor name.

1. Select an element from the **Element Name** dropdown list.

1. In the **Parameter Name** dropdown list:

   - If you want to create an element alarm monitor for an overall element alarm state, select **[Element Alarm State]**.

   - If you want to create an element alarm monitor for a single parameter alarm state, select one of the parameters.

     The list will only contain monitored parameters (i.e. parameters that are monitored based on an alarm template).

1. If you have selected a table column parameter, in the **Index** dropdown list, select the required index.

1. Click **Add**.

   The element alarm monitor will be added and its alarm value will be displayed.

> [!NOTE]
>
> - It is not possible to add an element alarm monitor that is already present (i.e. an element alarm level or parameter/index combination that already exists as an element alarm monitor).
> - Each monitor name (across all monitor tables) needs to be unique. If a monitor name already exists in any of the three tables, it will not be added.

In the **Documentation** column, you can describe the particular usage of this monitor.

To **edit** an element alarm monitor:

1. Right-click the element alarm monitor and select **Edit item** in the context menu.

1. In the pop-up window, modify the element alarm monitor configuration as necessary.

1. Click **Update**.

> [!NOTE]
> It is not possible to modify an element alarm monitor name.

To **delete** one or more element alarm monitors:

1. Select the element alarm monitor(s) you want to delete.

   Use the Shift or Ctrl keys in case you want to select several element alarm monitors.

1. Right-click your selection and select **Delete selected item(s)** in the context menu.

1. In the confirmation box, click **OK** if you are sure you want to delete the selected items.

> [!NOTE]
> Only element alarm monitors that are not used in any condition can be deleted. If you try to delete element alarm monitors, and one or more of the selected element alarm monitors is used in a condition, none of the selected element alarm monitors will be deleted. In such a case, a pop-up message will be displayed clearly indicating this.

### Adding/Editing/Deleting a View Alarm Monitor

In the **View Alarm Monitors** table, you can define view alarm monitors, which can subscribe to a view alarm state.

To **add** a view alarm monitor:

1. On the **Monitors** page, click the **Add View Alarm Monitor** button.

   This will open an IAS in a pop-up window.

1. In the pop-up window, define the view alarm monitor name.

1. In the **View Name** dropdown list, select a view.

1. In the **Parameter Name** dropdown list, select **[View Alarm State]**.

1. Click **Add**.

   The view alarm monitor will be added and its alarm value will be displayed.

> [!NOTE]
>
> - It is not possible to add a view alarm monitor that is already present (i.e. a view that already exists as a view alarm monitor).
> - Each monitor name (across all monitor tables) needs to be unique. If a monitor name already exists in any of the three tables, it will not be added.

In the **Documentation** column, you can describe the particular usage of this monitor.

To **edit** a view alarm monitor:

1. Right-click the view alarm monitor and select **Edit item** in the context menu.

1. In the pop-up window, modify the view alarm monitor configuration as necessary.

1. Click **Update**.

> [!NOTE]
> It is not possible to modify an view alarm monitor name.

To **delete** one or more view alarm monitors:

1. Select the view alarm monitor(s) you want to delete.

   Use the Shift or Ctrl keys in case you want to select several view alarm monitors.

1. Right-click your selection and select **Delete selected item(s)** in the context menu.

1. In the confirmation box, click **OK** if you are sure you want to delete the selected items.

> [!NOTE]
> Only view alarm monitors that are not used in any condition can be deleted. If you try to delete view alarm monitors, and one or more of the selected view alarm monitors is used in a condition, none of the selected view alarm monitors will be deleted. In such a case, a pop-up message will be displayed clearly indicating this.

### Adding/Editing/Deleting a User-Defined Static Variable

In the **Static Variables** table, you can define user-defined static variables that can be used in conditions.

To **add** a static variable:

1. On the **User-Defined Variables** page, click the **Add Static Variable** button.

   This will open an IAS in a pop-up window.

1. In the pop-up window, define the name and value of the static variable.

1. Click **Add**.

> [!NOTE]
> The static variable will only be added if the static variable name you defined does not exist yet.

In the **Documentation** column, you can describe the particular usage of this monitor.

To **edit** a static variable value, click the pencil icon, modify the value, and save it.

To **delete** one or more static variables:

1. Select the static variable(s) you want to delete.

   Use the Shift or Ctrl keys in case you want to select several static variables.

1. Right-click your selection and select **Delete selected item(s)** in the context menu.

1. In the confirmation box, click **OK** if you are sure you want to delete the selected items.

> [!NOTE]
> Only static variables that are not used in any condition can be deleted. If you try to delete static variables, and one or more of the selected static variables is used in a condition, none of the selected static variables will be deleted. In such a case a popup message will be displayed clearly indicating this.

### Adding/Editing/Deleting Conditions

In the **Conditions** table, you can define conditions.

To **add** a condition:

1. On the **Conditions** page, click the **Add Condition** button.

   This will open an IAS in a pop-up window.

1. In the pop-up window, define the name of the condition.

1. Configure the condition itself, using the monitors defined on the Monitors page.

   While the IAS window is open, you can navigate to these monitors, right-click a specific monitor entry, select **Other => Copy 'Monitor Name'**, and then paste it in the condition definition. This will prevent typos and speeds up the configuration.

1. Optionally, set the **Visualize** option to *No*. This option can be used to for example conditionally show or hide the condition in Visual Overview.

1. Set the **Corrective Action Script** to an Automation script that exists in the system. This is the script that will be executed if the condition is evaluated as true.

   > [!NOTE]
   >
   > - In order for the corrective action script to be executed automatically when the condition is evaluated as true, the **Automatic Correction** parameter needs to be enabled in the Conditions table. This parameter cannot be configured in the pop-up window, but must be configured directly in the table.
   - A template corrective action script is provided in the Logical Layer install package. You can use this template to start developing your own scripts. The condition name is passed to the Automation script as an argument, so when you set up the corrective action scripts, you can reuse a single script but act differently depending on the provided condition name.

1. Click Add.

   The condition will be added, and the result will be updated to *True* or *False*. A timestamp indicates the last time when the result of the condition was updated.

> [!NOTE]
>
> - The condition will only be added if the condition name you defined does not exist yet.
> - No validation is done on the condition definition, and it is added as you defined it. The logic will only try to resolve it taking into account the expected correct syntax and the configured monitors and static variables. If all is well, the logic will resolve the condition to *True* or *False*. Otherwise, it will result in *Unknown* or even possibly *Infinite Loop*. If this happens, you have most likely made a syntax error or a typo in one of the monitor names or compare values.
> - A condition entry also contains some additional parameters that can only be edited directly in the Conditions table, but not via the pop-up window, such as the Automatic Correction, Corrective Action Text, and Owner parameter. You can for example use the Corrective Action Text parameter to conditionally display text in Visual Overview in case the condition is evaluated as true, and the Owner parameter can for example refer to the person responsible for the configuration and maintenance of this condition.

In the **Documentation** column, you can describe the particular usage of this monitor.

To **edit** a condition:

1. Right-click the condition and select **Edit item** in the context menu.

1. In the pop-up window, modify the condition configuration as necessary.

1. Click **Update**.

> [!NOTE]
> It is not possible to modify a condition name.

To **delete** one or more conditions:

1. Select the conditions(s) you want to delete.

   Use the Shift or Ctrl keys in case you want to select several conditions.

1. Right-click your selection and select **Delete selected item(s)** in the context menu.

1. In the confirmation box, click **OK** if you are sure you want to delete the selected items.

> [!NOTE]
> Only conditions that are not used in any other (selected or not selected) condition can be deleted. If you try to delete conditions, and one or more of the selected conditions is used in another condition, none of the selected conditions will be deleted. In such a case, a pop-up message will be displayed clearly indicating this.

### Condition Syntax

Every comparison has to start with `<` and end with `>`. Any of the configured monitors can be used in a condition.

A typical comparison will compare a monitor against a value. This value can be a hard-coded numeric (integer or analog) or string value or a display value (if applicable for that monitor), an alarm severity (*Normal*, *Warning*, *Minor*, *Major*, *Critical*, *Undefined*), or a static variable (to be prefixed by an @ sign). Note that you cannot compare a monitor against another monitor.

The **examples** below show condition definitions where `Number` is a parameter monitor with a numeric value, `State` is a parameter monitor for a discrete value, `RateAlarmState` is an element alarm monitor for a parameter, `IRDAlarmState` is an element alarm monitor for an element, and `MAX` is a static variable:

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

Combining multiple comparisons is possible with the keywords `and`, `or`, and `not` (`not` will be translated to `and not`). Conditions can be reused inside other conditions. In this case, you use the condition as it is without comparing it against *True* or *False*. In order to invert a condition, use an exclamation mark. Brackets are also supported in order to overrule the logical evaluation order.

Examples:

- `<Number==5>and<String==Test>`

- `<Number==5>not<ConditionName>`

  This can also be written as `<Number==5>and<!ConditionName>`

- `<String==Test>or<Discreet==Disconnected>`

- `(<Condition1> or <Condition2>) and <Condition3>`

### Importing Parameter Monitors

By importing parameter monitors, you can easily create a large number of new parameter monitors by copy-pasting/editing existing ones. This is very effective in case you need to define similar monitors for different elements or for multiple indexes. Note that an import will never modify or delete any of the existing monitors.

1. Start by creating a number of parameter monitors as described above.

1. Right-click an entry in the **Parameter Value Monitors** table and select **Other** > **Export table**.

1. Select an export location by browsing to a folder and defining a file name (e.g. *TheMonitors.csv*).

1. Click **Save**.

1. Select the **Include hidden columns** checkbox.

1. Click **Export**.

1. Edit the file:

   1. Remove all but one of the monitors present in the file.

   1. Edit the first monitor by removing the first value, which is the key.

      > [!IMPORTANT]
      > Do not remove the first comma.

   1. Edit the Name value (second column), if needed the Documentation value (third column), the Element value (fourth column), the Parameter value (fifth column), and if needed the Index value (sixth column).

   1. Save the file.

1. Upload the file to the Skyline Logical Layer protocol folder within the DataMiner Documents folder.

   If this protocol folder does not exist yet, add it first.

1. On the **Monitors** page, click **Import Parameters**.

1. In the **Parameter CSV File Path** box, enter the full path of the file, e.g. `C:\Skyline DataMiner\Documents\Skyline Logical Layer\TheMonitors.csv`.

1. Click the **Import Parameters** button.

   This should add all the defined monitors.

> [!NOTE]
> When importing parameter monitors checks will be performed to verify for each parameter monitor if the element, parameter and (if applicable) index exist. If any of the to be imported parameter monitors is invalid a pop-up message will be shown indicating the reason why it is invalid and none of the to be imported parameter monitors will be imported or added. On top of that checks are done to prevent that existing monitors could get corrupted (i.e. changed or duplicated). In any case, when importing monitors it is good practice to always check the element logging and verify if no errors are reported. Also check in the Parameter Value Monitors table if all expected monitors have been added, and if they have obtained a valid value. This is the only way to be sure an import has been fully successful.

### Importing Condition Monitors

Proceed in the same way as for the import of parameter monitors, editing at least the Name value (second column) and Condition value (fourth column).

Unlike with the import of parameter monitors, no validation whatsoever is performed, but the overwriting or deleting of existing conditions will be prevented.
