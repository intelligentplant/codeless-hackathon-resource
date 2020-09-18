# Get data into Power Platform

Industrial App Store (IAS) Power Platform connector provides a few functions to make it easier getting process and A&E data into Power Platofrm straight from the source. Although the functions are staight forward you can find more info on them [here](https://github.com/intelligentplant/IAS-Power-BI-connector#supported-actions-functions "IAS Power Platform functions").

## Power BI :chart_with_upwards_trend:

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

## Power Automate :zap:

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

4. **Create tag name variable**<br /> Repeat the above steps with the following parameters:

| Name  | Value  | Note                                                                  |
|-------|--------|-----------------------------------------------------------------------|
| Name  | tag    | Our variable name for later reference will be called *tag*. Feel free to give more descriptive name, like *dryoilvol_tag*. |
| Type  | String |                                                                       |
| Value | North Brae.1.dry_oil_vol       | Fully qualified address of the data historian.                        |

Once completed it should look something like below:

![Industrial App Store Connector - Autoamte - Getting started](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-automate-set-variables.jpg)

5. **Add Industrial App Store data retrieval step**<br />Hit *+New Step* and look for *Industrial App Store*. Once found, select the connector and choose *Get Processed* action.

![Industrial App Store Connector - Autoamte - Getting started](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-automate-getprocessed.gif)

>NOTE: you can double click the step name to give a more descriptive name or click the 3 dots and choose *Add a comment* to leave a brief description for this step.

5. **Sign in**<br />Sign in using your Microsoft credentials provided to you earlier today.

> NOTE: you'll only need to do this once per flow. The same connection credentials can be re-used in other flows

![Industrial App Store Connector - Autoamte - Log in](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-automate-login.gif)