---
permalink: /en-US/api/Microsoft_Toolkit_Uwp_Notifications_TileContent.htm
title: Microsoft.Toolkit.Uwp.Notifications.TileContent API 
description: API page for Microsoft.Toolkit.Uwp.Notifications.TileContent
keywords: windows, app, toolkit, UWP, API
layout: api
search.product: eADQiWindows 10XVcnh
---


# TileContent class

Base Tile element, which contains a single visual element.

## Members

The **TileContent** class has the following types of members:

### Methods

#### GetContent()

Retrieves the notification XML content as a string, so that it can be sent with a HTTP POST in a push notification.

##### Parameters



| Name | Description | Type || --- | --- | --- || return |The notification XML content as a string. |


#### GetXml()

Retrieves the notification XML content as a WinRT XmlDocument, so that it can be used with a local Tile notification's constructor on either [TileNotification](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Notifications.TileNotification) or [ScheduledTileNotification](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Notifications.ScheduledTileNotification).

##### Parameters



| Name | Description | Type || --- | --- | --- || return |The notification XML content as a WinRT XmlDocument. |


### Properties

#### Visual

The visual element is required.


