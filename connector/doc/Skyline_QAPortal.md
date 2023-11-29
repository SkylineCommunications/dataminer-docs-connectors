---
uid: Connector_help_Skyline_QAPortal
---

# Skyline QAPortal

The **Skyline QAPortal** connector allows you to manage **regression tests** and group them together and see the results in DataMiner. This will allow you to alarm and trend the results of your regression tests.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Manage regression tests</li><li>Run tests with different inputs</li></ul>         |<span style="color:grey">N/A</span>         |<span style="color:grey">N/A</span>         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |<ul><li>[SLC-AS-SkylineQAPortalExampleTest](https://github.com/SkylineCommunications/SLC-AS-SkylineQAPortalExampleTest)</li></ul>         |<span style="color:grey">N/A</span>   |

## Configuration

### Initialization

There is an option to push the results to the **Skyline QA Portal**. This will provide visibility to your tests for **Skyline Communications**. In order to enable this you will need to have an mail server configured on your DMS, so the results can be mailed to the portal and you will need to configure the **API Key** and the **Client ID** on the **Settings** page. Then you can enable the option **Forward Results to Portal**. The API Key and Client ID will need to be provided by Skyline and needs to be kept **secret** to your organization.

## How to use

The connector will automatically detect any regression tests available in your DMS. Regression tests are added in the form of an automation script. There is an example script [SLC-AS-SkylineQAPortalExampleTest](https://github.com/SkylineCommunications/SLC-AS-SkylineQAPortalExampleTest) available to get you started with regression tests. If the refression tests requires input parameters, then you can add them under the **Input Parameters** page. The connector is designed so you can add the same test multiple times with different inputs. This way you can make your regression test generic and reusable.

### Adding a regression test

To add a regression test, go to the **General** page and use the **Context Menu** (right-click) on the **Regression Tests** table. If you just added a new regression test, it is possible that you need to use the **Refresh Tests** button to get them in the dropdown.

### Adding input parameters

If your regression test has input parameters, then you can use the **Input** column on the **Regression Tests** table to configure them. If you did not yet define any **Input Group** yet (empty dropdown), then you can create a new one by setting the **New...** option under the '...'. This will create a new group **Input Group** in the **Input Parameters** table. You will need to configure the **Value** in that table. There is also a **Context Menu** on that table that allows you to create or remove any **Input Groups**.

### Grouping your tests

There is a **Group** column on the **Regression Tests** table which will allow you to group a set of tests together that you want to execute at once. If there is an order in which the tests need to be executed, you can use the **Exec Order** column to define the order. The test with the lowest order will be executed first. If any tests in the same group have the same **Exec Order** then they will be executed at the same time.

### Running your tests

You can run the regression tests by using the **Run** button on the **Regression Tests** table or on the **Groups** table. Once the test(s) are finished you will find the results under the **Results Cases** and the **Results Performance** pages.

## Known Regression Tests

- [SLC-AS-SkylineQAPortalExampleTest](https://github.com/SkylineCommunications/SLC-AS-SkylineQAPortalExampleTest)