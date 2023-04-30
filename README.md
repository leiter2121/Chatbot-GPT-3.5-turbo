# Chatbot with DALL·E Image Generation

This repository contains a Python script for a chatbot that can generate responses using the OpenAI GPT-3.5 model and generate images using OpenAI's DALL·E. The chatbot also uses Amazon Polly to convert the bot's response to speech.

## Dependencies

- openai (version 3.0.0 or later)
- boto3
- pygame
- requests

You will also need to have an OpenAI API key and Amazon Polly credentials in order to use this script.

## Setup

1. Install the required dependencies by running `pip install -r requirements.txt`.
2. Set your OpenAI API key and Amazon Polly credentials in the script. Replace the placeholder values for `openai.api_key`, `region_name`, `aws_access_key_id`, and `aws_secret_access_key` with your own values.
3. Run the script using `python chatbot.py`.

## Usage

The chatbot will prompt the user to enter a message. The chatbot will respond to the user's message with a text response generated using the OpenAI GPT-3.5 model.

If the user's message contains the word "image", the chatbot will ask the user to describe the image they want to see. The chatbot will then generate an image based on the user's description using OpenAI's DALL·E. The generated image will be saved to the user's desktop.

To quit the chatbot, the user can enter the message "quit". The chatbot will save the conversation history to a pickle file before quitting.

## Additional Notes

- The `generate_chat_response` function limits the conversation history to the last 15 messages and the total token count of the conversation to 4096 tokens. You can adjust these values by changing the `conversation` and `max_tokens` parameters, respectively.
- The `generate_dalle_image` function generates an image with a default size of 1024x1024 pixels. You can adjust the size by changing the `size` parameter.
- The `speak_text` function converts text to speech using Amazon Polly and plays the speech using pygame. If you do not want to play the speech, you can comment out the `mixer.init()` and `mixer.music.play()` lines in the function.
