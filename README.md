# Introduction

Chat21-cloud function is the backend module required for the operation of the other chat21 modules.

* Send a direct message
* Send a group message
* Create a conversation for each message
* Send the push notification for direct and group message
* Send an info message to notify the creation of a group or a member joining

# Pre requisites

* NPM installed. More info here https://nodejs.org/en/
* Create a Firebase Project on https://console.firebase.google.com/. Follow the Firebase Documentation to create a new project on the Firebase console.
* Install Firebase CLI running ```npm install -g firebase-tools```. 
More info here https://firebase.google.com/docs/cli/ 
If the command fails, you may need to change npm permissions as described here https://docs.npmjs.com/getting-started/fixing-npm-permissions or try to install Firebase CLI locally with ```npm install firebase-tools```

You can find more info about Firebase Functions here https://firebase.google.com/docs/functions/get-started

# Project setup
* Clone or download this repo from github 
* Run from command line:
```
cd functions 
npm install
```
* Login to Firebase CLI with ```firebase login```. More info here  https://firebase.google.com/docs/cli/
* Set up your Firebase project by running ```firebase use --add```, select your Project ID and follow the instructions.

## Setup Options
Use with Google Cloud environment to configure the platform.
* Enable Support features with: ```firebase functions:config:set support.enabled=true```

* Enable email notification with: ```firebase functions:config:set email.enabled=true```
    Set STMP URI endpoint with : ```firebase functions:config:set email.endpoint=smtp://<Username>:<password>@smtp.mailgun.org``` (Unset with ```firebase functions:config:unset email.endpoint```)
    Set Gmail account with  : ```firebase functions:config:set email.gmail.user=frontiere21@gmail.com``` and ```firebase functions:config:set email.gmail.password=ft21gmail``` More info here https://community.nodemailer.com/using-gmail/ and here https://medium.com/@manojsinghnegi/sending-an-email-using-nodemailer-gmail-7cfa0712a799

* Disable the option "Automatically join the General Group on signup" with ```firebase functions:config:set group.general.autojoin=false```


# Test locally

This project comes with a web-based UI for testing the function. To test locally do:

* Start serving your project locally using ```firebase serve --only hosting,functions```
* Open the app in a browser at https://localhost:5000.
* Sign in to the web app in the browser using Google Sign-In
* Create messages and explore them using the List and Detail sections.
* Sign out. You should no longer be able to access the API.

# Deploy
* Deploy to Firebase using the following command: ```firebase deploy```. You can see the deployed functions on the Firebase Console under Functions menu.
* Open the app using firebase open hosting:site, this will open a browser.


[Read the REST API page](docs/api.md)



# BOT Setup
* Create a bot user with the mobile app or web app. Ex: email:bot@chat21.org, firstname: Bot, lastname: Chat21,etc.
* Retrieve the bot user id (<BOT_UID>) from the profile tab of the mobile app or from firebase autentication tab
* Set the bot user id <BOT_UID> parameter with ```firebase functions:config:set bot.uid=<BOT_UID>```

# FB Messenger
* Create an FB APP 
* Enable FB webhook with ```firebase functions:config:set webhook.enabled=true```
* Set FB secret with ```firebase functions:config:set webhook.secret=EAANskcQny4cBAIpgGUvuHNoHCpgIcyTTJpzZBZCjlZAxaMtTnJcfEBQZBniOUnNr92ThWbTOtMEZCfAazxaFhVnq1WpLmZBUhnTfJUlmO4xF37telaUZCpCECqaObMeyumZB4UGP0BZChSER9ce3uVA8HBMIJTAHa097V3bnNcLACB7qVTCySNg3c```