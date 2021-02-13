# Slack-Bot

It is a slack bot made with python and slack API for automation.

## Setup

```python
    pip install slackclient
    pip install python-dotenv

```

## Basic Usage of the Web Client

Slack provide a Web API that gives you the ability to build applications that interact with Slack in a variety of ways. This Development Kit is a module based wrapper that makes interaction with that API easier. We have a basic example here with some of the more common uses but a full list of the available methods are available here. More detailed examples can be found in our Basic Usage guide.

### Sending a message to Slack

One of the most common use-cases is sending a message to Slack. If you want to send a message as your app, or as a user, this method can do both. In our examples, we specify the channel name, however it is recommended to use the channel_id where possible. Also, if your app's bot user is not in a channel yet, invite the bot user before running the code snippet (or add chat:write.public to Bot Token Scopes for posting in any public channels).

```python
import os
from slack import WebClient
from slack.errors import SlackApiError

client = WebClient(token=os.environ['SLACK_API_TOKEN'])

try:
    response = client.chat_postMessage(
        channel='#random',
        text="Hello world!")
    assert response["message"]["text"] == "Hello world!"
except SlackApiError as e:
    # You will get a SlackApiError if "ok" is False
    assert e.response["ok"] is False
    assert e.response["error"]  # str like 'invalid_auth', 'channel_not_found'
    print(f"Got an error: {e.response['error']}")
```

- Here we also ensure that the response back from Slack is a successful one and that the message is the one we sent by using the assert statement.

### Interesting things to try

Make some changes in the code and observe the output.

## Built by (A-Z)

- [Bhimraj Yadav](https://www.facebook.com/bhimrazy)

## License

MIT © bhimrazy
