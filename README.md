# Configure Google Drive OAuth and Save Access Token
In this article I am going to help you setup an oauth key in google drive and use a simple technique  to save the access token. So, this will enable us not to verify access everytime we make an api call. 
## Now follow the below steps to create OAuth key, 
- First go to [Google's developer Console](https://console.developers.google.com/projectselector2/apis/dashboard?authuser=1&supportedpurview=project).
- You should see "Select A Project" on top left corner just right of the "Google API" logo. If you already have a project you will see the selected project name. Click it and it will open a popup window that will assist you to create a new project.
- After you have created the project, add Google drive api from select api screen
- Now that you have selected you are api you need to configure OAuth2.0 key. So, head over to "Credentials" by selecting from the left panel and create a new OAuth key. You should see the option on the top panel.
- On the configuration page give any name you like to client name, however you should use the gmail id you want to use for testing in the "Test User" section.
- Also, Make sure you have put `http://localhost:8080` in the "Authorized Javascript Origin" and `http://localhost:8080/` in "Authorized Redirect URI" otherwise the key will not work. 
- Save the oAuth2.0 key
- After you have saved it you should see your OAuth key in the "Credential" page with your given client name
- From there download the key. You will see a download icon just right of the key.

## Getting Access Token
- After you have downloaded the OAuth2.0 key it should be downloaded as something like `client_secret_*VERYLONGTEXT*.json`. So, rename it as `client_secrets.json`
- Now download this [file](https://github.com/tonmoy50/setup-pydrive-cred/blob/main/src/makecred.py) or just download this repo entirely.
- In your downloaded directory copy the `client_secrets.json` file
- Now, we need the pydrive package before we can create access token. So, first make sure you have python 3.7 or up and then open your terminal and run `pip install pydrive`
- Next, run the `makecred.py` file. It should open a browser and will ask for your permission to give access to your api. Just make sure you are using the same gmail address that you have setup for test user in OAuth consent screen. Afterwards, it should create a file name `mycreds.txt` in the same directory.

So, we have successfully created access token and everytime we call our drive api we won't need to authorize access.
