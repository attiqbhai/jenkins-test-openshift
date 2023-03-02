Assumptions
-----------
	- JDK 1.8 is installed
	- Maven is installed

Instructions to build and deploy
--------------------------------

1. Run below command to package the jar. Make sure you run below command in folder where pom file resides.
mvn clean package -s settings.xml

2. If previous command runs successfully it should give you a target folder containing jar file

3. Copy pom file and paste it in target folder

4. Copy settings file and paste it in target folder

5. Switch to target folder

6. Run below command. Compare jar file name given in below command. Also provide below values:
	- App Public Url
	- Business Group Id
	- Anypoint platform environment name
	- Connected app credentials.
	
mvn -X -U --batch-mode -s settings.xml -Dmule.version=4.4.0 -Danypoint.applicationName=jenkins-test-openshift -Dartifact=jenkins-test-openshift-1.0.0-SNAPSHOT-mule-application.jar -Dapp.public.url=http://jenkins-test-openshift.apps.aws-rtf.4yio.p1.openshiftapps.com -Danypoint.mule.environment=dev -Dbusiness.group.id=*********************** -Danypoint.connectedAppClientId=****************************** -Danypoint.connectedAppClientSecret=************************ -Danypoint.mule.environment=dev mule:deploy

7. Below is the error that it throws:
'''''''''''''''''''''''''''''''''''''''''''''''
[DEBUG] HTTP Request
GET https://anypoint.mulesoft.com/hybrid/api/v2/organizations/************************************/environments/************************************/deployments
Accept: application/json
User-Agent: mule-deployer/3.8.2
Authorization: bearer c7e0cf78-bfc2-49d8-8168-1479238db106
x-anypoint-session-extend: true
X-ANYPNT-ENV-ID: ************************************
X-ANYPNT-ORG-ID: ************************************


[DEBUG] HTTP response
403 Forbidden
Strict-Transport-Security: max-age=31536000; includeSubDomains
Server: nginx
Connection: keep-alive
Content-Length: 196
Date: Thu, 02 Mar 2023 12:38:14 GMT
x-anypnt-trx-id: a17e2
Content-Type: application/json
''''''''''''''''''''''''''''''''''''''''''''''''