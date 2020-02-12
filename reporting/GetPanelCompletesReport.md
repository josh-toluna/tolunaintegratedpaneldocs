---
title: GetPanelCompletesReport
has_children: false
parent: Reporting
nav_order: 7
---

## GetPanelCompletesReport

Returns all completes generated by a panel in the given date range.
>Please note: the date range is restricted to 30 days.

### Route
```
GET http://{IP_CORE_URL}/IntegratedPanelService/api/Reports/Surveys/PanelCompletes?SamplePartnerGuid={PartnerGUID}&StartDate={StartDate}&EndDate+{EndDate}
```

### Request Parameters

| Name | Type | Description | Required? |
| :--- | :--- | :--- | :---: |
| SamplePartnerGUID | ```GUID``` | API key provided by Toluna | Yes |
| StartDate | ```dateTime``` | UTC date/time at which report should begin. Format: YYYY-MM-DD HH:MM:SS |
| EndDate | ```dateTime``` | UTC date/time at which report should end. Format: YYYY-MM-DD HH:MM:SS |

### Response Details

| Name | Type | Description |
| :--- | :--- | :--- |
| PartnerGUID | ```GUID``` | Partner API key |
| CreatedUTC | ```dateTime``` | UTC date/time report created |
| StartSearchUTC | ```dateTime``` | UTC date/time start report |
| EndSearchUTC | ```dateTime``` | UTC date/time end report |
| CompletesSummary[] | ```array``` | List of completes |
| CompletesSummary[n].SurveyID | ```int``` | Toluna Survey identifier |
| CompletesSummary[n].SurveyName | ```string``` | Toluna Survey name |
| CompletesSummary[n].WaveID | ```int``` | Current iteration of the Survey. Studies related to one another can be sent "Waves" that the Member experiences as unique Surveys |
| CompletesSummary[n].MemberCode | ```string``` | Unique Respondent Code from the Partner |
| CompletesSummary[n].EventDate | ```dateTime``` | date/time fo last change |
| CompletesSummary[n].AdditionalData | ```string``` | Query string parameters requested by the Partner |

### Possible Response Codes

| Code | Etiology, actions |
| :--- | :--- |
| 200 | OK. Request processed normally; results returned without issue |
| 400 | {StartDate} must precede {EndDate} |
| 400 | Search date range cannot exceed 30 days |
| 400 | Could not find Partner for {PartnerGUID} |
| 500 | Internal Error. An exception occurred while processing the request. Toluna likely has details captured in its logs |

### Example Response
```
{
  "Name": "PanelCompletesReport",
  "Description": "Shows the list of completes for a panel in the provided date range",
  "PartnerGUID": "b89268bf-5f68-470e-ac50-9ff6998cb93b",
  "CreatedUTC": "2018-01-23T17:28:19.157403Z",
  "StartSearchUTC": "2017-10-01T00:00:00",
  "EndSearchUTC": "2017-10-03T00:00:00",
  "CompletesSummary": [
    {
    "SurveyID": 36326,
    "SurveyName": "1074978-US-3",
    "WaveID": 0,
    "MemberCode": "1701440138",
    "EventDate": "2017-10-02T15:29:46.573",
    "AdditionalData": “clickid=123”
    },
    {
    "SurveyID": 36326,
    "SurveyName": "1074978-US-3",
    "WaveID": 0,
    "MemberCode": "1701440138",
    "EventDate": "2017-10-02T15:29:46.573",
    "AdditionalData": “clickid=124”
    }
  ]
}
```