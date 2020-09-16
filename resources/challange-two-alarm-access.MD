# Challenge Two :trophy:

## Catapult Offshore Renewable Energy

> Learning from turbine alarms integrated with SCADA.

* [**Challenge Statement**](https://www.theogtc.com/media/3837/challenge-two-final.pdf "Challenge Statement - Catapult Offshore Renewable Energy")
* [**Help sheet**]()<br />Overview of the Levenmouth Wind Turbine with some getting started hints.
* [**Tag & Alarm List**](http://appstore.intelligentplant.com/nuget/downloads/OgtcHack20/ORE-TagAndAlarmList.xlsx "Tag & Alarm List - Catapult Offshore Renewable Energy")<br />Complete list of tags and alarms on asset.
* [**Using Alarm & Event Meta Tags :alarm_clock:**](https://github.com/intelligentplant/IAS-Power-BI-connector#using-alarm--evnet-meta-tags-alarm_clock "Using Alarm & Event Meta Tags - Catapult Offshore Renewable Energy")<br />Industrial App Store enables users to interact with A&E data using special predefined meta tags. You can easily create Bad Actor report or even extarct Sequence of Events data for further analysis or simple display purposes. See [here](https://github.com/intelligentplant/IAS-Power-BI-connector#using-alarm--evnet-meta-tags-alarm_clock "Using Alarm & Event Meta Tags - Catapult Offshore Renewable Energy") how to formulate a request the A&E data.

## Acquiring data

1. Start Power BI and open the Industrial App Store Connector.<br />
Please refer to [these easy steps](https://github.com/intelligentplant/IAS-Power-BI-connector#get-the-connector "IAS - Getting started") to start Power BI and open the data connector.

2. Select and expand *ORE Catapul Alarm Analysis* data source.
3. Sleect *Get Raw* function.

![Start Industrial App Store Connector](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-challange-two-get-ae-data.gif)

4. Fill the following values for the required paraemters

| Parameter  | Value                             | Description                                                                                               |
|------------|-----------------------------------|-----------------------------------------------------------------------------------------------------------|
| Tag name   | ORE Catapult/Levenmouth/Soe/0-30. | We utilise meta tags to retrieve data from A&E store. More information is available [here](https://github.com/intelligentplant/IAS-Power-BI-connector#using-alarm--evnet-meta-tags-alarm_clock "Industrial App Store - Using Alarm & Event Meta Tags").                 |
| Start Data | *-30d                             | You can enter relative or absolute dates. Use the following format for absolute dates `2020-08-01T00:00Z` |
| End Date   | *                                 | You can enter relative or absolute dates. Use the following format for absolute dates `2020-08-01T00:00Z` |
| Points     | 1                                 | This is not applicable, but needs a value.                                                                |

4. Hit apply, tick the checkbox next to the function and hit *Load* to start working on the data in Power BI.<br />
The query should result into a similar result seen below.

![Start Industrial App Store Connector](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-challange-two-get-ae-ORE-data.jpg)

## SCADA data

Please refer to the [**tag list**](http://appstore.intelligentplant.com/nuget/downloads/OgtcHack20/ORE-TagAndAlarmList.xlsx "Tag & Alarm List - Catapult Offshore Renewable Energy") provided by ORE Catapult and the guide [here](https://github.com/intelligentplant/codeless-hackathon-resource/blob/master/resources/get-data-into-power-platform.MD#power-bi-chart_with_upwards_trend "IAS - Getting data into Power BI") on how to get process data into Power BI.

## Good luck :v: