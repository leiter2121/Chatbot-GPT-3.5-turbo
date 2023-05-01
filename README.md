

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

## Usage

To use this program, run the `KendraGenVIbot.py` script in a Python environment that has the required packages and credentials set up. The program will prompt you for input and respond with conversational AI messages. You can exit the program by typing "quit" in the prompt.

### Search

If you type "search" followed by a query, the program will use the Bing Search API to search the web for the query and return the top five search results.

### Image Generation

If you type "generate image", the program will ask you to describe the image you want to see. You can then describe the image in natural language and the program will use DALL·E to generate an image based on your description. The program will save the generated image to your desktop.

## Acknowledgments

This program was created by adapting the OpenAI GPT-3 and integrating it with the Bing Search API, DALL·E, and Amazon Polly.
