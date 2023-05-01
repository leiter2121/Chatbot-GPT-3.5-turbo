

# Kendra chatbot powered by GPT-3.5-Turbo

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

## Running the code

After you have updated the API keys and credentials, you can run the code using your preferred method, such as running it in a Python IDE or running it from the command line with `python your_code_file.py`.

## Usage

To use this program, run the `KendraGenVIbot.py` script in a Python environment that has the required packages and credentials set up. The program will prompt you for input and respond with conversational AI messages. You can exit the program by typing "quit" in the prompt.

### Search

If you type "search" followed by a query, the program will use the Bing Search API to search the web for the query and return the top five search results.

### Image Generation

If you type "generate image", the program will ask you to describe the image you want to see. You can then describe the image in natural language and the program will use DALL·E to generate an image based on your description. The program will save the generated image to your desktop.

## Acknowledgments

This program was created by adapting the OpenAI GPT-3 and integrating it with the Bing Search API, DALL·E, and Amazon Polly.
