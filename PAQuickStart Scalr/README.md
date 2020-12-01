# PingAccess QuickStart Application Scalr Postman Collection

A Postman collection that uses the  [PingFederate](https://support.pingidentity.com/s/document-item?bundleId=pingfederate-93&topicId=gettingStartedGuide%2FgettingStarted.html) and [PingAccess](https://support.pingidentity.com/s/document-item?bundleId=pingaccess-52&topicId=overview%2Fpa_c_PingAccess_Overview.html) Admin REST APIs to setup and configure the PAQuickStart app on Scalr VMs.  Unlike the PAQuickStart python script or data.zip, this collection will not overwrite your existing PF and PA configuration.  Instead it simply uses the Admin APIs to add the configuration necessary for the PAQuickStart app to your existing PF and PA instances.  In addition, this collection could be used for illustrative purposes, to show how you can automate the setup/configuration of an application in PA via the Admin APIs.

## Installation

To use the latest published version, click the following button to import the PA QuickStart Setup collection into Postman:

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/1d1926a58e139c6125af#?env%5BPA-QuickStart-Scalr%5D=W3sia2V5IjoicGZIb3N0IiwidmFsdWUiOiIxMC4xMDEuNTAuNSIsImVuYWJsZWQiOnRydWV9LHsia2V5IjoicGFIb3N0IiwidmFsdWUiOiIxMC4xMDEuNjAuMTcxIiwiZW5hYmxlZCI6dHJ1ZX0seyJrZXkiOiJzZXJ2ZXJOYW1lIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6InBjdklkIiwidmFsdWUiOiJTaW1wbGVQQVF1aWNrU3RhcnQiLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6ImlkcEFkYXB0ZXJJZCIsInZhbHVlIjoiSFRNTFBBUXVpY2tTdGFydCIsImVuYWJsZWQiOnRydWV9LHsia2V5IjoiY2xpZW50U2VjcmV0IiwidmFsdWUiOiIyRmVkZXJhdGUiLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6InBmVW4iLCJ2YWx1ZSI6IkFkbWluaXN0cmF0b3IiLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6InBmUHciLCJ2YWx1ZSI6IjJGZWRlcmF0ZSIsImVuYWJsZWQiOnRydWV9LHsia2V5IjoicGFVbiIsInZhbHVlIjoiQWRtaW5pc3RyYXRvciIsImVuYWJsZWQiOnRydWV9LHsia2V5IjoicGFQdyIsInZhbHVlIjoiMkFjY2VzcyIsImVuYWJsZWQiOnRydWV9LHsia2V5IjoidiIsInZhbHVlIjoidjMiLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6InBhVmlydHVhbEhvc3RJZCIsInZhbHVlIjozLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6InBmVmlydHVhbEhvc3RJZCIsInZhbHVlIjo0LCJlbmFibGVkIjp0cnVlfSx7ImtleSI6InNjb3BlUnVsZUlkIiwidmFsdWUiOjEsImVuYWJsZWQiOnRydWV9LHsia2V5IjoiYXR0clJ1bGVJZCIsInZhbHVlIjoyLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6IndlYlJ1bGVJZCIsInZhbHVlIjozLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6ImFwaVJTSWQiLCJ2YWx1ZSI6MSwiZW5hYmxlZCI6dHJ1ZX0seyJrZXkiOiJhcGlNYXBJZCIsInZhbHVlIjoxLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6IndlYk1hcElkIiwidmFsdWUiOjIsImVuYWJsZWQiOnRydWV9LHsia2V5Ijoid2ViU2Vzc2lvbklkIiwidmFsdWUiOjEsImVuYWJsZWQiOnRydWV9LHsia2V5IjoicGZDZXJ0SWQiLCJ2YWx1ZSI6InlmaWFxcXJ4aWIwczM2ZmppdjdsaWNnZHEiLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6InBmQ2VydERhdGEiLCJ2YWx1ZSI6Ii0tLS0tQkVHSU4gQ0VSVElGSUNBVEUtLS0tLVxuTUlJRGpUQ0NBbldnQXdJQkFnSUdBWFliVll2Y01BMEdDU3FHU0liM0RRRUJDd1VBTUc0eEN6QUpCZ05WQkFZVEFsVlRNUXN3Q1FZRFxuVlFRSUV3SkRUekVQTUEwR0ExVUVCeE1HUkdWdWRtVnlNUlV3RXdZRFZRUUtFd3hRYVc1blNXUmxiblJwZEhreEZEQVNCZ05WQkFzVFxuQzBSbGRtVnNiM0J0Wlc1ME1SUXdFZ1lEVlFRREV3c3hNQzR4TURFdU5UQXVOVEFlRncweU1ERXhNekF5TWpRMU5UbGFGdzB6TURFeFxuTWpneU1qUTFOVGxhTUc0eEN6QUpCZ05WQkFZVEFsVlRNUXN3Q1FZRFZRUUlFd0pEVHpFUE1BMEdBMVVFQnhNR1JHVnVkbVZ5TVJVd1xuRXdZRFZRUUtFd3hRYVc1blNXUmxiblJwZEhreEZEQVNCZ05WQkFzVEMwUmxkbVZzYjNCdFpXNTBNUlF3RWdZRFZRUURFd3N4TUM0eFxuTURFdU5UQXVOVENDQVNJd0RRWUpLb1pJaHZjTkFRRUJCUUFEZ2dFUEFEQ0NBUW9DZ2dFQkFPL1ZwRUZSWEhXa1RIbk1TQmRvWWs5d1xubTEySzQ5MUp3SWtYRTREMkt0WjNOQUdjVUFubGh1ajdCTzl4bno1aXVCcEdSR0JEQ0k1Q2pCMDhYbjluNlpQLys2MGh2UG9xRlEwclxueGkrKzdOcURLSWNLSkNudlRtQ2drNXFpbE4yc3Rza2RNNHNLWVoyek9WRHRjV1ZwMHc2NGdlTzZ2SzZucXo4RktBWUZYbFVvNkhUYVxuWkNpQm1iOE9oWTFpMWtKSXRFa1dvNVNLSDdjUDAxL0NyajdKalJCcXFUTjBHSXZlRW9GSHNDWHlwWUtXcTcyVjdLdkh3azdyd2VSdlxuaHp4QVA3aFg4UzlXaFJ5ZWJWWGNtSDgyZ0w4b1JGNHlDZm5BMFlxbmNETGVndjhKc1MwK2NDZkE5dWJHZmtmR1VxRFVTWk85SC96blxuWnc0VjJhS01scjBmMTZrQ0F3RUFBYU14TUM4d0xRWURWUjBSQkNZd0pJSUpiRzlqWVd4b2IzTjBnaEZ3WkcxbGRISnBZM010TURFdFxuTlRBdE5ZY0VDbVV5QlRBTkJna3Foa2lHOXcwQkFRc0ZBQU9DQVFFQWlmczNxdmhjRWE0bkJ5N0VRWUtZNUdkQ1hpUjJRbGpXNkRFR1xuWWwvQXduQ1AvZVpYOEtLdG9ySVV3R3o1dGhPYnRFL0lSTHBCOFFQZkwyUW5pUForVzhvei9qbkFYckkzV2JKOEk2ejNXbmk5by9VUlxuSDNFY3EyMkFXOWVhTjgyNFlib245L1BWWHlEVFh6RkdBV3ZTTFFmUml1dUxURU1QUVhRYWNZNU56VWRhWHJsUkxWVlVmbGxuSkFIZ1xuOWY3d2w4NmtVQ3dOZXAwK05TT3NpRDdnd2o0anp0MEV6VUt1NmxLakhqLzNxaTZRVXJNTHpYL3ZnZ2J1cEI5N3lhcGVXdUs1TE8veVxuQ2I0WjV0RjVQaDVQNXpXS2ttVFNMTUNmZWVZajVUZmt5VkJZZ2VxQ0VzK045M0x3SHRMQ256aVc0d3BOSkF6VFdualppMXlzdDc0dlxuMXc9PVxuLS0tLS1FTkQgQ0VSVElGSUNBVEUtLS0tLVxuIiwiZW5hYmxlZCI6dHJ1ZX0seyJrZXkiOiJjZXJ0SWQiLCJ2YWx1ZSI6MSwiZW5hYmxlZCI6dHJ1ZX0seyJrZXkiOiJjZXJ0R3JvdXBJZCIsInZhbHVlIjozLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6InNpdGVJZCIsInZhbHVlIjoxLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6IndlYkFwcElkIiwidmFsdWUiOjIsImVuYWJsZWQiOnRydWV9LHsia2V5Ijoicm9vdFJlc291cmNlSWQiLCJ2YWx1ZSI6MiwiZW5hYmxlZCI6dHJ1ZX0seyJrZXkiOiJhcGlBcHBJZCIsInZhbHVlIjoxLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6InBBVmlydHVhbEhvc3RJZCIsInZhbHVlIjozLCJlbmFibGVkIjp0cnVlfV0=)

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
