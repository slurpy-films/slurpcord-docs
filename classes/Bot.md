# Slurpcord Docs > Classes > Bot


[Source Code](https://github.com/slurpy-films/slurpcord/tree/master/src/bot.js)

## The Bot class is the main class of slurpcord.

---

# Constructor
The `Bot` class constructor initializes a bot instance.

**Arguments:**
- `token` - The Discord bot token.
- `prefix` - The command prefix for the bot (optional, default is an empty string).

**Example:**
```javascript
import { Bot } from 'slurpcord';

const bot = new Bot("TOKEN", "?");
```

---

# Methods:

## command()
Creates a new command for the bot.

**Arguments:**
- `name` - The name of the command.
- `action` - The function to execute when the command is called. It will be called with two arguments. The [message](https://github.com/slurpy-films/slurpcord-docs/tree/master/structures/Message.md), and the input the user provides.

**Example:**
```javascript
bot.command("ping", (message, input) => {
    message.reply("Pong!");
});
```

---

## slashCommand()
Creates a new slash command handler for the bot. Slashcommands does not work with this as of now. Use event().

**Arguments:**
- `name` - The name of the slash command.
- `action` - The function to execute when the slash command is used.

**Example:**
```javascript
bot.slashCommand("hello", (interaction) => {
    interaction.reply("Hello, World!");
});
```

---

## event()
Registers an event listener for specific events in the bot. As of now the only events are: MessageCreate, InteractionCreate, MemberJoin, MemberLeave. More will be added in the future.

**Arguments:**
- `event` - The event to listen for. Use Events for this.
- `action` - The function to execute when the event is triggered.

**Example:**
```javascript
bot.event(Events.MessageCreate, (message) => {
    console.log(`New message: ${message.content}`);
});
```

---

## setCommands()
Sets the bot's slash commands using an array of commands.

**Arguments:**
- `commands` - An array of command objects. Recommended to use the class `SlashCommand` for this.

**Example:**
```javascript
const command1 = new SlashCommand()
    .setName("command1")
    .setDescription("This is command 1")

const command2 = new SlashCommand()
    .setName("command2")
    .setDescription("This is command 2")

bot.setCommands([command1, command2]);
```

---

## setPrefix()
Sets the command prefix for the bot.

**Arguments:**
- `prefix` - The new command prefix to set.

**Example:**
```javascript
bot.setPrefix("!");
```

---

## setActivity()
Sets the bot's activity status (playing, streaming, etc.).

**Arguments:**
- `name` - The activity's name (e.g., "Playing a game").
- `type` - The activity type (default is 0 for "Playing"). Recommended to use `ActivityTypes` for the type.

**Example:**
```javascript
bot.setActivity("Playing Slurpcord!", ActivityTypes.Playing);
```

---

## start()
Starts the bot by connecting to Discord's WebSocket gateway.

**Example:**
```javascript
bot.start();
```

---

## guilds.fetch()
Fetches guilds (servers) that the bot is a member of.

**Arguments:**
- `id` - The ID of the guild to fetch (optional). If omitted, all guilds will be fetched.

**Example:**
```javascript
bot.guilds.fetch();  // Fetches all guilds the bot is in
bot.guilds.fetch("guild_id");  // Fetches a specific guild by ID
```

---

## users.fetch()
Fetches a user by their ID.

**Arguments:**
- `id` - The ID of the user to fetch.

**Example:**
```javascript
bot.users.fetch("user_id");  // Fetches a user by their ID
```

---

## channels.fetch()
Fetches a channel by its ID.

**Arguments:**
- `id` - The ID of the channel to fetch.

**Example:**
```javascript
bot.channels.fetch("channel_id");  // Fetches a channel by ID
```

---

## button()
Registers a button interaction handler.

**Arguments:**
- `action` - The function to execute when the button is clicked.

**Example:**
```javascript
bot.button((interaction) => {
    interaction.reply("Button clicked!");
});
```

---

## ready()
Sets the action to be executed when the bot is ready and connected to Discord.

**Arguments:**
- `action` - The function to execute when the bot is ready.

**Example:**
```javascript
bot.ready(() => {
    console.log("Bot is ready!");
});
```