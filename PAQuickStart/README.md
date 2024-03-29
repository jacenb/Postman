# PingAccess QuickStart Application Postman Collection

A Postman collection that uses the  [PingFederate](https://support.pingidentity.com/s/document-item?bundleId=pingfederate-93&topicId=gettingStartedGuide%2FgettingStarted.html) and [PingAccess](https://support.pingidentity.com/s/document-item?bundleId=pingaccess-52&topicId=overview%2Fpa_c_PingAccess_Overview.html) Admin REST APIs to setup and configure the PAQuickStart app.  Unlike the PAQuickStart python script or data.zip, this collection will not overwrite your existing PF and PA configuration.  Instead it simply uses the Admin APIs to add the configuration necessary for the PAQuickStart app to your existing PF and PA instances.  In addition, this collection could be used for illustrative purposes, to show how you can automate the setup/configuration of an application in PA via the Admin APIs.

## Installation

To use the latest published version, click the following button to import the PA QuickStart Setup collection into Postman:

[<img src="https://run.pstmn.io/button.svg" alt="Run In Postman" style="width: 128px; height: 32px;">](https://app.getpostman.com/run-collection/8082918-d0a1d9b9-9e54-4a40-82ec-64ec52a4e131?action=collection%2Ffork&source=rip_markdown&collection-url=entityId%3D8082918-d0a1d9b9-9e54-4a40-82ec-64ec52a4e131%26entityType%3Dcollection%26workspaceId%3D331aedb8-ca88-4365-b53f-4d947e2d8b7d#?env%5BPA-QuickStart%5D=W3sia2V5IjoicGZIb3N0IiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjB9LHsia2V5IjoicGFIb3N0IiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjF9LHsia2V5IjoicGN2SWQiLCJ2YWx1ZSI6IlNpbXBsZVBBUXVpY2tTdGFydCIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IlNpbXBsZVBBUXVpY2tTdGFydCIsInNlc3Npb25JbmRleCI6Mn0seyJrZXkiOiJpZHBBZGFwdGVySWQiLCJ2YWx1ZSI6IkhUTUxQQVF1aWNrU3RhcnQiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiJIVE1MUEFRdWlja1N0YXJ0Iiwic2Vzc2lvbkluZGV4IjozfSx7ImtleSI6ImNsaWVudFNlY3JldCIsInZhbHVlIjoiMkZlZGVyYXRlIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiMkZlZGVyYXRlIiwic2Vzc2lvbkluZGV4Ijo0fSx7ImtleSI6InBmVW4iLCJ2YWx1ZSI6IkFkbWluaXN0cmF0b3IiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiJBZG1pbmlzdHJhdG9yIiwic2Vzc2lvbkluZGV4Ijo1fSx7ImtleSI6InBmUHciLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IiIsInNlc3Npb25JbmRleCI6Nn0seyJrZXkiOiJwYVVuIiwidmFsdWUiOiJBZG1pbmlzdHJhdG9yIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiQWRtaW5pc3RyYXRvciIsInNlc3Npb25JbmRleCI6N30seyJrZXkiOiJwYVB3IiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjh9LHsia2V5IjoidiIsInZhbHVlIjoidjMiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiJ2MyIsInNlc3Npb25JbmRleCI6OX0seyJrZXkiOiJ2aXJ0dWFsSG9zdCIsInZhbHVlIjoibG9jYWxob3N0IiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoibG9jYWxob3N0Iiwic2Vzc2lvbkluZGV4IjoxMH0seyJrZXkiOiJ2aXJ0dWFsSG9zdElkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjExfSx7ImtleSI6InNjb3BlUnVsZUlkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjEyfSx7ImtleSI6ImF0dHJSdWxlSWQiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IiIsInNlc3Npb25JbmRleCI6MTN9LHsia2V5Ijoid2ViUnVsZUlkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjE0fSx7ImtleSI6ImFwaVJTSWQiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IiIsInNlc3Npb25JbmRleCI6MTV9LHsia2V5IjoiYXBpTWFwSWQiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IiIsInNlc3Npb25JbmRleCI6MTZ9LHsia2V5Ijoid2ViTWFwSWQiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IiIsInNlc3Npb25JbmRleCI6MTd9LHsia2V5Ijoid2ViU2Vzc2lvbklkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjE4fSx7ImtleSI6InBmQ2VydElkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjE5fSx7ImtleSI6InBmQ2VydERhdGEiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IiIsInNlc3Npb25JbmRleCI6MjB9LHsia2V5IjoiY2VydElkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjIxfSx7ImtleSI6ImNlcnRHcm91cElkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjIyfSx7ImtleSI6InNpdGVJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiIiwic2Vzc2lvbkluZGV4IjoyM30seyJrZXkiOiJ3ZWJBcHBJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiIiwic2Vzc2lvbkluZGV4IjoyNH0seyJrZXkiOiJyb290UmVzb3VyY2VJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiIiwic2Vzc2lvbkluZGV4IjoyNX0seyJrZXkiOiJhcGlBcHBJZCIsInZhbHVlIjpudWxsLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiJudWxsIiwic2Vzc2lvbkluZGV4IjoyNn1d)

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
