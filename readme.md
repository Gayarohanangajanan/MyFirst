# identity-conditional-auth-typingdna

### Installing the connector & extensions

   1. Download the resources/typing-dna folder
        
   2. Copy the files inside plugins folder and paste them to IS_Home/repository/deployment/server/webapps/authenticationendpoint/plugins
      *copy the whole plugins folder if there is no plugins inside the authentication endpoint already
         
   3. Add the typing-dna.js file to IS_Home/repository/deployment/server/webapps/authenticationendpoint/js

 ![Alt text](images/screen-shot-1.png?raw=true)
   
   4. Add the following line in IS_Home/repository/deployment/server/webapps/authenticationendpoint/basicauth.jsp  
         ```<jsp:directive.include file="plugins/basicauth-extensions.jsp"/>```
    
   5. Add the typingdna.json to IS_Home/repository/resources/identity/authntemplates. This is the adaptive 
      authentication template going to be used.
     
   6. Download the TypingDNA connector & add it to IS_Home/repository/components/dropins folder

   7. Download the [TypingDNA API] and add it to IS_Home/repository/deployment/server/webapps folder  
    
   8. Go to IS_Home/repository/resources/conf/templates/repository/
      conf/identity & open identity.xml.j2 and add the following line inside ResourceAccessControl tag.    
          ```<Resource context="(.*)/api/typingdna/v1.0/(.*)" secured="true" http-method="GET,DELETE"/>```
      
   9. Go to IS_Home/repository/resources/conf/ & open default.json and
      add the following path inside ‘tenant_context.rewrite.webapps’ to make the API path as tenant qualified.  
          ```"/api/typingdna/v1.0/"```  
      Make sure you have added this before `"/api/"`
  
  
### Create a TypingDNA account.
You can craete a TypingDNA account from [here](https://www.typingdna.com/clients/signup). 
Refer this for further information.
  
  
### Configuring TypingDNA API settings.
Skip this part if you are using developer/free TypingDNA account.

   1. Login to typingdna with your account and Configure the following.   
   2. Enable the Auto-Enroll & Enable Force Initial Enrollments & Update Settings.  

 ![Alt text](images/screen-shot-2.png?raw=true)

### Configuring the Identity provider

  1. Login to console
  2. Go to Manage -> configurations -> other settings
  3. Select/ Scroll down to TypingDNA Configuration
  4. Enable TypingDNA & configure API Key, Secret. You can get the Key & Secret from TypingDNA 
     [dashboard](https://www.typingdna.com/clients/).
     Refer this doc for further information.
  5. Enable Advance TypingDNA-API mode if you have pro/enterprise typingDNA account - This advance mode will allow you 
     to use TypingDNA’s advance APIs & configurations for the authentication.

  6. Configure the region ( type eu or us )

 ![Alt text](images/screen-shot-3.png?raw=true)

### Configuring Service provider
  
  1. Go to Develop -> Application & Select the sample application you configured
  2. Go to sign-on method
  3. Add Typing-Biometric-Based in templates->user  
Refer this doc to get more information about TypingDNA adaptive template.
   
 ![Alt_text](images/screen-shot-4.png?raw=true)

