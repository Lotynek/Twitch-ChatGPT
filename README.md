

### 1. Deploy to Render

[![Deploy to Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy)



---

## 2. Set your environment variables
Go to the variables/environment tab in your deployment. 

Create 3 new variables. The exact spelling of these variables is important:

### 3.1 Required Variables for both Render and Cyclic

1. _**OPENAI_API_KEY**_
  - This is where you paste your openAI Secure Key.

### 3.2 Required Variables only for Render

2. _**CHANNELS**_
  - This is where you put your twitch channel name.
  - If you have more than one channel, separate them with a comma. (e.g. channel1,channel2,channel3)
  - If the channel has FOLLOWERS-ONLY mode enabled: 


### 3.2. Optional Variables for both Render and Cyclic

3. _**GPT_MODE**_
  - (default: CHAT)
  - Accepts one of 2 values:
    - "CHAT" - Chat mode with history, cheaper than prompt mode but also faster. Uses gpt-3.5-turbo as model.
    - "PROMPT" - Prompt mode, no history. Uses text-davinci-003 as model.

4. _**HISTORY_LENGTH**_
  - (default: 3)
  - Accepts a number.
  - Only works when GPT_MODE is CHAT
  - Defines how many bot-user conversations will be saved and sent together with the most recent user message.
  - This gives ChatGPT the ability to remember things and allow conversations instead of static prompts.

5. _**MODEL_NAME**_
  - (default: gpt-3.5-turbo)
  - Accepts one of 2 values:
    - "gpt-3.5-turbo" - The default model. This is the fastest and cheapest model. It is also the least accurate.
    - "text-davinci-003" - Most expensive model.
    - "gpt-4" - Most accurate model and if you have the plan for it!

6.3. Optional Variables only for Render

6. _**COMMAND_NAME**_
  - (default: chat)
  - You can add an exclamation mark (!) before the command name to make look like a twitch command.
  - Accepts a string.
  - Defines the command that will be used to trigger the bot.

7. _**TWITCH_USER**_
This step can be complicated.
  - To get the necessary twitch user:
    - Go to https://dev.twitch.tv/console
    - Register your application
    - Fill a name for your application (this can be anything)
    - Set OAuth Redirect URL to https://twitchapps.com/tokengen/
    - Set Category to Chat Bot
    - Set Description to anything you want
  - Fill the TWITCH_USER variable with the name of your application

8. _**TWITCH_AUTH**_
  - Go to https://twitchapps.com/tmi/ and click on Connect with Twitch
  - Copy the token from the page and paste it in the TWITCH_AUTH variable  
  - ⚠️ THIS TOKEN MIGHT EXPIRE AFTER A FEW DAYS, SO YOU MIGHT HAVE TO REPEAT THIS STEP EVERY FEW DAYS ⚠️

9. _**ENABLE_TTS**_
  - (default: false)
  - Accepts a boolean.
  - If set to true, the bot will use the text-to-speech feature.

Save the Changes.

## 4. Text-To-Speech (TTS) Connection

Your render url, for example:
- https://your-twitch-bot.onrender.com/

You will see the following web page, and it is directly connected to your twitch chat.

You can add it to your stream as a widget :)

![img.png](imgs/img.png)


---

## 5. Add your API Command to your Chatbot
Now it is time to build your Chat-Command. 


### Streamelements
Go to your Streamelements Dashboard -> Chatbot -> Commands -> Custom Commands.

Create a new command.

Enter the following in the response field:
```
$(urlfetch https://your-cyclic-url.app/gpt/"${user}:${queryescape ${1:}}")
```



### Nightbot

Enter the following in the message field:

```bash
$(eval "$(urlfetch https://your-cyclic-url.app/gpt/"$(user):$(querystring)")"; ' ')
```


## Extra commands

### !continue
Twitch has a 400 character limit on chat messages. 
If you want to continue a conversation, you can use the !continue command.

$(urlfetch https://your-cyclic-url.app/continue")
