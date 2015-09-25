ms.TocTitle: Outlook Calendar REST API reference
Title: Outlook Calendar REST API reference
Description: Reference how to interact with the Calendar REST API and client library APIs that provide access to events, calendars, and calendar groups in Exchange Online.
ms.ContentId: 443f1cdf-1adb-46a2-b299-228c6f429954
ms.topic: reference (API)
ms.date: July 13, 2015

# Outlook Calendar REST API reference

<a name="GetCalendar"> </a>
###Get a calendar (REST)

_Required scope:  **Calendar.Read**_

Get a calendar by ID. You can get the user's primary calendar by using the `../me/calendar` endpoint.

```no-highlight
GET https://outlook.office365.com/api/{version}/me/calendars/{calendar_id}
```

|**Required parameter**|**Type**|**Description**|
|:-----|:-----|:-----|
|_URL parameters_|
|version|string|The [version](#SupportedVersions) of the API.|
|calendar_id|string|The calendar ID.|


```REST-i
[!RESTAPI [calendar_api_get_calendar_by_id](trydata/calendar_api_get_calendar_by_id.json)]
```

**Response type**

****

<a name="GetCalendarsClient"> </a>
###Get a calendar collection or a calendar (Client)

Get the user's calendars. To get the user's default calendar, use the `client.Me.Calendar` shortcut property. To get a different calendar, specify the calendar ID
 as the index of the  **Calendars** collection or use the **GetById** method.

Example: `client.Me.Calendars[calendarId].ExecuteAsync()`

**Note** Calendar collections support query expressions such as **Select**, **OrderBy**, and **Take**.