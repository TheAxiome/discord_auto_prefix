# Package Info

(Create discord.js custom guild prefix without much work!)[https://www.npmjs.com/package/discord_auto_prefix]

# How to use

`npm i discord_auto_prefix`

```
const Discord = require('discord.js)
const client = new Discord.Client()
const { aPrefix } = require('discord_auto_prefix)
const prefix = new aPrefix()
const DEFAULT_PREFIX = `!`; //It is important to have a defualt prefix variable

client.on('ready', () => {
    console.log(`${client.user.tag} is now online!`)
})

client.on('message', async message => {
    prefix.defPrefix(DEFAULT_PREFIX) //Sets the bots default prefix

    const PREFIX = aPrefix.fetchPrefix() //Fetch's the guilds prefix
    if (!message.content.startsWith(PREFIX)) return;

    if (message.content.startsWith('!setprefix')) {
        const NEW_PREFIX = message.content.slice(10)

        prefix.setPrefix(NEW_PREFIX) //Sets the guilds prefix
    }

})

client.login('TOKEN')
```

More values coming soon!
