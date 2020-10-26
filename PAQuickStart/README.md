# PingAccess QuickStart Application Postman Collection

A Postman collection that uses the  [PingFederate](https://support.pingidentity.com/s/document-item?bundleId=pingfederate-93&topicId=gettingStartedGuide%2FgettingStarted.html) and [PingAccess](https://support.pingidentity.com/s/document-item?bundleId=pingaccess-52&topicId=overview%2Fpa_c_PingAccess_Overview.html) Admin REST APIs to setup and configure the PAQuickStart app.  Unlike the PAQuickStart python script or data.zip, this collection will not overwrite your existing PF and PA configuration.  Instead it simply uses the Admin APIs to add the configuration necessary for the PAQuickStart app to your existing PF and PA instances.  In addition, this collection could be used for illustrative purposes, to show how you can automate the setup/configuration of an application in PA via the Admin APIs.

## Installation

To use the latest published version, click the following button to import the PA QuickStart Setup collection into Postman:

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/95754e155653078df704#?env%5BPA-QuickStart%5D=W3sia2V5IjoicGZIb3N0IiwidmFsdWUiOiJsb2NhbGhvc3QiLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6InBhSG9zdCIsInZhbHVlIjoibG9jYWxob3N0IiwiZW5hYmxlZCI6dHJ1ZX0seyJrZXkiOiJwY3ZJZCIsInZhbHVlIjoiU2ltcGxlUEFRdWlja1N0YXJ0IiwiZW5hYmxlZCI6dHJ1ZX0seyJrZXkiOiJpZHBBZGFwdGVySWQiLCJ2YWx1ZSI6IkhUTUxQQVF1aWNrU3RhcnQiLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6ImNsaWVudFNlY3JldCIsInZhbHVlIjoiMkZlZGVyYXRlIiwiZW5hYmxlZCI6dHJ1ZX0seyJrZXkiOiJwZlVuIiwidmFsdWUiOiJBZG1pbmlzdHJhdG9yIiwiZW5hYmxlZCI6dHJ1ZX0seyJrZXkiOiJwZlB3IiwidmFsdWUiOiJQYWNlcnMzISIsImVuYWJsZWQiOnRydWV9LHsia2V5IjoicGFVbiIsInZhbHVlIjoiQWRtaW5pc3RyYXRvciIsImVuYWJsZWQiOnRydWV9LHsia2V5IjoicGFQdyIsInZhbHVlIjoiUGFjZXJzMyEiLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6InYiLCJ2YWx1ZSI6InYzIiwiZW5hYmxlZCI6dHJ1ZX0seyJrZXkiOiJ2aXJ0dWFsSG9zdCIsInZhbHVlIjoibG9jYWxob3N0IiwiZW5hYmxlZCI6dHJ1ZX0seyJrZXkiOiJ2aXJ0dWFsSG9zdElkIiwidmFsdWUiOjEsImVuYWJsZWQiOnRydWV9LHsia2V5Ijoic2NvcGVSdWxlSWQiLCJ2YWx1ZSI6MSwiZW5hYmxlZCI6dHJ1ZX0seyJrZXkiOiJhdHRyUnVsZUlkIiwidmFsdWUiOjIsImVuYWJsZWQiOnRydWV9LHsia2V5Ijoid2ViUnVsZUlkIiwidmFsdWUiOjMsImVuYWJsZWQiOnRydWV9LHsia2V5IjoiYXBpUlNJZCIsInZhbHVlIjoxLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6ImFwaU1hcElkIiwidmFsdWUiOjEsImVuYWJsZWQiOnRydWV9LHsia2V5Ijoid2ViTWFwSWQiLCJ2YWx1ZSI6MiwiZW5hYmxlZCI6dHJ1ZX0seyJrZXkiOiJ3ZWJTZXNzaW9uSWQiLCJ2YWx1ZSI6MSwiZW5hYmxlZCI6dHJ1ZX0seyJrZXkiOiJwZkNlcnRJZCIsInZhbHVlIjoiY2VkbXllYWxiZW94MjYwZTljaHUwNXhjdCIsImVuYWJsZWQiOnRydWV9LHsia2V5IjoicGZDZXJ0RGF0YSIsInZhbHVlIjoiLS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tXG5NSUlEVmpDQ0FqNmdBd0lCQWdJR0FYVkhNTEVaTUEwR0NTcUdTSWIzRFFFQkN3VUFNR3d4Q3pBSkJnTlZCQVlUQWxWVE1Rc3dDUVlEXG5WUVFJRXdKRFR6RVBNQTBHQTFVRUJ4TUdSR1Z1ZG1WeU1SVXdFd1lEVlFRS0V3eFFhVzVuU1dSbGJuUnBkSGt4RkRBU0JnTlZCQXNUXG5DMFJsZG1Wc2IzQnRaVzUwTVJJd0VBWURWUVFERXdsc2IyTmhiR2h2YzNRd0hoY05NakF4TURJd01UZ3dOakUwV2hjTk16QXhNREl4XG5NVGd3TmpFMFdqQnNNUXN3Q1FZRFZRUUdFd0pWVXpFTE1Ba0dBMVVFQ0JNQ1EwOHhEekFOQmdOVkJBY1RCa1JsYm5abGNqRVZNQk1HXG5BMVVFQ2hNTVVHbHVaMGxrWlc1MGFYUjVNUlF3RWdZRFZRUUxFd3RFWlhabGJHOXdiV1Z1ZERFU01CQUdBMVVFQXhNSmJHOWpZV3hvXG5iM04wTUlJQklqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FROEFNSUlCQ2dLQ0FRRUExaUFZcVl3TlBqc3dza0JUQ0N0eUZtMEl1SE9qXG5jQ083NnA4Q3BSdDh6Q2JXN1NxUFpFTk5lZEFYTnNJekZqV2tZK1AwR0c4S2ttK3FUSklXQVMrY25NVHR5bU8rcWdiQStTdmcwOTJoXG5RVkRmZklDV2lISUEwNGkxY3dVQ2ZORTR6STV2QXpjN2ZPN01ydmhtV3VhdXg2MzhnWlVUbGU3OTA3dzY4VjFqWFlVdUxDeFUzQ2lMXG5kVXZiSWh6ZllSYXhBSVk0VlR6SXlVczRnNk4zZ2VJSmFaWUNIVzl3L1lLejBldkV3eHdxNWNPQmxNcU9hOCs0eFdCVXlCUHRJUFhtXG5pNHVqTWhEOGFYWjNnamE1S2VscnNyYUw5TVlNUTdjYWVjb2VGWVg2Ym5Qem5rOWM2R0NtSWlSVlRlNXVjckpLNDl5M1U2elkyQytQXG5kNGtPa1JtN3NRSURBUUFCTUEwR0NTcUdTSWIzRFFFQkN3VUFBNElCQVFBRm11MW0rS25idGliR2x6Sm9GY2t5L2FzWFJUVFVaTGViXG4yK1lxckZUUUN0M3pFRVQvTnlMNEJtZVVxcmZwUnJSS05JaXYrRFMzeDBPakpEU1lraVF1bE5sVU1TWVpObkRWTENZRXNBUmkrbTVQXG40YlBmeWN3dUpZRFJaUmkvNzUvQlF4U0NYY3M3VEEzYVcra1pOTnBWVmJrMGJEWFVYRjFuNlVKTGdRKy9rZllNNXFDVFlteENIdExBXG5LcUxYeWFIMGpqQytjTkxGWkdKL0VadDFFQW5mZUdmTVhUN0pmenl6TVEwRzB1NmJjVmdtUWc3TFB2MVFpTmE0dGJjeXFNQWFZY1hpXG5ES0dOWVBZUG03ZlhHeDlvTEEvQUJib2NoV0JpbFJsdXpLOC9YdVdFMkxGR2FKdUVCWk1IZW9ndmdoLzdUMm1EajlaRVJwWnU4d0QrXG40ZVFIXG4tLS0tLUVORCBDRVJUSUZJQ0FURS0tLS0tXG4iLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6ImNlcnRJZCIsInZhbHVlIjoxLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6ImNlcnRHcm91cElkIiwidmFsdWUiOjMsImVuYWJsZWQiOnRydWV9LHsia2V5Ijoic2l0ZUlkIiwidmFsdWUiOjEsImVuYWJsZWQiOnRydWV9LHsia2V5Ijoid2ViQXBwSWQiLCJ2YWx1ZSI6MiwiZW5hYmxlZCI6dHJ1ZX0seyJrZXkiOiJyb290UmVzb3VyY2VJZCIsInZhbHVlIjoyLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6ImFwaUFwcElkIiwidmFsdWUiOjEsImVuYWJsZWQiOnRydWV9XQ==)

You can also download the collection file from this repo, then import directly into Postman.

### Prerequisites

* *Postman* The collection is for use by the Postman app. Postman is a utility that allows you to quickly test and use REST APIs. More information can be found at [getpostman.com](https://www.getpostman.com/).
* *PingAccess:*
  * Version 5.x
* *PingAccess QuickStart Application:*
  * Version 5.x
  * PingAccessQuickStart.war file placed in the /pingfederate/server/default/deploy directory
* *PingFederate:*
    * Version 9.x
    * The OIDC role under OAuth 2.0 AS server settings needs to be enabled:  
      * System > Protocol Settings > Roles & Protocols tab > OPENID CONNECT
    * Settings for SLO:
      * The host you'll use to access the app, typically either localhost or a Scalr IP address, needs to be configured in Redirect Validation settings:
        * Security > Redirect Validation > Add the host
      * Track user sessions for logout needs to be enabled in Authorization Server settings:
        * OAuth Server > Authorization Server Settings > TRACK USER SESSIONS FOR LOGOUT

## Usage

The collection is arranged in folders, and sub-folders based on the configuration performed, e.g. PF and PA.  In addition to the collection, there is an environment variable file that needs to be downloaded from this repo, and imported into Postman.  The collection is meant to be executed via Postman's Collection Runner.  In Collection Runner simply choose the "PA QuickStart Setup" collection and "PA-QuickStart" from the Environment dropdown.

More information on Postman Collection Runner can be found [here](https://learning.getpostman.com/docs/postman/collection_runs/intro_to_collection_runs/).

### Environment variables

The environment variable file contains a number of static and dynamic environment variables.  The static variables should be reviewed as they need to be modified to match your [environment](https://www.getpostman.com/docs/v6/postman/environments_and_globals/manage_environments).  The dynamic variables are used to store identifiers the collection will use to build dependent pieces of the configuration as it moves through the API requests, and thus should remained undefined.  

More information on managing Postman environments and variables can be found [here](https://www.getpostman.com/docs/v6/postman/environments_and_globals/variables).

### Static Variables That Need Review

|Variable  |Default value               |Example        |Notes                    |
|----------|----------------------------|---------------|-------------------------|
|`pfHost`  |``                          |`10.101.40.197`|Used by Postman to access PF Admin API|
|`paHost`  |``                          |`10.101.40.197`|Used by Postman to access PA Admin API|
|`pfUn`    |`Administrator`             |`Administrator`|PF Admin username|
|`pfPw`    |``                          |`2Federate`    |PF Admin password|
|`paUn`    |`Administrator`             |`Administrator`|PA Admin username|
|`paPw`    |``                          |`2Access`      |PA Admin password|
|`v`       |`v3`                        |`v3`           |PA Admin API version|
|`virtualHost`|`localhost`              |`localhost`    |The host that will be used to access the app|

### Dynamic Variables (Should Stay Undefined)

|Variable  |Notes                                                        |Use Case|
|----------|-------------------------------------------------------------|--------|
|`virtualHostId`|ID of the Virtual Host created                          |Both    |
|`scopeRuleId`|ID of the OAuth Scope Rule created                        |API App |
|`attrRuleId`|ID of the OAuth Attribute Rule created                     |API App |
|`webruleId`|ID of the Web Session Attribute Rule created                |Web App |
|`apiRSId`|ID of the Rule Set created                                    |API App |
|`apiMapId`|ID of the API Identity Mapping created                       |API App |
|`webMapId`|ID of the Web Identity Mapping created                       |Web App |
|`webSessionId`|ID of the Web Session created                            |Web App |
|`pfCertId`|ID of the primary PF runtime SSL cert                        |Both    |
|`pfCertData`|The primary PF runtime SSL cert data                       |Both    |
|`certGroupId`|ID of the Trusted Certificate Group created               |Both    |
|`stieId`  |ID of the Site created for the apps                          |Both    |
|`webAppId`|ID of the Web App created                                    |Web App |
|`rootResourceId`|ID of the Web App Root Resource, modified to Anonymous |Web App |
|`apiAppId`|ID of the API App created                                    |API App |

### PA Token Provider Configuration

By default the collection will attempt to setup your PF instance as the Token Provider for your PA instance.  If you've already configured this simply unselect the following three API requests in Collection Runner prior to running the collection:
* PUT Update PF Admin Config
* PUT Update PF Engine Config
* PUT Update PF Auth Server Config

### Accessing PAQuickStart App

Once the collection run is completed you should be able to access the application via the following URL:
* *https://{virtualHost}:3000/PingAccessQuickStart/home*

In addition, the collection creates a simple PCV in PF with the following three users (all three have the same password which is *2Federate*):
* joe
* sarah
* test

### Change Log

[See ChangeLog here](CHANGELOG.md)

## See Also

[Ping Identity APIs](https://www.pingidentity.com/content/developer/en/explore.html)

[Postman API development tool](https://www.getpostman.com/)
