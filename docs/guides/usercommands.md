---
description: Learn how create Context Menu Commands with Epikcord.py!
authors: Epikcord.py
---

# Context Menu Commands


## What are User Commands and Message Commands?

![gif](https://gblobscdn.gitbook.com/assets%2F-MjPk-Yu4sOq8KGrr_yG%2F-MjSXhYe9K0uVV4_oRsn%2F-MjSYM78m_x2LUvCexhn%2FqxVMvwcH.gif?alt=media&token=90f20216-6860-4234-abbd-1e237224dc65)

When you right click a message, you may see a option called "Apps". Hover over it and you can see commands a bot can run with that message. These are called message commands.

When you right click a message in the user list, you can once again see an option called "Apps". Hover over it and you can see commands a bot can run with that message. These are called user commands.

## Creating User Commands

```py
from EpikCord import Client, Intents

intents = Intents().guilds.guild_members.guild_messages.direct_messages.message_content

client: Client = Client("token", intents)
  
@client.event
async def ready():
    print("Ready!")
    
@client.user_command("mention")
async def mention(interaction):
    await interaction.reply(content = "Lol I'm not pinging them.")

client.login()
```
!!! tip
    If you want to make the command global, remove guild_ids. Note that global application commands can take up to an hour to register.

