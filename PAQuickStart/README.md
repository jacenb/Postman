# PingAccess QuickStart Application Postman Collection

A Postman collection that uses the  [PingFederate](https://support.pingidentity.com/s/document-item?bundleId=pingfederate-93&topicId=gettingStartedGuide%2FgettingStarted.html) and [PingAccess](https://support.pingidentity.com/s/document-item?bundleId=pingaccess-52&topicId=overview%2Fpa_c_PingAccess_Overview.html) Admin REST APIs to setup and configure the PAQuickStart app.  Unlike the PAQuickStart python script or data.zip, this collection will not overwrite your existing PF and PA configuration.  Instead it simply uses the Admin APIs to add the configuration necessary for the PAQuickStart app to your existing PF and PA instances.  In addition, this collection could be used for illustrative purposes, to show how you can automate the setup/configuration of an application in PA via the Admin APIs.

## Installation

To use the latest published version, click the following button to import the PA QuickStart Setup collection into Postman:

[<img src="https://run.pstmn.io/button.svg" alt="Run In Postman" style="width: 128px; height: 32px;">](https://app.getpostman.com/run-collection/8082918-0ad61645-ba99-4ee5-9007-a94dccaea6d4?action=collection%2Ffork&source=rip_markdown&collection-url=entityId%3D8082918-0ad61645-ba99-4ee5-9007-a94dccaea6d4%26entityType%3Dcollection%26workspaceId%3Df4489be6-a2b7-4b76-99f6-6c93f44c33f3#?env%5BPA-QuickStart%5D=W3sia2V5IjoicGZIb3N0IiwidmFsdWUiOiJsb2NhbGhvc3QiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiJsb2NhbGhvc3QiLCJzZXNzaW9uSW5kZXgiOjB9LHsia2V5IjoicGFIb3N0IiwidmFsdWUiOiJsb2NhbGhvc3QiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiJsb2NhbGhvc3QiLCJzZXNzaW9uSW5kZXgiOjF9LHsia2V5IjoicGN2SWQiLCJ2YWx1ZSI6IlNpbXBsZVBBUXVpY2tTdGFydCIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IlNpbXBsZVBBUXVpY2tTdGFydCIsInNlc3Npb25JbmRleCI6Mn0seyJrZXkiOiJpZHBBZGFwdGVySWQiLCJ2YWx1ZSI6IkhUTUxQQVF1aWNrU3RhcnQiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiJIVE1MUEFRdWlja1N0YXJ0Iiwic2Vzc2lvbkluZGV4IjozfSx7ImtleSI6ImNsaWVudFNlY3JldCIsInZhbHVlIjoiMkZlZGVyYXRlIiwiZW5hYmxlZCI6dHJ1ZSwidHlwZSI6ImRlZmF1bHQiLCJzZXNzaW9uVmFsdWUiOiIyRmVkZXJhdGUiLCJzZXNzaW9uSW5kZXgiOjR9LHsia2V5IjoicGZVbiIsInZhbHVlIjoiQWRtaW5pc3RyYXRvciIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IkFkbWluaXN0cmF0b3IiLCJzZXNzaW9uSW5kZXgiOjV9LHsia2V5IjoicGZQdyIsInZhbHVlIjoiMkZlZGVyYXRlIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiMkZlZGVyYXRlIiwic2Vzc2lvbkluZGV4Ijo2fSx7ImtleSI6InBhVW4iLCJ2YWx1ZSI6IkFkbWluaXN0cmF0b3IiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiJBZG1pbmlzdHJhdG9yIiwic2Vzc2lvbkluZGV4Ijo3fSx7ImtleSI6InBhUHciLCJ2YWx1ZSI6IjJBY2Nlc3MiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIyQWNjZXNzIiwic2Vzc2lvbkluZGV4Ijo4fSx7ImtleSI6InYiLCJ2YWx1ZSI6InYzIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoidjMiLCJzZXNzaW9uSW5kZXgiOjl9LHsia2V5IjoidmlydHVhbEhvc3QiLCJ2YWx1ZSI6ImxvY2FsaG9zdCIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6ImxvY2FsaG9zdCIsInNlc3Npb25JbmRleCI6MTB9LHsia2V5IjoidmlydHVhbEhvc3RJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiIiwic2Vzc2lvbkluZGV4IjoxMX0seyJrZXkiOiJzY29wZVJ1bGVJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiIiwic2Vzc2lvbkluZGV4IjoxMn0seyJrZXkiOiJhdHRyUnVsZUlkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjEzfSx7ImtleSI6IndlYlJ1bGVJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiIiwic2Vzc2lvbkluZGV4IjoxNH0seyJrZXkiOiJhcGlSU0lkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjE1fSx7ImtleSI6ImFwaU1hcElkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjE2fSx7ImtleSI6IndlYk1hcElkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjE3fSx7ImtleSI6IndlYlNlc3Npb25JZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiIiwic2Vzc2lvbkluZGV4IjoxOH0seyJrZXkiOiJwZkNlcnRJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiIiwic2Vzc2lvbkluZGV4IjoxOX0seyJrZXkiOiJwZkNlcnREYXRhIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjIwfSx7ImtleSI6ImNlcnRJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiIiwic2Vzc2lvbkluZGV4IjoyMX0seyJrZXkiOiJjZXJ0R3JvdXBJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiIiwic2Vzc2lvbkluZGV4IjoyMn0seyJrZXkiOiJzaXRlSWQiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IiIsInNlc3Npb25JbmRleCI6MjN9LHsia2V5Ijoid2ViQXBwSWQiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IiIsInNlc3Npb25JbmRleCI6MjR9LHsia2V5Ijoicm9vdFJlc291cmNlSWQiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IiIsInNlc3Npb25JbmRleCI6MjV9LHsia2V5IjoiYXBpQXBwSWQiLCJ2YWx1ZSI6bnVsbCwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoibnVsbCIsInNlc3Npb25JbmRleCI6MjZ9XQ==)

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
