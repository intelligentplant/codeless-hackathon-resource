# Challenge Two - Data Guide:trophy:

## Catapult Offshore Renewable Energy

> Learning from turbine alarms integrated with SCADA.

## How to acquiring A&E data

1. **Start Power BI and open the Industrial App Store Connector**<br />
The connector is certified and distributed by Microsoft with Power BI updates :fire:. Just click Get data and look for Industrial App Store data connector.

![Start Industrial App Store Connector](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-start-connector.gif)

2. **Log in**<br />
Sign in using your Microsoft credentials provided to you at the start of the event.

> During the log in process you can authorise Power BI to access your data sources or feel free to browse demo data source available by default for you to play around with.

![Log in Industrial App Store Connector](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-start-connector-log-in.gif)

3. **Choose data source**<br />Select and expand *ORE Catapul Alarm Analysis* data source.
4. **Choose data function**<br />To retrieve A&E data sleect *Get Raw* data function.

![Start Industrial App Store Connector](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-challange-two-get-ae-data.gif)

5. **Fill in parameters**<br />Fill the following values for the required paraemters.

| Parameter  | Value                             | Description                                                                                               |
|------------|-----------------------------------|-----------------------------------------------------------------------------------------------------------|
| Tag name   | ORE Catapult/Levenmouth/Soe/0-30. | We utilise meta tags to retrieve data from A&E store. More information is available [here](https://github.com/intelligentplant/IAS-Power-BI-connector#using-alarm--evnet-meta-tags-alarm_clock "Industrial App Store - Using Alarm & Event Meta Tags").                 |
| Start Data | *-30d                             | You can enter relative or absolute dates. Use the following format for absolute dates `2020-08-01T00:00Z` |
| End Date   | *                                 | You can enter relative or absolute dates. Use the following format for absolute dates `2020-08-01T00:00Z` |
| Points     | 1                                 | This is not applicable, but needs a value.                                                                |

6. **Load data**<br />Hit apply, tick the checkbox next to the function and hit *Load* to start working on the data in Power BI.<br />
The query should result into a similar result seen below.

> NOTE: This connects to the source historian on site to retrieve data :fire:. If you used *relative* timestamps in your data query this means your result data set will always be up to date.

![Start Industrial App Store Connector](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-challange-two-get-ae-ORE-data.jpg)

## How to acquiring SCADA data

Please refer to the [**tag list**](http://appstore.intelligentplant.com/nuget/downloads/OgtcHack20/ORE-TagAndAlarmList.xlsx "Tag & Alarm List - Catapult Offshore Renewable Energy") provided by ORE Catapult and the guide [here](https://github.com/intelligentplant/codeless-hackathon-resource/blob/master/resources/get-data-into-power-platform.MD#power-bi-chart_with_upwards_trend "IAS - Getting data into Power BI") on how to get process data into Power BI.

1. **Start Power BI and open the Industrial App Store Connector**<br />
The connector is certified and distributed by Microsoft with Power BI updates :fire:. Just click Get data and look for Industrial App Store data connector.

![Start Industrial App Store Connector](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-start-connector.gif)

2. **Log in**<br />
Sign in using your Microsoft credentials provided to you at the start of the event.

> During the log in process you can authorise Power BI to access your data sources or feel free to browse demo data source available by default for you to play around with.

![Log in Industrial App Store Connector](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-start-connector-log-in.gif)

3. **Choose data source**<br />Select and expand *Edge Historian (ORE Catapul)* data source.
4. **Choose data function**<br />To retrieve process data sleect *Get Processed* data function.

> A brief description of available data functions that enable Microsoft’s powerful analytics and visualizations to be applied to real-time and historical process data can be found [here](https://github.com/intelligentplant/IAS-Power-BI-connector#supported-actions-functions "IAS Power Platform functions").

![Start Industrial App Store Connector](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-challange-two-get-process-data.gif)

5. **Fill in parameters**<br />Fill the following values for the required paraemters.

| Parameter  | Value                             | Description                                                                                               |
|------------|-----------------------------------|-----------------------------------------------------------------------------------------------------------|
| Tag name   | Iconics DA OPC.P135S1_Site_T01.Turbine.AmbTemp_DegC,Iconics DA OPC.P135S1_Site_T01.Turbine.MainBearingtemp1,Iconics DA OPC.P135S1_Site_T01.Turbine.GenBearingtemp1 | You can query data for a single tag or multiple tags when using a comma separated list. Please refer to the tag list provided by ORE catapult [here](http://appstore.intelligentplant.com/nuget/downloads/OgtcHack20/ORE-TagAndAlarmList.xlsx "Tag & Alarm List - Catapult Offshore Renewable Energy").                 |
| Start Data | *-30d                             | You can enter relative or absolute dates. Use the following format for absolute dates `2020-08-01T00:00Z` |
| End Date   | *                                 | You can enter relative or absolute dates. Use the following format for absolute dates `2020-08-01T00:00Z` |
| Function   | AVG                               | Use any provided data function from the dropdown but AVG is a good starting point.                                                                |
| Interval     | 1d                                 | This can be 1d, 90s, 5d, etc.                                                                |

6. **Load data**<br />Hit apply, tick the checkbox next to the function and hit *Load* to start working on the data in Power BI.<br />
The query should result into a similar result seen below.

> NOTE: This connects to the source historian on site to retrieve data :fire:. If you used *relative* timestamps in your data query this means your result data set will always be up to date.

![Start Industrial App Store Connector](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-challange-two-get-process-ORE-data.jpg)

## How to get data in Power Automate :zap:

- You utilise pre-defined challange templates found on [Microsoft Power Autoamte Portal](https://flow.microsoft.com/).

![Start Industrial App Store Connector](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-automate-flow-templates.jpg)

- Or you can create your own flow by following [this](https://github.com/intelligentplant/codeless-hackathon-resource/blob/master/resources/get-data-into-power-platform.MD#power-automate-zap "Industrial App Store - Get data into Power Automate") step by step guide :hourglass_flowing_sand:. For this you'll need to know which tags you want to interogate and the following value for qualified data source name (this is a qualified data source name for on-site historian).

For **process** data use

```text
FBF94704A9C213490B00CFD213C6CDB41653A7E8461EE9AA43871BDD6B4795D2.Edge Historian
```

For **A&E** process data use

```text
FBF94704A9C213490B00CFD213C6CDB41653A7E8461EE9AA43871BDD6B4795D2.ORE Catapult Alarm Analysis
```

## Aditional resources

* [**Challenge Statement**](https://www.theogtc.com/media/3837/challenge-two-final.pdf "Challenge Statement - Catapult Offshore Renewable Energy")
* [**Help sheet**]()<br />Overview of the Levenmouth Wind Turbine with some getting started hints.
* [**Tag & Alarm List**](http://appstore.intelligentplant.com/nuget/downloads/OgtcHack20/ORE-TagAndAlarmList.xlsx "Tag & Alarm List - Catapult Offshore Renewable Energy")<br />Complete list of tags and alarms on asset.
* [**Using Alarm & Event Meta Tags :alarm_clock:**](https://github.com/intelligentplant/IAS-Power-BI-connector#using-alarm--evnet-meta-tags-alarm_clock "Using Alarm & Event Meta Tags - Catapult Offshore Renewable Energy")<br />Industrial App Store enables users to interact with A&E data using special predefined meta tags. You can easily create Bad Actor report or even extarct Sequence of Events data for further analysis or simple display purposes. See [here](https://github.com/intelligentplant/IAS-Power-BI-connector#using-alarm--evnet-meta-tags-alarm_clock "Using Alarm & Event Meta Tags - Catapult Offshore Renewable Energy") how to formulate a request the A&E data.

## Good luck :v:

Intelligent Plant and Microsoft teams are always here to provide a helping hand if you encoutner any technical issues.