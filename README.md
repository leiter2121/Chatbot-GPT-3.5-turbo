

# Kendra is a chatbot powered by GPT-3.5-Turbo, Microsoft Bing Search, Amazon Polly, and OpenAI DALL·E .

This is a Python program that demonstrates how to use the OpenAI API to generate conversational AI responses, search the web using Bing Search API, and generate images using DALL·E. The program also uses Amazon Polly to generate spoken text from the conversational responses.

## Prerequisites

To run this program, you need to have the following:
- Python 3.8 (minimum) https://www.python.org/downloads/release/python-380/
- An OpenAI API key
- A Bing Search API key
- An endpoint for the Bing Search API
- Amazon AWS credentials with access to the Amazon Polly service

You also need to have the following Python packages installed:

- `openai`
- `boto3`
- `pygame`
- `requests`

You can install these packages using `pip`:

```
pip install openai boto3 pygame requests
```

## Setting up APIs, and Reigions

## OpenAI API

1. Go to the [OpenAI API](https://beta.openai.com/signup/) and sign up for an account.
2. Once you have an account, go to your [dashboard](https://beta.openai.com/dashboard/) and create an API key.
3. Copy the API key and replace `YOUR_OPENAI_API_KEY` in the code with your API key.

## Bing Search API

1. Go to the [Bing Search API documentation](https://docs.microsoft.com/en-us/bing/search-apis/bing-web-search/create-bing-search-service-resource) and follow the instructions to create a Bing Search resource.
2. Once you have a resource, go to the [Azure portal](https://portal.azure.com/) and navigate to your resource's dashboard.
3. Copy the subscription key and replace `YOUR_BING_SEARCH_API_KEY` in the code with your subscription key.
4. Also, replace `BING SEARCH ENDPOINT` with the endpoint of your Bing Search resource.

## Amazon Polly

1. Go to the [Amazon Web Services (AWS) console](https://console.aws.amazon.com/console/home) and sign up for an account if you don't already have one.
2. Once you're signed in, navigate to the [IAM dashboard](https://console.aws.amazon.com/iam/home#/home) and create a new user with programmatic access.
3. Copy the user's access key ID and secret access key, and replace `YOUR_AWS_ID_API_KEY` and `YOUR_AWS_SECRET_KEY` in the code with these values.
4. Also, replace `YOUR_REGION_NAME` with the region where you created the user.

## Usage

To use this program, run the `KendraGenVIbot.py` script in a Python environment that has the required packages and credentials set up. The program will prompt you for input and respond with conversational AI messages. You can exit the program by typing "quit" in the prompt. 

## (THE BOT WILL NOT SAVE THE CONVERSATION HISTORY UNLESS YOU QUIT THE BOT PROPERLY.)

## Adjusting the Settings in generate_chat_response function:

The `generate_chat_response` function is responsible for generating the chat response. This function takes in the `conversation` parameter, which contains a list of messages between the user and the bot. Here's how you can adjust the settings in this part of the code:

1. Truncate or Omit Conversation History: You can adjust the conversation history by changing the number of messages that the function will keep in memory. By default, it keeps the last 15 messages. If you want to increase or decrease this number, you can change the value in the following line of code:

```
conversation = conversation[-15:]
```

2. Limit Conversation Tokens: The `conversation_tokens` variable is used to count the number of tokens in the conversation. If this number exceeds 4096 tokens, the function will only keep the last message. If you want to adjust this value, you can change the number 4096 in the following line of code:

```
if conversation_tokens > 4096:
    conversation = conversation[-1:]
```

3. Max Tokens: The `max_tokens` parameter limits the total number of tokens in the generated response. By default, this value is set to 1000 tokens. If you want to adjust this value, you can change the number in the following line of code:

```
max_tokens=1000
```


### Search

If you type "search" followed by a query, the program will use the Bing Search API to search the web for the query and return the top five search results.

To adjust the number of searches in the `search_bing` function, you can modify the value of the `count` parameter in the `params` dictionary. The `count` parameter specifies the number of search results to retrieve from the Bing search API. By default, the value is set to 5, but you can change it to any positive integer value to retrieve more or fewer search results.

Here's an example of how to modify the `count` parameter to retrieve 10 search results:

```
params = {
    'q': query,
    'count': 10,  # Retrieve 10 search results
    'offset': 0,
    'mkt': 'en-US'
}
```

(Note that the maximum value of `count` is 50, as per the Bing search API documentation.)

### Image Generation

If you type "generate image", the program will ask you to describe the image you want to see. You can then describe the image in natural language and the program will use DALL·E to generate an image based on your description. The program will save the generated image to your desktop.


## How to change the voice in Amazon Polly

To change the voice used by the `speak_text` function in the Python code that uses Amazon Polly. By default, the voice used is "Joey". Follow the steps below to change the voice to a different one.

1. Determine the name of the voice you want to use. You can find a list of all the available voices at [this page](https://docs.aws.amazon.com/polly/latest/dg/voicelist.html). Note down the name of the voice you want to use.

2. In your code, find the `speak_text` function, which should look like this:

   ```
   def speak_text(text):
        response = polly.synthesize_speech(
            Text=text,
            OutputFormat="mp3",
            VoiceId="Joey",
            Engine="neural"
        )
   ```

   The `VoiceId` parameter specifies the voice to use. By default, it is set to "Joey". To change the voice, update the `VoiceId` parameter with the name of the voice you want to use.

   For example, to use the "Emma" voice, the `speak_text` function should look like this:

   ```
   def speak_text(text):
        response = polly.synthesize_speech(
            Text=text,
            OutputFormat="mp3",
            VoiceId="Emma",
            Engine="neural"
        )
   ```

3. Save your changes and run your code. The `speak_text` function will now use the new voice you specified.

   **Note:** that not all voices are available in all regions. If you get an error when trying to use a voice, you may need to switch to a different region that supports that voice. You can find a list of the available regions for Amazon Polly at [this page](https://docs.aws.amazon.com/general/latest/gr/rande.html#polly_region).
   
   **Note:** Not all Amazon Polly voices support the neural TTS engine. If you want to use the neural TTS engine, make sure to choose a voice that supports it. You can check the documentation to see which voices support the neural TTS engine. If you choose a voice that doesn't support the neural TTS engine, you can still use the standard TTS engine by removing the `Engine` parameter from the `synthesize_speech` function call or setting it to `"standard"`, or remove the `"Engine"` line from the code altogether.

## Use Cases

This script can be used as a starting point for building a conversational AI chatbot or an interactive agent that responds to user input in a natural language. Some possible use cases for the script could be:

1. Customer support: The chatbot could be trained on a knowledge base and used to provide 24/7 customer support for a product or service.

2. Personal assistant: The chatbot could be integrated with a calendar or email system to help manage tasks, appointments, and reminders.

3. Education: The chatbot could be used to help students learn a new language or a complex topic by providing personalized feedback and guidance.

4. Entertainment: The chatbot could be designed to entertain users by telling jokes, playing games, or recommending movies or music.

5. Research: The chatbot could be used to help researchers or academics find relevant literature or data by searching through online databases.

6. Virtual tour guide: The chatbot could be used to provide users with a personalized tour of a city, museum, or historical site.

7. Mental health support: The chatbot could be designed to provide emotional support or counseling to users who may be experiencing anxiety or stress.

## Acknowledgments

This program was created by adapting the OpenAI GPT-3.5 Turbo LLM and integrating it with the Bing Search API, DALL·E, and Amazon Polly.
