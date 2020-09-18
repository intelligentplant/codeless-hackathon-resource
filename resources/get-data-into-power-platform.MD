# Get data into Power Platform

Industrial App Store (IAS) Power Platform connector provides a few functions to make it easier getting process and A&E data into Power Platofrm straight from the source. Although the functions are staight forward you can find more info on them [here](https://github.com/intelligentplant/IAS-Power-BI-connector#supported-actions-functions "IAS Power Platform functions").

- [Get data into Power Platform](#get-data-into-power-platform)
  - [Power BI](#power-bi)
  - [Power Automate](#power-automate)
    - [Recap](#recap)
  - [Power Apps](#power-apps)
    - [Recap](#recap-1)
  - [Aditional resources](#aditional-resources)

## Power BI

Follow the simple steps below to get process data into Power BI Desktop. Below steps assume you are familiar with starting the *Industrial App Store* connector, if no - please check this simple [Getting started](https://github.com/intelligentplant/IAS-Power-BI-connector#getting-started "IAS connector - getting started") guide.

1. Start Power BI Desktop
2. Select Industrial App Store data connector and sign in.
 
> More information on getting started with the connector can be found [here](https://github.com/intelligentplant/IAS-Power-BI-connector#getting-started "IAS connector - getting started").

3. Select and expand the data source you with to interogate.
4. Sleect Get Data function.

> A brief description of available data functions that enable Microsoft’s powerful analytics and visualizations to be applied to real-time and historical process data can be found [here](https://github.com/intelligentplant/IAS-Power-BI-connector#supported-actions-functions "IAS Power Platform functions").

![Industrial App Store Connector - Functions - Get Data](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-functions-getData.gif)

5. Load data into report.

> Once data is retreived from the source, tick the checkbox next to the function and select *Load*.

Repeat the above steps if you wish to load more data sets into the report.

![Industrial App Store Connector - Functions - Get Data](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-load-data-in.jpg)

## Power Automate

In this walkthrough I will connect and retreive value from Oil & Gas Authority data set.

1. **Start Power Automate**<br/>Navigate to [Microsoft Power Autoamte](https://flow.microsoft.com/). Log in if required.
2. **Create new Flow**<br />Hit *:heavy_plus_sign: Create* on the left hand side menu and choose an *Instant Flow* or a *Scheduled Flow* and confirm your selection.

![Industrial App Store Connector - Autoamte - Getting started](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-automate-getting-started.gif)

3. **Create data source name variable**<br /> Create data source name variable by adding a new step called *Initialize variable*. Hit *+ New step* and search for *Initialize variable*. Once found, select that action to add it to the flow. Fill the paraetmers with the following values:

| Name  | Value  | Note                                                                  |
|-------|--------|-----------------------------------------------------------------------|
| Name  | dsn    | Our variable name for later reference will be called *dsn*. |
| Type  | String |                                                                       |
| Value | FCBB05262EADC0B147746EE6DFB2B3EA5C272C33C2C5E3FE8F473D85529461CA.OGA North Sea Production       | Fully qualified address of the data historian.                        |

>NOTE: you can double click the step name to give a more descriptive name or click the 3 dots and choose *Add a comment* to leave a brief description for this step.

4. **Create tag name variable**<br /> Repeat the above steps with the following parameters:

| Name  | Value  | Note                                                                  |
|-------|--------|-----------------------------------------------------------------------|
| Name  | tag    | Our variable name for later reference will be called *tag*. Feel free to give more descriptive name, like *dryoilvol_tag*. |
| Type  | String |                                                                       |
| Value | North Brae.1.dry_oil_vol       | Fully qualified address of the data historian.                        |

>NOTE: you can double click the step name to give a more descriptive name or click the 3 dots and choose *Add a comment* to leave a brief description for this step.

5. **Create tag name variable**<br /> Repeat instructions from step 3 with the following parameters:

| Name  | Value  | Note                                                                  |
|-------|--------|-----------------------------------------------------------------------|
| Name  | limit  | Our variable name for later reference will be called *limit*. Feel free to give more descriptive name, like *oil_limit*. |
| Type  | Integer |                                                                       |
| Value | 20       | Limit value.                        |

>NOTE: you can double click the step name to give a more descriptive name or click the 3 dots and choose *Add a comment* to leave a brief description for this step.

Once completed it should look something like below:

![Industrial App Store Connector - Autoamte - Getting started](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-automate-set-variables-3.jpg)

6. **Add Industrial App Store data retrieval step**<br />Hit *+New Step* and look for *Industrial App Store*. Once found, select the connector and choose *Get Processed* action.

![Industrial App Store Connector - Autoamte - Getting started](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-automate-getprocessed.gif)

>NOTE: you can double click the step name to give a more descriptive name or click the 3 dots and choose *Add a comment* to leave a brief description for this step.

7. **Sign in**<br />Sign in using your Microsoft credentials provided to you earlier today.

> NOTE: you'll only need to do this once per flow. The same connection credentials can be re-used in other flows

![Industrial App Store Connector - Autoamte - Log in](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-automate-login.gif)

8. **Fill in parameters**<br />Fill in the required parameters with the following values:

| Name             | Value          | Note                                                        |
|------------------|----------------|-------------------------------------------------------------|
| Data source name | dsn - variable | From Dynamic content dropdown choose dsn variable property. |
| Tag to query     | tag - variable | From Dynamic content dropdown choose tag variable property. |
| Start time       | 2001-01-01     | The absolute or relative query start time.                  |
| End time         | 2001-03-01     | The absolute or relative query end time.                    |
| Data function    | AVG            |                                                             |
| Sample interval  | 1d             |                                                             |

![Industrial App Store Connector - Autoamte - Log in](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-automate-getprocessed-params.gif)

The historical data returned to Power Automate describes the instrument values using the [JSON file format](https://en.wikipedia.org/wiki/JSON). An example data set is shown below: 

```json
{
    "Edge Historian (ORE Catapult - LDT-INTELPLANT)": {
        "Iconics DA OPC.P135S1_Site_T01.Turbine.AmbTemp_DegC": {
            "TagName": "Iconics DA OPC.P135S1_Site_T01.Turbine.AmbTemp_DegC",
            "DisplayType": "TrailingEdge",
            "Values": [
                {
                    "IsNumeric": true,
                    "TagName": "Iconics DA OPC.P135S1_Site_T01.Turbine.AmbTemp_DegC",
                    "UtcSampleTime": "2020-09-08T04:20:40Z",
                    "NumericValue": 13.89999,
                    "TextValue": "13.89999",
                    "Status": "Good",
                    "Unit": "degC",
                    "Notes": null,
                    "Error": null,
                    "HasError": false
                },
                {
                    "IsNumeric": true,
                    "TagName": "Iconics DA OPC.P135S1_Site_T01.Turbine.AmbTemp_DegC",
                    "UtcSampleTime": "2020-09-09T04:20:40Z",
                    "NumericValue": 13.89999,
                    "TextValue": "13.89999",
                    "Status": "Good",
                    "Unit": "degC",
                    "Notes": null,
                    "Error": null,
                    "HasError": false
                },
				// -- remaining values removed for brevity --
            ]
        }
    }
}
```

The data is indexed by data source name (`Edge Historian (ORE Catapult - LDT-INTELPLANT)`) and then tag name (`Iconics DA OPC.P135S1_Site_T01.Turbine.AmbTemp_DegC`). The entry for each tag contains the following fields:

- `TagName` - the display name of the tag.
- `DisplayType` - provides a hint describing how lines between individual values should be drawn when visualizing the data on a chart.
- `Values` - a list of tag values.

Each entry in the `Values` collection describes a single value for the tag at a specific point in time. Although there are several fields defined on each value, the fields that we are most interested in are:

- `UtcSampleTime` - the UTC timestamp for the sample, specified in ISO 8601 format.
- `NumericValue` - the numerical value recorded by the instrument.
- `Status` - the quality status associated with the value (`Good`, `Bad`, or `Uncertain`). The status will generally be `Good` unless the physical instrument has been diagnosed with a fault.
- `Unit` - the unit of measure for the value.

For the purpose of this exercise, the remaining fields can be ignored.

> NOTE: if you are using *Snapshot* data functions please refer to [this](https://github.com/intelligentplant/codeless-hackathon-resource/blob/master/resources/ias-pp-automate-data-types.MD "IAS - Data response") data structure.

9. **Loop through data**<br /> Create a new step called *Apply to each*. We will use this to loop through each *Numerical value* in the historical data set and check against a limit variable we created in step *5*.

To loop through the response returned by your data query enter the following *expression* as your loop input. Click *Add dynamic content* and select *Expression*.

```text
body('Get_data')?[variables('dsn')]?[variables('oilvol_tag')]?['Values']
```

Hit *Update* to confirm your entry

![Industrial App Store Connector - Autoamte - Log in](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-automate-loop-values.jpg)

10. **Add a condition**. Now isnide your loop click *Add an action* and search for *Condition* step. Once found click on it to add to your flow.

* Add another expression that represents current numerical value in the loop to be compared to the limit value. 

Current numerical value expression

```text
items('Apply_to_each')?['NumericValue']
```

* Choose *is greater than or equal to* operation
* Reference limit variable name from the *Dynamic content dropdown*

### Recap

- Declare variables so they can be re-used further down in the flow
- Establish a connection to Industrial App Store
- Query historical data
- Extract historical data

:loudspeaker: Data is not persited or stored after the flow is ran. It stays safe and secure on clients network.

Thats it :boom: It's now up to you what you wish to do with it, whether its sending a notification email based on the conditions (un)met or simply fill in a weekly Excel report so it can be reviewed by the management :handshake:.

## Power Apps

You can use Microsoft Autoamte to create logic that performs one or more tasks when an event occurs in a PowerApp. For example, configure a button that retrieves current wind turbine sensor data, sends an email or meeting request, or creates an online report. You can also use a flow to return data to PowerApps. For example, configure a flow that retrieves current wind turbine rotor temperature from on site historian, and then processes that data by using Flow's built-in actions. You can configure any control in the app to start the flow, which continues to run even if you close PowerApps.

1. Create your application.
2. Add a button.
3. Assign a Power Autoamte action to the button on click event.
   - Highlight the button.
   - Click Action at the top menu bar.
   - Select *Power Automate*.
   - Hit *Create new flow* option.

![Industrial App Store Connector - Apps - Getting started](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-apps-getting-started.jpg)

3. Follow the instructions on how to create flow to get snapshot values in [Power Automate](#Power Automate) section.
   > Make sureto use *Get Snapshot* function instead of *Get Processed*.
4. Create an object similar to below to return values back to your Power Autoamte App.

![Industrial App Store Connector - Apps - Getting started](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-apps-flow-response.jpg)

5. Reference returned variables to assign to , for example, text values to display current tag values. The screenshot below shows a formula that calls above created flow and sets a local variable with the result returned by the flow.

![Industrial App Store Connector - Apps - Getting started](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-apps-flow-data-formula.jpg)

6. The text element can reference the variable like so:

![Industrial App Store Connector - Apps - Getting started](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-apps-flow-data-formula-text.jpg)

The resulting app could look similar to this:

A simple applciation for an engineer to retreive current sensor readings from wind turbine SCADA and depending on the values could schedule a maintenence to chekc out high readings.

![Industrial App Store Connector - Apps - Getting started](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-apps-app.gif)

### Recap

- Create an app
- Assign an Action to a button
- Create a flow with power Autoamte to retrieve data from on-site data historian and return to your app
- Update UI controls

:loudspeaker: Data is not persited or stored after the flow is ran. It stays safe and secure on clients network.

That's it :boom: It's now up to you what you wish to do with it, whether its sending a notification email based on the conditions (un)met or simply fill in a weekly report so it can be reviewed by the management :handshake:.

## Aditional resources

* [**Using Alarm & Event Meta Tags :alarm_clock:**](https://github.com/intelligentplant/IAS-Power-BI-connector#using-alarm--evnet-meta-tags-alarm_clock "Using Alarm & Event Meta Tags - Catapult Offshore Renewable Energy")<br />Industrial App Store enables users to interact with A&E data using special predefined meta tags. You can easily create Bad Actor report or even extarct Sequence of Events data for further analysis or simple display purposes. See [here](https://github.com/intelligentplant/IAS-Power-BI-connector#using-alarm--evnet-meta-tags-alarm_clock "Using Alarm & Event Meta Tags - Catapult Offshore Renewable Energy") how to formulate a request the A&E data.
* [**Data response types**](https://github.com/intelligentplant/codeless-hackathon-resource/blob/master/resources/ias-pp-automate-data-types.MD "IAS - Data response")<br />See what type of data is returned when a historical or a snapshot data query is perofrmed in Power Automate or Power Apps.