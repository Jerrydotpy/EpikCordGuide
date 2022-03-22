---
description: Learn how to create slash commands with EpikCord.py!
authors: Epikcord.py
---

# Buttons

## Creating a simple button

!!! warning
    Currently we can only support one callback on all buttons

```py
from EpikCord import Client, Intents

intents = Intents().guilds.guild_members.guild_messages.direct_messages.message_content

client: Client = Client("token", intents)
  
@client.event
async def ready():
    print("Ready!")


@client.event
async def message_create(message):
    if message.author.id == client.user.id:
        return
    if message.content == "button":
        message.channel = Messageable(client, message.channel_id)

        actionrow = ActionRow().add_components(MessageSelectMenu(custom_id="select_menu")
        actionrow.add_options(MessageSelectMenuOption("label", "value")))

        await message.channel.send(content = "Anything", components=[actionrow])

@client.event
async def interaction_create(interaction): # Events can be `on_FOO_BAR`
    if interaction.is_message_component():
        await interaction.reply(content = "Anything")
```
