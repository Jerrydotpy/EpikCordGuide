---
description: Learn how to make a Discord bot using the EpikCord.py Library!
authors: Epikcord.py
---

# Creating your first bot
## Creating the bot
Just like how you needed to sign up to Discord to get started, we need to get your bot signed up too. To do this, 

1. Go to the [Discord Developer Portal](https://discord.com/developers/applications) and click on New Application.
2. Give your bot a name, and click Create
3. Now, you should see a page like this.
	![image](https://user-images.githubusercontent.com/96548672/159582454-46722fd9-b2c2-43fa-9d7c-dded512feb6b.png)
4. Click on Bot tab on the left side of the screen.
5. Add intents too
	![image](https://user-images.githubusercontent.com/96548672/159582651-aa9df25a-b7d0-4aa2-99ef-8e1cace21245.png)
6. You can give it a name, change the Avatar, etc.

### Inviting the bot
Now, lets get the bot added to some servers. Go to the OAuth2 tab in the left pane, and select `bot` and `applications.commands` as the scope.

The `applications.command`s scope allows the bot to use Slash Commands, which you may want to have.

Next, we choose what permissions the bot will have. You can select them. For now, lets give your bot the Administrator permission, meaning the bot will have all the permissions.
Once you select the permissions, click on copy to get the bot invite link.

![image](https://user-images.githubusercontent.com/96548672/159583072-ea75a1a1-e3e7-4b92-bedf-60131446d585.png)

You can use this link to invite the bot.

## Tokens
Now that we have an account for our bot, we need to login. In order to login, we need the bot's password.
All users and bots have a "token". You may think of a token as a unique password, since this is what we use to log into the bot and connect it to Discord.

Tokens are "snowflakes". Not actual snowflakes, though. Just like how no two snowflakes in real life have the same pattern, a snowflake in computers is a unique thing - no two bots have the same token - so a token is a snowflake. An ID is a snowflake.

Now, lets get our bot's token. To do this, 

1. Go back to the Bot tab. 
2. Click on the Copy button in the "Token" section.
	![image](https://user-images.githubusercontent.com/96548672/159583534-b4fa1336-9e35-4c10-a581-4141c0a71611.png)

Now, you have your bot's token copied to your clipboard.

!!! danger
	Never leak your bot's token, and never share it with anyone. Even if you get any DMs and someone tells you to do so, maybe claiming to be Discord Staff, do not do so. They are probably lying and are scamming you. Anyone with your token will be able to access your bot fully. They will be able to do anything they want with your bot. 

	Never push it to GitHub, or send it with the code. One way to prevent your token from getting leaked is to store it in `.env` files.

### Storing the token in an ENV file
Storing your bot Token in an ENV File will increase its security, and prevent it from getting leaked. 

1. Create a file with the name `.env`. Just `.env`, with the dot/period at the start.
2. Define the token in the file, like,
	```env
	TOKEN = [PASTE YOUR TOKEN HERE]
	```
	for example,
	```env
	TOKEN = yourtoken here
	```

!!! info
    We don't support bot prefix commands yet. But we are trying our best to implement this

## Coding the Basics

Here is a basic bot:

Install this before running the code
```py
pip3 install python-dotenv
```

```py
"""
Before you implement this in your bot, please note that its just for testing, 
If you have a test bot and are professional with your code, you can experiment 
with different features and report the bugs in an issue
"""


import os
from dotenv import load_dotenv
from EpikCord import Client


load_dotenv()

intents = Intents().guilds.guild_members.guild_messages.direct_messages.message_content # Intents().all if you want all

client: Client = Client(os.getenv("TOKEN"), intents)

@client.event
async def ready():
    print("Ready!")

client.login()
```

## Message events

You must have message intents for this:

```py
"""
Before you implement this in your bot, please note that its just for testing, 
If you have a test bot and are professional with your code, you can experiment 
with different features and report the bugs in an issue
"""


from EpikCord import Client,Intents,Messageable

intents = Intents().guilds.guild_members.guild_messages.direct_messages

client = Client("your_token", intents)

@client.event
async def message_create(message):
    if message.author.id == client.user.id:
        return
    if message.content == "example test":
        message.channel = Messageable(client, message.channel_id)

        await message.channel.send(content="hello, chat testing")

client.login()
```

## Embeds

```py
"""
Before you implement this in your bot, please note that its just for testing, 
If you have a test bot and are professional with your code, you can experiment 
with different features and report the bugs in an issue
"""


from EpikCord import Client,Intents,Messageable, Embed

intents = Intents().guilds.guild_members.guild_messages.direct_messages

client = Client("your_token", intents)

@client.event
async def message_create(message):
    if message.author.id == client.user.id:
        return
    if message.content == "embed":
        message.channel = Messageable(client, message.channel_id)

        embed = Embed(title="This is a embed", description="This a description")
        embed.add_field(name="This is a ", value="field")


        await message.channel.send(embeds=[embed])

client.login()
```

So you learned the basics of creating of the basic bot! Happy Coding
