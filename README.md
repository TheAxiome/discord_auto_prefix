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

prefix.defPrefix(client, "!") //Sets the bots default prefix

client.on('ready', () => {
    console.log(`${client.user.tag} is now online!`)
})

client.on('message', async message => {

    const PREFIX = await prefix.fetchPrefix(client, message) //Fetch's the guilds prefix
    const defprefix = await fetBotPrefix(client)

    if (PREFIX == null) {
        PREFIX = defprefix
    }
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
defPrefix() 
//Replace *VALUE HERE* with your bots default prefix, this will be the prefix if there is no guild prefix already!
```

```
fetchPrefix()
//Fetch the guilds prefix, if there is none the guild prefix will be the default prefix!
```

```
setPrefix()
//Set the guilds prefix
```

```
fetBotPrefix()
//Fetches the bots default prefix
```

More values coming soon!
