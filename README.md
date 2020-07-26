# Info

[Create discord.js custom guild prefix without much work!](https://www.npmjs.com/package/discord_auto_prefix)

[This is a list of npms I created, and will make next](https://github.com/TheAxiome/NPM-List/blob/masterREADME.md)

# Useful Links

- Git hub [Issues](https://github.com/TheAxiome/discord_auto_prefix/issues)
- Report any issues or feedback in my [discord](https://discord.gg/ZbKVPY5), go to the npm-issues channel! 
# Update Log

**Version 1.4.0**
- Fixed commands not working after the prefix was changed
- Updated every command
- Added *deletePrefix()* command, see the values/syntax section for how it works

**Version 1.3.0**
- Bug fixes
- Added new instances to call the client, and guild

# How to use

`npm i discord_auto_prefix`

```javaScript
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

client.on('guildDelete', async guild => {
    prefix.deletePrefix(guild) //Deletes the bots prefix data when leaving a guild
})

client.on('message', async message => {
    if (message.author.bot) return;
    if (message.channel.type === 'dm') return;

    const PREFIX = await prefix.fetchPrefix(message)

    if (!message.content.startsWith(PREFIX)) return; //If mesage isn't start with prefix then return
    const args = message.content.slice(PREFIX.length).split(" "); //Config Args(Arguements)
    const command = args.shift().toLowerCase();

    if (command === "ping") {
        message.channel.send(`PONG!`)
    }

    if (command === "setprefix") {
        if (!message.member.hasPermission("MANAGE_GUILD")) return;
        if (!args) return message.channel.send("No prefix was provided!")

        prefix.setPrefix(message, args)
    }

})

client.login('TOKEN')

//A better and easier to understand guide will be put here soon!
```

# Values/Syntax

**If you do not understand the syntax below, or have any values to replace it with, copy from the example I showed above*

```
defaultPrefix(guild, value)
```
```css
This sets the default prefix of a bot when it joins a new guild

Replace "value" with the prefix you want to set
Replace "guild" with the guild value
```

```
deletePrefix(guild)
```
```css
This deletes a guilds prefix data when the bot leaves it
This is an optional command, but I encourage you to use it, it helps improve performance

Replace "guild" with the guild value
```

```
fetchPrefix(message)
```
```css
This fetches the guilds prefix

Replace "message" with the message value
```

```
setPrefix(message, value)
```
```css
This changes a guilds prefix

Replace "message" with the message value
Replace "value" with the new prefix
```

```
setLogging()
//This command is in testing
```

More values coming soon!
