# Data responses

## Get Snapshot :watch:

The snapshot data returned to Power Automate describes the instrument values using the [JSON file format](https://en.wikipedia.org/wiki/JSON). An example data set is shown below:

```json
{
    "FBF94704A9C213490B00CFD213C6CDB41653A7E8461EE9AA43871BDD6B4795D2.Edge Historian": {
        "Iconics DA OPC.P135S1_Site_T01.Turbine.AmbTemp_DegC": {
            "TagName": "Iconics DA OPC.P135S1_Site_T01.Turbine.AmbTemp_DegC",
            "UtcSampleTime": "2020-09-18T07:34:42.433Z",
            "NumericValue": 15.09999,
            "IsNumeric": true,
            "TextValue": "15.09999",
            "Status": "Good",
            "Unit": "degC",
            "Notes": null,
            "Error": null,
            "HasError": false,
            "Properties": {}
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


## Get Historical :calendar:

`The historical data returned to Power Automate describes the instrument values using the [JSON file format](https://en.wikipedia.org/wiki/JSON). An example data set is shown below: 

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
`