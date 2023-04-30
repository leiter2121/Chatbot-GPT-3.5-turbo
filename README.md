Kendra is an AI chatbot that can generate a text response and even an image using OpenAI's GPT-3 and DALL·E models. The chatbot also uses Amazon Polly to convert the text response to speech.

## Dependencies

Kendra requires the following dependencies to be installed:

- `openai`: Python library for accessing the OpenAI API
- `boto3`: Python library for accessing the Amazon Web Services (AWS) API
- `pygame`: Python library for audio playback
- `requests`: Python library for making HTTP requests
- `pickle`: Python library for object serialization

You can install these dependencies using `pip`:

```bash
pip install openai boto3 pygame requests pickle
```

## Setup

To use Kendra, you need to set up your OpenAI API key and your Amazon Polly credentials. You can do this by editing the following lines in the `KendraGenIIIbot.py` file:

```python
openai.api_key = "YOUR OPENAI API KEY"

polly = boto3.client(
    "polly",
    region_name="YOUR AWS REGION",
    aws_access_key_id="YOUR AWS ID KEY",
    aws_secret_access_key="YOUR AWS SECRET KEY HERE"
)
```
Replace `YOUR OPENAI API KEY` with your OpenAI API key, and replace `YOUR AWS REGION`, `YOUR AWS ID KEY`, and `YOUR AWS SECRET KEY HERE` with your AWS credentials.

# You can change the voice in Amazon Polly by changing the voice model variable from "Joey" to another model. Check AWS details.
```python
def speak_text(text):
    response = polly.synthesize_speech(
        Text=text,
        OutputFormat="mp3",
        VoiceId="Joey",
        Engine="neural"
    )
```    


## Usage

To use Kendra, simply run the `KendraGenIIIbot.py` file using Python:

```bash
python KendraGenIIIbot.py
```

The chatbot will prompt you to enter a message. Type your message and press Enter to send it to Kendra. Kendra will then generate a text response or an image, depending on your input.

You can exit Kendra by typing "quit" into the chat. Kendra will save the conversation history to a pickle file before exiting.

## How it Works

Kendra works by using the OpenAI GPT-3.5 Turbo model to generate a text response to a user's message. The chatbot keeps a history of the conversation, and uses this history as context for the GPT-3 model.

If the user's message contains the word "image", Kendra will ask the user to describe the image they want to see. Kendra will then use the user's description as the prompt to generate an image with the DALL·E model. The generated image will be saved to the user's desktop.

If the user's message does not contain the word "image", Kendra will generate a text response using the GPT-3 model.

Kendra also uses Amazon Polly to convert the text response to speech, which is played back to the user using the Pygame library.

Kendra stores the conversation history in a pickle file, which is loaded and saved each time the chatbot is run. This allows Kendra to remember the conversation history across multiple sessions.

## Limitations

Kendra has some limitations:

- Kendra can only generate images with the DALL·E model if the user provides a good description of the image they want to see. If the description is too vague or ambiguous, the generated image may not be what the user had in mind.
- Kendra may generate inappropriate or offensive responses, as the GPT-3 model has been trained on a large corpus of text that includes some offensive content.
