---
description: Learn how to create User commands on your Discord Bot using the Epikcord.py library!
authors: Epikcord.py 
---


# :fontawesome-brands-message-code: Message commands

Message commands are commands you can use a user. You right click the user and go to apps and use a message command on the user.
## Creating Message Commands

Similar to user commands, but is a global user command

```py
from EpikCord import Client, Intents

intents = Intents().guilds.guild_members.guild_messages.direct_messages.message_content

client: Client = Client("token", intents)
  
@client.event
async def ready():
    print("Ready!")
    
    
@client.message_command("test")
async def test(interaction):
    await interaction.reply(content = "Seems like a message to me.")

client.login()
```