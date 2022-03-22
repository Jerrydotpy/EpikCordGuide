---
description: Learn how to create Slash Commands on your Discord Bot using the Epikcord.py library!
authors: Epikcord.py
---

# Slash Commands

This page will show you how to use Slash Commands with EpikCord.py. 

!!! important
	To create commands in a guild, your app must be authorized with the `applications.commands` scope. In order to make commands work within a guild, the guild must authorize your application with the `applications.commands` scope. The `bot` scope is not enough.


!!! tdlr "Supported Option Types"
	
	| Name     | Value              | Note                           |
	|:---------|:-------------------|:-------------------------------|
	|INTEGER   |`int`| Any integer between -2^53 and 2^53|
	|BOOLEAN   |`bool`|     |	
	|USER	   | `discord.Member` |    |	
	|CHANNEL | `discord.abc.GuildChannel`|	Includes all channel types + categories|
	|ROLE|	`discord.Role`| |	
	|MENTIONABLE|	`discord.abc.Mentionable`|	Includes users and roles|
	|NUMBER| `float`|	Any double between -2^53 and 2^53 |

## Creating a slash command

```py
import asyncio
import datetime
import time
from EpikCord import Client, Intents, StringOption, NumberOption

intents = Intents().guilds.guild_members.guild_messages.direct_messages.message_content

client: Client = Client("token", intents)
  
@client.event
async def ready():
    print("Ready!")

@client.command(
    name = "ping",
    description = "A test command",
    guild_ids = [
        "937364424208039957"
    ]
)
async def ping(interaction):
    start = time.perf_counter()
    await interaction.reply(content = f"Pong!")
    end = time.perf_counter()
    
    asyncio.sleep(0.5)
    
    trip = end - start
    rt_ping = f'{(trip * 1000):.2f}ms ({humanize.precisedelta(datetime.timedelta(seconds=trip))})'
    
    await interaction.edit_original_message(content = f"Pong! {rt_ping}")
    
client.login()
```
