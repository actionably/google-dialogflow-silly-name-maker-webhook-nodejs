# Actions on Google: Silly Name Maker Sample using Node.js and Cloud Functions for Firebase including Dashbot integration

This is a super simple Assistant app, built using Dialogflow and Node.js, to
generate a silly name based on your lucky number and favorite color.

## Setup Instructions

### Steps
1. Create an account on [https://www.dashbot.io](https://www.dashbot.io)
1. Create a google bot on dashbot.io (make note of the API_KEY)
1. Substitute the API_KEY created above for REPLACE_WITH_YOUR_DASHBOT_API_KEY in functions/index.js 
1. Use the [Actions on Google Console](https://console.actions.google.com) to add a new project with a name of your choosing.
1. Under *Build a custom app*, click *BUILD* in the Dialogflow box and then click *Create Actions on Dialogflow*.
1. Click *Save* to save the project.
1. Click on the gear icon to see the project settings.
1. Select *Export and Import*.
1. Select *Restore from zip*. Follow the directions to restore from the `SillyNameMaker.zip` in this repo.
1. Deploy the fulfillment webhook provided in the functions folder using [Google Cloud Functions for Firebase](https://firebase.google.com/docs/functions/):
   1. Follow the instructions to [set up and initialize Firebase SDK for Cloud Functions](https://firebase.google.com/docs/functions/get-started#set_up_and_initialize_functions_sdk). Make sure to select the project that you have previously generated in the Actions on Google Console and to reply `N` when asked to overwrite existing files by the Firebase CLI.
   1. Run `firebase deploy --only functions` and take note of the endpoint where the fulfillment webhook has been published. It should look like `Function URL (sillyNameMaker): https://${REGION}-${PROJECT}.cloudfunctions.net/sillyNameMaker`
1. Go back to the Dialogflow console and select *Fulfillment* from the left navigation menu. Enable *Webhook*, set the value of *URL* to the `Function URL` from the previous step, then click *Save*.
1. In the `make_name` intent, check *End Conversation* for the section *Actions on Google*, then Save.
1. Open Dialogflow's *Integrations* page, open the *Settings* menu for *Actions on Google*, authorize by clicking *Authorize*, then click *Test*.
1. Click *View* to open the Actions on Google simulator.
1. Type `Talk to my test app` in the simulator, or say `OK Google, talk to my test app` to any Actions on Google enabled device signed into your developer account.

**Note: To use dashbot on firebase when you must have entered a credit card for Google Cloud and linked this firebase project to this billing account.**

For more detailed on dashbot, see the [dashbot documentation](https://www.dashbot.io/docs).

For more detailed information on deployment, see the [documentation](https://developers.google.com/actions/dialogflow/deploy-fulfillment).

### Testing locally

1. Install [ngrok](https://ngrok.com/)
1. Run ngrok ```ngrok http 5000``` 
1. Go back to the Dialogflow console and select *Fulfillment* from the left navigation menu. Enable *Webhook*, set the value of *URL* to the ngrok url from the previous step, then click *Save*.
1. ```cd functions```
1. ```npm install```
1. ```npm start```

## References and How to report bugs
* Actions on Google documentation: [https://developers.google.com/actions/](https://developers.google.com/actions/).
* If you find any issues, please open a bug here on GitHub.
* Questions are answered on [StackOverflow](https://stackoverflow.com/questions/tagged/actions-on-google).

## How to make contributions?
Please read and follow the steps in the CONTRIBUTING.md.

## License
See LICENSE.md.

## Terms
Your use of this sample is subject to, and by using or downloading the sample files you agree to comply with, the [Google APIs Terms of Service](https://developers.google.com/terms/).

## Google+
Actions on Google Developers Community on Google+ [https://g.co/actionsdev](https://g.co/actionsdev).
