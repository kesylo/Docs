<h1 style="color:green">Service Activation (ProSaaS)</h1>

## Legend
- DAM = Media
- CMP = Content
- PCM = Product
- MRM = Project, FreeModelling
  
You can see client license and status at:
```
https://<tenant>.stylelabs.cloud/api/status/license
https://<tenant>.stylelabs.cloud/api/status
```

## Prerequisites
- In status, get client M version. based on that, you can follow licensing docs for 3.2 or 3.3
- Write down licences codes to be activated

## 1- Licensing

#### Steps
- Go to web app -> settings -> Oauth
  - Add Oauth client -> Client ID and pwd Generated here: https://www.guidgenerator.com/

- On Postman:
  - POST -> ```https://<tenant>.stylelabs.cloud/oauth/token```
    - Authorization -> Basic Auth -> Username and password from the client we just created
    - Body -> select: x-www-form... 
      - grant_type: **password**
      - username: **administrator**
      - password: From 1password 
      - get token
  - GET -> ```https://<tenant>.stylelabs.cloud/status/license```
    - Headers:
      - Authorization : ```Bearer <Token>```
      - Copy output for next step
  - PUT -> ```https://<tenant>.stylelabs.cloud/status/license```
    - Headers:
      - Authorization : ```Bearer <Token>```
      - Content-Type: **application/json**
    - Body -> select: raw
      - Paste previous output
      - Adjust modules section: 0 for **OFF** and 2147483647 for **On**

- Go to web app -> settings -> Users -> Users
  - Search for: **Superuser** and hit details on the right (The **i** icon)
  - Hit edit and add/remove corresponding modules

- Go to web app -> settings -> Users -> User groups
  - Search for: **Superuser** and hit details on the right (The **i** icon)
  - Hit edit and add/remove corresponding modules

## 2- Activate Vision API (MS vision)

#### Steps
- Go to web app -> settings -> Taxonomy -> Search: **Assettype**
  - On **Archive** hit details on the right (The **i** icon) 
  - then edit and activate **Triggers Vision**
- To validate vison API, upload asset, edit **overview**
  - On **type** hit add and select **archive**
  - After some time you should see details on the image