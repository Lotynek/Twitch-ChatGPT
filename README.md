

###  Deploy to Render

[![Deploy to Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy)



---


  _**GPT_MODE**_
  - (default: CHAT)
  - Accepts one of 2 values:
    - "CHAT" - Chat mode with history, cheaper than prompt mode but also faster. Uses gpt-3.5-turbo as model.
    - "PROMPT" - Prompt mode, no history. Uses text-davinci-003 as model.

  _**HISTORY_LENGTH**_
  - (default: 3)
  - Accepts a number.
  - Only works when GPT_MODE is CHAT
  - Defines how many bot-user conversations will be saved and sent together with the most recent user message.
  - This gives ChatGPT the ability to remember things and allow conversations instead of static prompts.

  _**MODEL_NAME**_
  - (default: gpt-3.5-turbo)
  - Accepts one of 2 values:
    - "gpt-3.5-turbo" - The default model. This is the fastest and cheapest model. It is also the least accurate.
    - "text-davinci-003" - Most expensive model.
    - "gpt-4" - Most accurate model and if you have the plan for it!

