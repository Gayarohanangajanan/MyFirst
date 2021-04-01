identity-conditional-auth-typingdna
Installing the connector & extensions
Download the resources/typing-dna folder

Copy the files inside plugins folder and paste them to IS_Home/repository/deployment/server/webapps/authenticationendpoint/plugins *copy the whole plugins folder if there is no plugins inside the authentication endpoint already

Add the typing-dna.js file to IS_Home/repository/deployment/server/webapps/authenticationendpoint/js

Alt text

Add the following line in IS_Home/repository/deployment/server/webapps/authenticationendpoint/basicauth.jsp
<jsp:directive.include file="plugins/basicauth-extensions.jsp"/>

Add the typingdna.json to IS_Home/repository/resources/identity/authntemplates. This is the adaptive authentication template going to be used.

Download the TypingDNA connector & add it to IS_Home/repository/components/dropins folder

Download the [TypingDNA API] and add it to IS_Home/repository/deployment/server/webapps folder

Go to IS_Home/repository/resources/conf/templates/repository/ conf/identity & open identity.xml.j2 and add the following line inside ResourceAccessControl tag.
<Resource context="(.*)/api/typingdna/v1.0/(.*)" secured="true" http-method="GET,DELETE"/>

Go to IS_Home/repository/resources/conf/ & open default.json and add the following path inside ‘tenant_context.rewrite.webapps’ to make the API path as tenant qualified.
"/api/typingdna/v1.0/"
Make sure you have added this before "/api/"

Create a TypingDNA account.
You can craete a TypingDNA account from here. Refer this for further information.

Configuring TypingDNA API settings.
Skip this part if you are using developer/free TypingDNA account.

Login to typingdna with your account and Configure the following.
Enable the Auto-Enroll & Enable Force Initial Enrollments & Update Settings.
Alt text

Configuring the Identity provider
Login to console

Go to Manage -> configurations -> other settings

Select/ Scroll down to TypingDNA Configuration

Enable TypingDNA & configure API Key, Secret. You can get the Key & Secret from TypingDNA dashboard. Refer this doc for further information.

Enable Advance TypingDNA-API mode if you have pro/enterprise typingDNA account - This advance mode will allow you to use TypingDNA’s advance APIs & configurations for the authentication.

Configure the region ( type eu or us )

Alt text

Configuring Service provider
Go to Develop -> Application & Select the sample application you configured
Go to sign-on method
Add Typing-Biometric-Based in templates->user
Refer this doc to get more information about TypingDNA adaptive template.
Alttext
