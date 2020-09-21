# Getting Started on the Alba Dataset

For this exercise, you will be connecting to an OSI Soft PI Historian (a large database for storing time-series process data) recording live data from the Alba platform.

* Data is accessible via a “tag” – *a unique identifier for a measurement*.

For a short-list of useful tags, refer to the [Challenge 4 Help Sheet](https://github.com/intelligentplant/codeless-hackathon-resource/blob/master/resources/Challenge4HelpSheet.pdf).

# How to get data into Power BI

We can interrogate the historian as follows...

1. **Start Power BI and open the Industrial App Store Connector**<br />
The connector is certified and distributed by Microsoft with Power BI updates :fire:. Just click Get data and look for Industrial App Store data connector.

![Start Industrial App Store Connector](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-start-connector.gif)

2. **Log in**<br />
Sign in using Microsoft and enter you Hackathon account credentials. 

![Log in Industrial App Store Connector](https://intelligentplant.com/datasheets/powerplatform/resources/ias-pp-start-connector-log-in.gif)


3. **Enter Query Parameters**<br />
From the Navigator, select *Alba PI Historian* and enter the parameters for your query.

For example, if we wanted to obtain hourly readings of Full Load Current (FLC%) for Gas Compressors A and B over the past 7 days, we’d enter the following parameters into the Industrial App Store Data Connector for Power BI.

![](images/Challenge4DataGuide01.png)

| Parameter | Value | Notes |
|-----------|-------|-------|
|Tag Names |  ALB-FLC_K0801A.PV, ALB-FLC_K0801B.PV | Comma separated list of tags |
| Start Date | *-7d| A relative date notation meaning "now minus 7 days". Alternatively, an explicit date could be used (e.g. "2010-09-15"). |
|End Date | *| A relative data notation meaning "now". Alternatively, an explicit date could be used (e.g. "2010-09-21").|
| Function | Interp | Interpolated date, this means an approximated value is derived for the specified interval. |
| Interval | 1h | 1 hour |

4. **Load data**<br />Hit apply, tick the checkbox next to the function and hit *Load* to start working on the data in Power BI.<br />

> NOTE: This connects to the source historian on site to retrieve data :fire:. If you used *relative* timestamps in your data query this means your result data set will always be up to date.

# How to get data in Power Automate :zap:

:bulb: You can utilise the pre-defined challange templates found on [Microsoft Power Automate Portal](https://flow.microsoft.com/).

...or you can follow a step by step guide [here](https://github.com/intelligentplant/codeless-hackathon-resource/blob/master/resources/get-data-into-power-platform.MD#power-automate-zap "Industrial App Store - Get data into Power Automate"). Make sure you know which tag names you want to interogate and please use the following value for qualified data source name (this is a qualified data source name for on-site historian).

```text
7404BBBA5A773C7AC89411978E9B7F415B939B0DBC6B3C5B17AD59251D587B6A.Alba PI Historian
```


# More Info...

* [**Get data into Power Platform**](https://github.com/intelligentplant/codeless-hackathon-resource/blob/master/resources/get-data-into-power-platform.MD)<br/> General instructions on how to use Industrial App Store connectors for Power BI, Power Apps, Power Automate Flow and Power Virtual Agent.

* [**Industrial App Store Power BI Connector**](https://github.com/intelligentplant/IAS-Power-BI-connector)<br/> Detailed documentation on IAS Power BI Connecter.

# Good luck :v:

Intelligent Plant and Microsoft teams are always here to provide a helping hand if you encountner any technical issues.
