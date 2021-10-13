<img src="https://media.discordapp.net/attachments/897655744982319114/897676467071221790/Untitled_1.png">

# Overview

Welcome to SlashCord, the most easy to use python libary for discord.py slash commands.

# Install SlashCord

For linux and mac `pip3 install slashcord`, for windows `pip install slashcord`

# How to use SlashCord

All you have to do is use one function, `sync_all_commands`. This will sync all commands to discord and will start listening for interactions and respond to them. 
It is recommended to put this in an `on_ready` event. Here is an example:

```python
import discord
from discord.ext import commands
from slashcord.slash import *

intents = discord.Intents.default()

intents.members = True

client = commands.Bot(command_prefix="!", intents=intents)



@client.event
async def on_ready():
    await sync_all_commands(client)

@client.command()
async def say(ctx, message):
    await ctx.send(message)


client.run(token)
```

The `sync_all_commands` function takes these parameters:

`client`: Your bot object needed. This can be a `discord.ext.commands.Bot` or `discord.ext.commands.AutoShardedBot` object. `discord.Client` and `discord.AutoShardedClient` have not been tested, but might work. This parameter is required.

`case_sensitive`: Whether uppercase and lowercase letters matter when running a command. Setting this to `False` will make all arguments lowercase. This parameter is optional and defaults to `True`. 


`loading_message`: This message probably won't be seen by the user, but its needed due to how the library works. This can say anything. This parameter is optional and defaults to "Loading".

`send_hidden`: Whether to make messages hidden. Hidden messages can only be seen by the user that runs the command. This parameter is optional and defaults to `False`. 

`hidden_commands`: A list of command names to hide from the slash command list. After all commands are synced, all commands in this list are removed. This parameter is optional and defaults to `[]`

`choices`: A dictionary of choices for the commands given. All keys must be command names, and all values must be a list containing a dictionary with  `name` and `value` keys. An example is: `{"say" : [{"name" : "Greet", "value" : "Hi!"}]}`. This parameter is optional and defaults to `{}`.

`error_function`: A function that will be called if an exception is raised. The function must have two parameters: `context`, and `error`. The `context` will be a `SlashContext` object, and the `error` will be the exception that is raised. This will override the default error system which means exceptions won't be raised unless you manually raise them with `raise error`. This parameter is optional and defaults to `None`. 


# Credits 

Thank you for https://github.com/TricolorHen061 without him i couldnt make the main file of the project :D

Thank you for https://github.com/VincentRPS For Art and Styles :D

# Buttons coming soon!
