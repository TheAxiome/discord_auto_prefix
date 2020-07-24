# Package Info

[Create discord.js custom guild prefix without much work!](https://www.npmjs.com/package/discord_auto_prefix)

# Useful Links

- [Issues](https://github.com/TheAxiome/discord_auto_prefix/issues)
- [Discord](https://discord.gg/ZbKVPY5) Contact me axiome#0441

# Update Log

**Version 1.3.0**
- Bug fixes
- Added new instances to call the client, and guild

# How to use

`npm i discord_auto_prefix`

```
const Discord = require('discord.js')
const client = new Discord.Client()

const { aPrefix } = require('discord_auto_prefix')
const prefix = new aPrefix()


client.on('ready', () => {
    console.log(`${client.user.tag} is now online!`)
})

client.on('message', async message => {
    prefix.defaultPrefix(message, "!") //Sets the bots default prefix for a guild

    const PREFIX = await prefix.fetchPrefix(message) //Fetch's the guilds prefix

    if (!message.content.startsWith(PREFIX)) return;

    if (message.content.startsWith('!setprefix')) {
        const NEW_PREFIX = message.content.slice(10)

        prefix.setPrefix(message, NEW_PREFIX) //Sets the guilds prefix
    }

})

client.login('TOKEN')

//A better and easier to understand guide will be put here soon!
```

# Values/Syntax

```
defaultPrefix() 
//Sets the bots default prefix for a guild
```

```
fetchPrefix()
//Fetch the guilds prefix
```

```
setPrefix()
//Set the guilds prefix
```

More values coming soon!
