# PingAccess QuickStart Application Postman Collection

A Postman collection that uses the  [PingFederate](https://support.pingidentity.com/s/document-item?bundleId=pingfederate-93&topicId=gettingStartedGuide%2FgettingStarted.html) and [PingAccess](https://support.pingidentity.com/s/document-item?bundleId=pingaccess-52&topicId=overview%2Fpa_c_PingAccess_Overview.html) Admin REST APIs to setup and configure the PAQuickStart app.  Unlike the PAQuickStart python script or data.zip, this collection will not overwrite your existing PF and PA configuration.  Instead it simply uses the Admin APIs to add the configuration necessary for the PAQuickStart app to your existing PF and PA instances.  In addition, this collection could be used for illustrative purposes, to show how you can automate the setup/configuration of an application in PA via the Admin APIs.

## Installation

To use the latest published version, click the following button to import the PA QuickStart Setup collection into Postman:

[<img src="https://run.pstmn.io/button.svg" alt="Run In Postman" style="width: 128px; height: 32px;">](https://app.getpostman.com/run-collection/8082918-99dbdbb3-107c-406c-9e3f-77c45df5aae0?action=collection%2Ffork&source=rip_markdown&collection-url=entityId%3D8082918-99dbdbb3-107c-406c-9e3f-77c45df5aae0%26entityType%3Dcollection%26workspaceId%3D712cb1d6-b1d2-4bfe-b431-192f60a202d5#?env%5BPA-QuickStart%5D=W3sia2V5IjoicGZIb3N0IiwidmFsdWUiOiJsb2NhbGhvc3QiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoidGV4dCIsInNlc3Npb25WYWx1ZSI6ImxvY2FsaG9zdCIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoibG9jYWxob3N0Iiwic2Vzc2lvbkluZGV4IjowfSx7ImtleSI6InBhSG9zdCIsInZhbHVlIjoibG9jYWxob3N0IiwiZW5hYmxlZCI6dHJ1ZSwidHlwZSI6InRleHQiLCJzZXNzaW9uVmFsdWUiOiJsb2NhbGhvc3QiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6ImxvY2FsaG9zdCIsInNlc3Npb25JbmRleCI6MX0seyJrZXkiOiJwY3ZJZCIsInZhbHVlIjoiU2ltcGxlUEFRdWlja1N0YXJ0IiwiZW5hYmxlZCI6dHJ1ZSwidHlwZSI6InRleHQiLCJzZXNzaW9uVmFsdWUiOiJTaW1wbGVQQVF1aWNrU3RhcnQiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6IlNpbXBsZVBBUXVpY2tTdGFydCIsInNlc3Npb25JbmRleCI6Mn0seyJrZXkiOiJpZHBBZGFwdGVySWQiLCJ2YWx1ZSI6IkhUTUxQQVF1aWNrU3RhcnQiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoidGV4dCIsInNlc3Npb25WYWx1ZSI6IkhUTUxQQVF1aWNrU3RhcnQiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6IkhUTUxQQVF1aWNrU3RhcnQiLCJzZXNzaW9uSW5kZXgiOjN9LHsia2V5IjoiY2xpZW50U2VjcmV0IiwidmFsdWUiOiIyRmVkZXJhdGUiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoidGV4dCIsInNlc3Npb25WYWx1ZSI6IjJGZWRlcmF0ZSIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoiMkZlZGVyYXRlIiwic2Vzc2lvbkluZGV4Ijo0fSx7ImtleSI6InBmVW4iLCJ2YWx1ZSI6IkFkbWluaXN0cmF0b3IiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoidGV4dCIsInNlc3Npb25WYWx1ZSI6IkFkbWluaXN0cmF0b3IiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6IkFkbWluaXN0cmF0b3IiLCJzZXNzaW9uSW5kZXgiOjV9LHsia2V5IjoicGZQdyIsInZhbHVlIjoiMkZlZGVyYXRlIiwiZW5hYmxlZCI6dHJ1ZSwidHlwZSI6InRleHQiLCJzZXNzaW9uVmFsdWUiOiIyRmVkZXJhdGUiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6IjJGZWRlcmF0ZSIsInNlc3Npb25JbmRleCI6Nn0seyJrZXkiOiJwYVVuIiwidmFsdWUiOiJBZG1pbmlzdHJhdG9yIiwiZW5hYmxlZCI6dHJ1ZSwidHlwZSI6InRleHQiLCJzZXNzaW9uVmFsdWUiOiJBZG1pbmlzdHJhdG9yIiwiY29tcGxldGVTZXNzaW9uVmFsdWUiOiJBZG1pbmlzdHJhdG9yIiwic2Vzc2lvbkluZGV4Ijo3fSx7ImtleSI6InBhUHciLCJ2YWx1ZSI6IjJBY2Nlc3MiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoidGV4dCIsInNlc3Npb25WYWx1ZSI6IjJBY2Nlc3MiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6IjJBY2Nlc3MiLCJzZXNzaW9uSW5kZXgiOjh9LHsia2V5IjoidiIsInZhbHVlIjoidjMiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoidGV4dCIsInNlc3Npb25WYWx1ZSI6InYzIiwiY29tcGxldGVTZXNzaW9uVmFsdWUiOiJ2MyIsInNlc3Npb25JbmRleCI6OX0seyJrZXkiOiJ2aXJ0dWFsSG9zdCIsInZhbHVlIjoibG9jYWxob3N0IiwiZW5hYmxlZCI6dHJ1ZSwidHlwZSI6InRleHQiLCJzZXNzaW9uVmFsdWUiOiJsb2NhbGhvc3QiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6ImxvY2FsaG9zdCIsInNlc3Npb25JbmRleCI6MTB9LHsia2V5IjoidmlydHVhbEhvc3RJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwidHlwZSI6InRleHQiLCJzZXNzaW9uVmFsdWUiOiIxIiwiY29tcGxldGVTZXNzaW9uVmFsdWUiOjEsInNlc3Npb25JbmRleCI6MTF9LHsia2V5Ijoic2NvcGVSdWxlSWQiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInR5cGUiOiJ0ZXh0Iiwic2Vzc2lvblZhbHVlIjoiMSIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoxLCJzZXNzaW9uSW5kZXgiOjEyfSx7ImtleSI6ImF0dHJSdWxlSWQiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInR5cGUiOiJ0ZXh0Iiwic2Vzc2lvblZhbHVlIjoiMiIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoyLCJzZXNzaW9uSW5kZXgiOjEzfSx7ImtleSI6IndlYlJ1bGVJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwidHlwZSI6InRleHQiLCJzZXNzaW9uVmFsdWUiOiIzIiwiY29tcGxldGVTZXNzaW9uVmFsdWUiOjMsInNlc3Npb25JbmRleCI6MTR9LHsia2V5IjoiYXBpUlNJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwidHlwZSI6InRleHQiLCJzZXNzaW9uVmFsdWUiOiIxIiwiY29tcGxldGVTZXNzaW9uVmFsdWUiOjEsInNlc3Npb25JbmRleCI6MTV9LHsia2V5IjoiYXBpTWFwSWQiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInR5cGUiOiJ0ZXh0Iiwic2Vzc2lvblZhbHVlIjoiMSIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoxLCJzZXNzaW9uSW5kZXgiOjE2fSx7ImtleSI6IndlYk1hcElkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoidGV4dCIsInNlc3Npb25WYWx1ZSI6IjIiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6Miwic2Vzc2lvbkluZGV4IjoxN30seyJrZXkiOiJ3ZWJTZXNzaW9uSWQiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInR5cGUiOiJ0ZXh0Iiwic2Vzc2lvblZhbHVlIjoiMSIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoxLCJzZXNzaW9uSW5kZXgiOjE4fSx7ImtleSI6InBmQ2VydElkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoidGV4dCIsInNlc3Npb25WYWx1ZSI6IjYwdjZxczl0cTBzaXU1ZGY1bnZ4dDlzeTIiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6IjYwdjZxczl0cTBzaXU1ZGY1bnZ4dDlzeTIiLCJzZXNzaW9uSW5kZXgiOjE5fSx7ImtleSI6InBmQ2VydERhdGEiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInR5cGUiOiJ0ZXh0Iiwic2Vzc2lvblZhbHVlIjoiLS0tLS1CRUdJTi4uLiIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoiLS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tXG5NSUlEYnpDQ0FsZWdBd0lCQWdJR0FaY2N1QXY5TUEwR0NTcUdTSWIzRFFFQkN3VUFNR3d4Q3pBSkJnTlZCQVlUQWxWVE1Rc3dDUVlEXG5WUVFJRXdKRFR6RVBNQTBHQTFVRUJ4TUdSR1Z1ZG1WeU1SVXdFd1lEVlFRS0V3eFFhVzVuU1dSbGJuUnBkSGt4RkRBU0JnTlZCQXNUXG5DMFJsZG1Wc2IzQnRaVzUwTVJJd0VBWURWUVFERXdsc2IyTmhiR2h2YzNRd0hoY05NalV3TlRJNU1UVTBOVEV6V2hjTk16VXdOVE13XG5NVFUwTlRFeldqQnNNUXN3Q1FZRFZRUUdFd0pWVXpFTE1Ba0dBMVVFQ0JNQ1EwOHhEekFOQmdOVkJBY1RCa1JsYm5abGNqRVZNQk1HXG5BMVVFQ2hNTVVHbHVaMGxrWlc1MGFYUjVNUlF3RWdZRFZRUUxFd3RFWlhabGJHOXdiV1Z1ZERFU01CQUdBMVVFQXhNSmJHOWpZV3hvXG5iM04wTUlJQklqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FROEFNSUlCQ2dLQ0FRRUExMmd0bEpMcmJ1SFR5aDVqK2hST25PYlExQlZvXG5jMVoyYWNFTWZrZEpzMGNLbzBjK0gybHErTFcyUUZvSjMwUEpLZEtPakcwdmZjeVl6SEt5VFNaaHg0ckRaaXVKcEdxUDlndTRnblovXG4vSnRUSlZQUllQczJieWVBR3UrYzgyWERCQlY0SVZaMit4cVZ6TXROdkErcW1WN1RHcFJ1V3R2V21DVjZya3VaNDNZeUNJenc5Z2FyXG5WTGRvUVQ3d2U1aGloMEk0VWFtTjNqd2d6RDdrZ2g5RDMwbW0vL0dnQjJZZlhldndzL25HNXExVytLUXhBZDFqZUJYS0ZmTTREMXdKXG5LL1VoVHZHdmdWT0x2ZTZETzk0aVRlZStmS3RhdWpJbVNEUllicTdOSm96YllCUklLM1FGY0dBclpMMXVLb1kwaFZPTEVMcURST2xtXG5aLzVUUmtxdGZRSURBUUFCb3hjd0ZUQVRCZ05WSFNVRUREQUtCZ2dyQmdFRkJRY0RBVEFOQmdrcWhraUc5dzBCQVFzRkFBT0NBUUVBXG5JdWpOY3FJeWRTL1BpaWFaTmZDdmk5R1AvNFdUa3Q5OUpBaERvNzZBN0pOV3lqbzRPeDNRZHRRNWpDRlVYV1l4QnZNbWs1U05HYWhDXG45K3FPZ2xTU3AwQ01YWTAveUhKOFNLRnBaSXgvcVQrQVd3T2NYTldibmVhRWlnVTVpUmR0QnllVUl3aDBuU2xDbUJqcGNab0FCd1U4XG5vc1BPU3U2WU9nRVVHR0ZIQ2YvcEtUb09yaWZXSkNmRVE4T1ZReWxrdytjdFJremttbW1ZWHF6TFJNZ29oa2FqeFFzUXJxNTFzakk1XG5mdVh2OVJidjg0S3AwdlJZRG9va2NLemhzU0JlaFhBeTVTdkRTNlVYOXhHdHRaQmI0ZkV1WWNsSU5VZzNpcHd3RzV2d1VGR0xFbG5rXG5YODFQQkV5ZVhpUk9sL3d0emQ5VFJtUFJTUm5nZnI4TGR3YThxQT09XG4tLS0tLUVORCBDRVJUSUZJQ0FURS0tLS0tXG4iLCJzZXNzaW9uSW5kZXgiOjIwfSx7ImtleSI6ImNlcnRJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwidHlwZSI6InRleHQiLCJzZXNzaW9uVmFsdWUiOiIxIiwiY29tcGxldGVTZXNzaW9uVmFsdWUiOjEsInNlc3Npb25JbmRleCI6MjF9LHsia2V5IjoiY2VydEdyb3VwSWQiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInR5cGUiOiJ0ZXh0Iiwic2Vzc2lvblZhbHVlIjoiMyIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjozLCJzZXNzaW9uSW5kZXgiOjIyfSx7ImtleSI6InNpdGVJZCIsInZhbHVlIjoiIiwiZW5hYmxlZCI6dHJ1ZSwidHlwZSI6InRleHQiLCJzZXNzaW9uVmFsdWUiOiIxIiwiY29tcGxldGVTZXNzaW9uVmFsdWUiOjEsInNlc3Npb25JbmRleCI6MjN9LHsia2V5Ijoid2ViQXBwSWQiLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInR5cGUiOiJ0ZXh0Iiwic2Vzc2lvblZhbHVlIjoiMiIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoyLCJzZXNzaW9uSW5kZXgiOjI0fSx7ImtleSI6InJvb3RSZXNvdXJjZUlkIiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoidGV4dCIsInNlc3Npb25WYWx1ZSI6IjIiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6Miwic2Vzc2lvbkluZGV4IjoyNX0seyJrZXkiOiJhcGlBcHBJZCIsInZhbHVlIjpudWxsLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoidGV4dCIsInNlc3Npb25WYWx1ZSI6IjEiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6MSwic2Vzc2lvbkluZGV4IjoyNn1d)

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
