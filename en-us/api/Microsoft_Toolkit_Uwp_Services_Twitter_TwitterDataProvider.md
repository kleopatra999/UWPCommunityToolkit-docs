---
permalink: /en-US/api/Microsoft_Toolkit_Uwp_Services_Twitter_TwitterDataProvider.htm
title: Microsoft.Toolkit.Uwp.Services.Twitter.TwitterDataProvider API 
description: API page for Microsoft.Toolkit.Uwp.Services.Twitter.TwitterDataProvider
keywords: windows, app, toolkit, UWP, API
layout: default
search.product: eADQiWindows 10XVcnh
---


# TwitterDataProvider class

Data Provider for connecting to Twitter service.

## Members

The **TwitterDataProvider** class has this types of members

* [constructors](#constructors)

* [methods](#methods)

* [properties](#properties)

* [fields](#fields)

### constructors

#### contructor

Initializes a new instance of the [TwitterDataProvider](Microsoft_Toolkit_Uwp_Services_Twitter_TwitterDataProvider.htm) class. Constructor.

##### parameters



| name | description | type |


### methods

#### UploadPicture(Windows.Storage.Streams.IRandomAccessStream stream)

Publish a picture to Twitter user's medias.

##### parameters



| name | description | type |


#### GetTimeStamp()

Generate timestamp.

##### parameters



| name | description | type |


#### GetNonce()

Generate nonce.

##### parameters



| name | description | type |


#### ExchangeRequestTokenForAccessToken(System.String webAuthResultResponseData)

Extract and initialize access tokens.

##### parameters



| name | description | type |


#### GetSignature(System.String sigBaseString,System.String consumerSecretKey)

Generate request signature.

##### parameters



| name | description | type |


#### GetUserAsync(System.String screenName)

Retrieve user data.

##### parameters



| name | description | type |


#### GetUserTimeLineAsync``1(System.String screenName,System.Int32 maxRecords,Microsoft.Toolkit.Uwp.Services.IParser(TT0) parser)

Retrieve user timeline data with specific parser.

##### parameters



| name | description | type |


#### SearchAsync``1(System.String hashTag,System.Int32 maxRecords,Microsoft.Toolkit.Uwp.Services.IParser(TT0) parser)

Search for specific hash tag with specific parser.

##### parameters



| name | description | type |


#### LoginAsync()

Log user in to Twitter.

##### parameters



| name | description | type |


#### Logout()

Log user out of Twitter.



#### TweetStatus(System.String tweet,Windows.Storage.Streams.IRandomAccessStream[] pictures)

Tweets a status update.

##### parameters



| name | description | type |


#### GetSignatureBaseStringParams(System.String consumerKey,System.String nonce,System.String timeStamp,System.String additionalParameters)

Build signature base string.

##### parameters



| name | description | type |


#### GetDefaultParser(Microsoft.Toolkit.Uwp.Services.Twitter.TwitterDataConfig config)

Returns parser implementation for specified configuration.

##### parameters



| name | description | type |


#### GetDataAsync``1(Microsoft.Toolkit.Uwp.Services.Twitter.TwitterDataConfig config,System.Int32 maxRecords,Microsoft.Toolkit.Uwp.Services.IParser(TT0) parser)

Wrapper around REST API for making data request.

##### parameters



| name | description | type |


#### ValidateConfig(Microsoft.Toolkit.Uwp.Services.Twitter.TwitterDataConfig config)

Check validity of configuration.

##### parameters



| name | description | type |


#### ExtractTokenFromResponse(System.String getResponse,Microsoft.Toolkit.Uwp.Services.Twitter.TwitterOAuthTokenType tokenType)

Extract requested token from the REST API response string.

##### parameters



| name | description | type |


#### GetHomeTimeLineAsync``1(System.Int32 maxRecords,Microsoft.Toolkit.Uwp.Services.IParser(TT0) parser)

Get home time line data.

##### parameters



| name | description | type |


#### InitializeRequestAccessTokens(System.String twitterCallbackUrl)

Package up token request.

##### parameters



| name | description | type |


### properties

#### LoggedIn

Gets a value indicating whether the provider is already logged in



#### UserScreenName

Gets or sets logged in user information.



### fields

#### tokens

Base Url for service.



#### vault

Password vault used to store access tokens



#### BaseUrl

Base Url for service.

