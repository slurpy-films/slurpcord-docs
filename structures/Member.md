# Slurcord Docs > Structures > Member

This structure defines a `member` structure that lets you work with members.

## Methods:

### ban()
Bans the member from the server.

**Arguments:**
- `reason` (optional) - Audit log reason.
- `delmsgdays` (optional) - A number between 0 and 7 that says how many days of their messages should be deleted.

**Example:**
```javascript
const member = await bot.guilds.members.fetch("123456789012345678"); // Replace with a real member ID

try {
    await member.ban("They were not following the server rules.", 7); // Ban and delete their last 7 days of messages
    console.log(`Successfully banned ${member.user.tag}`);
} catch (error) {
    console.error(`Failed to ban ${member.user.tag}!`, error);
}
```

### kick()
Kicks the member from the server.

**Arguments:**
- `reason` (optional) - Audit log reason.

**Example:**
```javascript
const member = await bot.guilds.members.fetch("123456789012345678"); // Replace with a real member ID

try {
    await member.kick("They were being disruptive.");
    console.log(`Successfully kicked ${member.user.tag}`);
} catch (error) {
    console.error(`Failed to kick ${member.user.tag}!`, error);
}
```

### hasPermission()
Checks if the member has a specific permission in a given channel.

**Arguments:**
- `permission` - A string that names the permission you want to check for (e.g., `'ADMINISTRATOR'`, `'MANAGE_CHANNELS'`, `'SEND_MESSAGES'`, `'VIEW_CHANNEL'`).
- `channel` - The channel object (from your API wrapper) where you want to check the permission.

**Example:**
```javascript
const guild = await bot.guilds.fetch("123456789012345678"); // Replace with a real guild ID
const member = await guild.members.fetch("987654321098765432"); // Replace with a real member ID
const channel = await guild.channels.fetch("876543210987654321"); // Replace with a real channel ID

try {
    const canSendMessages = await member.hasPermission('SEND_MESSAGES', channel);
    if (canSendMessages) {
        console.log(`${member.user.tag} can send messages in ${channel.name}.`);
    } else {
        console.log(`${member.user.tag} cannot send messages in ${channel.name}.`);
    }

    const isAdmin = await member.hasPermission('ADMINISTRATOR', channel);
    if (isAdmin) {
        console.log(`${member.user.tag} is an administrator in ${channel.name} (and likely the whole server!).`);
    } else {
        console.log(`${member.user.tag} is not an administrator in ${channel.name}.`);
    }
} catch (error) {
    console.error("Failed to check permissions!", error);
}
```