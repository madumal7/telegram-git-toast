## Telegram Git Toast

This is a telegram bot created using expressJs. This repo has two branches which are master and, single-secret. Master branch is set to have multiple secrets per single chat while the single-secret branch bot only have one secret for all the chats. To have multiple secrets per chat, we need to store the secrets somewhere like firestore. I have used firestore in the master branch. However, if you are having only a single secret and you don't worry much about the security or you use this bot only for your personal projects the single-secret would be okay for you. Currently I have setup this project to deploy on to a firebase function.

**Credits:** Telegraf

## Getting Started

1.  Clone the repo
    ```
    git clone https://github.com/madumal7/binance-telegram-bot.git
    ```
2.  Install NPM packages, Go to functions folder and enter
    ```
    npm install
    ```
3.  Create a telegram bot using BotFather. Read the documentation [here](https://core.telegram.org/bots/api).
4.  Add following variables as your firebase environment variables. You may only need the "secret", if you are using the single secret bot. You can add a random string as you wish.

    ```
    {
        "crypto": {
            "token": <YOUR_TELEGRAM_BOT_TOKEN>,
            "projectid": <YOUR_FIREBASE_PROJECT_ID>,
            "region": <YOUR_FIREBASE_PROJECT_REGION>,
            "secret": <YOUR_SECRET_FOR_GIT_REQUEST_VALIDATION>
        }
    }
    ```

5.  Run `npm run deploy` to build and deploy the function to firebase
    Once you deploy the bot to your firebase function, the webhook will be set to your bot.
    Remember to check the firebase deployement doc. You may need to set up the .firebasesrc file in the root directory. This fill will include the details of your firebase project.

## Usage

To allow the bot to send git notifications, you need to do two things.
1. Add the bot to your telegram project group and type "/start" without double quotes. And bot will reply you with a message which includes a link.
2. Then add this link as your github webhook in the github repo or organization settings. Remember to add the secret. If you set it up as single-secret bot, it will be that particular secret you used. However, if it is the bot in master branch, a new secret will be included in the same message which the bot sent you.

If you use master branch, costs for the firestore resources will be added for your monthly bill.

## Motivation

I normally use telegram all the time for my works and I usually collaborate with my project teams using telegram.
Those times, this git toast bot helps me to know the git pushes instantly.
