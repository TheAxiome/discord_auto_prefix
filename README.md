# Package Info

[Create discord.js custom guild prefix without much work!](https://www.npmjs.com/package/discord_auto_prefix)

# Useful Links

- [Issues](https://github.com/TheAxiome/discord_auto_prefix/issues)
- Report any issues in my [discord](https://discord.gg/ZbKVPY5), go to the npm-issues channel! 

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

client.on('guildCreate', async guild => {
    prefix.defaultPrefix(guild, "!") //Sets the bots default prefix when it joins a new guild
})

client.on('message', async message => {
    const PREFIX = await prefix.fetchPrefix(message) //Fetch's the guilds prefix


    if (message.content === `${PREFIX}ping`) {
        message.channel.send(`PONG! My prefix  is ${PREFIX}`)
    }

    if (message.content.startsWith(`${PREFIX}setprefix`)) {
        const args = message.content.slice(10)

        prefix.setPrefix(message, args) //Sets the guilds prefix
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
//Change a guilds prefix
```

More values coming soon!
