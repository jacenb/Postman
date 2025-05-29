# PingAccess QuickStart Application Scalr Postman Collection

A Postman collection that uses the  [PingFederate](https://support.pingidentity.com/s/document-item?bundleId=pingfederate-93&topicId=gettingStartedGuide%2FgettingStarted.html) and [PingAccess](https://support.pingidentity.com/s/document-item?bundleId=pingaccess-52&topicId=overview%2Fpa_c_PingAccess_Overview.html) Admin REST APIs to setup and configure the PAQuickStart app on Scalr VMs.  Unlike the PAQuickStart python script or data.zip, this collection will not overwrite your existing PF and PA configuration.  Instead it simply uses the Admin APIs to add the configuration necessary for the PAQuickStart app to your existing PF and PA instances.  In addition, this collection could be used for illustrative purposes, to show how you can automate the setup/configuration of an application in PA via the Admin APIs.

## Installation

To use the latest published version, click the following button to import the PA QuickStart Setup collection into Postman:

[<img src="https://run.pstmn.io/button.svg" alt="Run In Postman" style="width: 128px; height: 32px;">](https://app.getpostman.com/run-collection/8082918-a7e8beb6-01d2-42b9-b8dd-2d258a0b492a?action=collection%2Ffork&source=rip_markdown&collection-url=entityId%3D8082918-a7e8beb6-01d2-42b9-b8dd-2d258a0b492a%26entityType%3Dcollection%26workspaceId%3D712cb1d6-b1d2-4bfe-b431-192f60a202d5#?env%5BPA-QuickStart-Scalr%5D=W3sia2V5IjoicGZIb3N0IiwidmFsdWUiOiIxMC4xMDEuNTAuNSIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IiIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoiIiwic2Vzc2lvbkluZGV4IjowfSx7ImtleSI6InBhSG9zdCIsInZhbHVlIjoiMTAuMTAxLjYwLjE3MSIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IiIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoiIiwic2Vzc2lvbkluZGV4IjoxfSx7ImtleSI6InNlcnZlck5hbWUiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IiIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoiIiwic2Vzc2lvbkluZGV4IjoyfSx7ImtleSI6InBjdklkIiwidmFsdWUiOiJTaW1wbGVQQVF1aWNrU3RhcnQiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiJTaW1wbGVQQVF1aWNrU3RhcnQiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6IlNpbXBsZVBBUXVpY2tTdGFydCIsInNlc3Npb25JbmRleCI6M30seyJrZXkiOiJpZHBBZGFwdGVySWQiLCJ2YWx1ZSI6IkhUTUxQQVF1aWNrU3RhcnQiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiJIVE1MUEFRdWlja1N0YXJ0IiwiY29tcGxldGVTZXNzaW9uVmFsdWUiOiJIVE1MUEFRdWlja1N0YXJ0Iiwic2Vzc2lvbkluZGV4Ijo0fSx7ImtleSI6ImNsaWVudFNlY3JldCIsInZhbHVlIjoiMkZlZGVyYXRlIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiMkZlZGVyYXRlIiwiY29tcGxldGVTZXNzaW9uVmFsdWUiOiIyRmVkZXJhdGUiLCJzZXNzaW9uSW5kZXgiOjV9LHsia2V5IjoicGZVbiIsInZhbHVlIjoiQWRtaW5pc3RyYXRvciIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IkFkbWluaXN0cmF0b3IiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6IkFkbWluaXN0cmF0b3IiLCJzZXNzaW9uSW5kZXgiOjZ9LHsia2V5IjoicGZQdyIsInZhbHVlIjoiMkZlZGVyYXRlIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiMkZlZGVyYXRlIiwiY29tcGxldGVTZXNzaW9uVmFsdWUiOiIyRmVkZXJhdGUiLCJzZXNzaW9uSW5kZXgiOjd9LHsia2V5IjoicGFVbiIsInZhbHVlIjoiQWRtaW5pc3RyYXRvciIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IkFkbWluaXN0cmF0b3IiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6IkFkbWluaXN0cmF0b3IiLCJzZXNzaW9uSW5kZXgiOjh9LHsia2V5IjoicGFQdyIsInZhbHVlIjoiMkFjY2VzcyIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IjJBY2Nlc3MiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6IjJBY2Nlc3MiLCJzZXNzaW9uSW5kZXgiOjl9LHsia2V5IjoidiIsInZhbHVlIjoidjMiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiJ2MyIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoidjMiLCJzZXNzaW9uSW5kZXgiOjEwfSx7ImtleSI6InBhVmlydHVhbEhvc3RJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiIiwiY29tcGxldGVTZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjExfSx7ImtleSI6InBmVmlydHVhbEhvc3RJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiIiwiY29tcGxldGVTZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjEyfSx7ImtleSI6InNjb3BlUnVsZUlkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6IiIsInNlc3Npb25JbmRleCI6MTN9LHsia2V5IjoiYXR0clJ1bGVJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiIiwiY29tcGxldGVTZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjE0fSx7ImtleSI6IndlYlJ1bGVJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiIiwiY29tcGxldGVTZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjE1fSx7ImtleSI6ImFwaVJTSWQiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IiIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoiIiwic2Vzc2lvbkluZGV4IjoxNn0seyJrZXkiOiJhcGlNYXBJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiIiwiY29tcGxldGVTZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjE3fSx7ImtleSI6IndlYk1hcElkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6IiIsInNlc3Npb25JbmRleCI6MTh9LHsia2V5Ijoid2ViU2Vzc2lvbklkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6IiIsInNlc3Npb25JbmRleCI6MTl9LHsia2V5IjoicGZDZXJ0SWQiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IiIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoiIiwic2Vzc2lvbkluZGV4IjoyMH0seyJrZXkiOiJwZkNlcnREYXRhIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6IiIsInNlc3Npb25JbmRleCI6MjF9LHsia2V5IjoiY2VydElkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6IiIsInNlc3Npb25JbmRleCI6MjJ9LHsia2V5IjoiY2VydEdyb3VwSWQiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IiIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoiIiwic2Vzc2lvbkluZGV4IjoyM30seyJrZXkiOiJzaXRlSWQiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IiIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoiIiwic2Vzc2lvbkluZGV4IjoyNH0seyJrZXkiOiJ3ZWJBcHBJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwic2Vzc2lvblZhbHVlIjoiIiwiY29tcGxldGVTZXNzaW9uVmFsdWUiOiIiLCJzZXNzaW9uSW5kZXgiOjI1fSx7ImtleSI6InJvb3RSZXNvdXJjZUlkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJzZXNzaW9uVmFsdWUiOiIiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6IiIsInNlc3Npb25JbmRleCI6MjZ9LHsia2V5IjoiYXBpQXBwSWQiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInNlc3Npb25WYWx1ZSI6IiIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoiIiwic2Vzc2lvbkluZGV4IjoyN31d)

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

## Usage

The collection is arranged in folders, and sub-folders based on the configuration performed, e.g. PF and PA.  In addition to the collection, there is an environment variable file that needs to be downloaded from this repo, and imported into Postman.  The collection is meant to be executed via Postman's Collection Runner.  In Collection Runner simply choose the "PA QuickStart Setup Scalr" collection and "PA-QuickStart-Scalr" from the Environment dropdown.

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

### Dynamic Variables (Should Stay Undefined)

|Variable  |Notes                                                        |Use Case|
|----------|-------------------------------------------------------------|--------|
|`serverName`|Name of the PF Scalr VM, added as a SAN on the PF cert     |Both    |
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
* *https://{paHost}:3000/PingAccessQuickStart/home*

In addition, the collection creates a simple PCV in PF with the following three users (all three have the same password which is *2Federate*):
* joe
* sarah
* test

### Change Log

[See ChangeLog here](CHANGELOG.md)

## See Also

[Ping Identity APIs](https://www.pingidentity.com/content/developer/en/explore.html)

[Postman API development tool](https://www.getpostman.com/)
