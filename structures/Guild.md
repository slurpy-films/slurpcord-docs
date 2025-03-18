# Slurcord Docs > Structures > Guild

This file defines a `guild` structure that lets you work with guilds.

## Methods:

### members.fetch()
Fetches information about a specific member in the guild. It first checks if the member's information is already saved in the cache to be faster.

**Arguments:**
- `userId` - The ID of the user you want to get information about. **Important:** This is required!

**Example:**
```javascript
const guild = await bot.guilds.fetch("123456789012345678"); // Replace with a real guild ID

try {
    const member = await guild.members.fetch("987654321098765432"); // Replace with a real user ID
    console.log(`Found member: ${member.user.username}#${member.user.discriminator}`);
} catch (error) {
    console.error("Couldn't find that member!", error);
}
```

### channels.fetch()
Fetches information about a specific channel in the guild.

**Arguments:**
- `channelId` - The ID of the channel you want to get information about.

**Example:**
```javascript
const guild = await bot.guilds.fetch("123456789012345678"); // Replace with a real guild ID

try {
    const channel = await guild.channels.fetch("876543210987654321"); // Replace with a real channel ID
    console.log(`Found channel: ${channel.name} (type: ${channel.type})`);
} catch (error) {
    console.error("Couldn't find that channel!", error);
}
```

### channels.create()
Creates a new channel in the guild.

**Arguments:**
- `channel` - An object containing the information for the new channel. It can have the following properties:
    - `name` - The name of the new channel. **Required.**
    - `type` - The type of the channel (e.g., `0` for text, `2` for voice). Check the Discord API for all the types.
    - `parentId` (optional) - The ID of the category this channel should be under.
    - `permissionOverwrites` (optional) - An array of permission overwrite objects for specific roles or members.

**Example:**
```javascript
const guild = await bot.guilds.fetch("123456789012345678"); // Replace with a real guild ID

try {
    const newChannel = await guild.channels.create({
        name: "new-discussion",
        type: 0, // Text channel
        parentId: "234567890123456789" // Replace with a real category ID (optional)
    });
    console.log(`Created new channel: ${newChannel.name}`);
} catch (error) {
    console.error("Failed to create the channel!", error);
}
```

### channels.delete()
Deletes a channel from the guild.

**Arguments:**
- `channelId` - The ID of the channel you want to delete.

**Example:**
```javascript
const guild = await bot.guilds.fetch("123456789012345678"); // Replace with a real guild ID
const channelToDeleteId = "345678901234567890"; // Replace with a real channel ID

try {
    await guild.channels.delete(channelToDeleteId);
    console.log(`Successfully deleted channel with ID: ${channelToDeleteId}`);
} catch (error) {
    console.error(`Failed to delete the channel with ID: ${channelToDeleteId}`, error);
}
```

### roles.fetch()
Fetches information about roles in the guild. You can either get a specific role by its ID or get a list of all roles in the guild.

**Arguments:**
- `roleId` (optional) - The ID of a specific role you want to get information about. If you don't provide an ID, it will return a list of all roles.

**Example:**
```javascript
const guild = await bot.guilds.fetch("123456789012345678"); // Replace with a real guild ID

// Fetching a specific role by ID
try {
    const role = await guild.roles.fetch("456789012345678901"); // Replace with a real role ID
    console.log(`Found role: ${role.name}`);
} catch (error) {
    console.error("Couldn't find that role!", error);
}

// Fetching all roles in the guild
try {
    const allRoles = await guild.roles.fetch();
    console.log(`Number of roles in the guild: ${allRoles.length}`);
    allRoles.forEach(role => console.log(`- ${role.name} (ID: ${role.id})`));
} catch (error) {
    console.error("Failed to fetch roles!", error);
}
```

### roles.create()
Creates a new role in the guild.

**Arguments:**
- `role` - An object containing the information for the new role. It can have the following properties:
    - `name` - The name of the new role. **Required.**
    - `color` (optional) - The color of the role (as a number).
    - `hoist` (optional) - Whether the role should be displayed separately in the member list (true or false).
    - `mentionable` (optional) - Whether the role can be mentioned by other members (true or false).
    - `permissions` (optional) - The permissions the role should have (as a bitfield number).

**Example:**
```javascript
const guild = await bot.guilds.fetch("123456789012345678"); // Replace with a real guild ID

try {
    const newRole = await guild.roles.create({
        name: "New Awesome Role",
        color: 0xFF00FF, // Magenta color
        hoist: true,
        mentionable: true
    });
    console.log(`Created new role: ${newRole.name} with ID: ${newRole.id}`);
} catch (error) {
    console.error("Failed to create the role!", error);
}
```

### roles.delete()
Deletes a role from the guild.

**Arguments:**
- `roleId` - The ID of the role you want to delete.

**Example:**
```javascript
const guild = await bot.guilds.fetch("123456789012345678"); // Replace with a real guild ID
const roleToDeleteId = "567890123456789012"; // Replace with a real role ID

try {
    await guild.roles.delete(roleToDeleteId);
    console.log(`Successfully deleted role with ID: ${roleToDeleteId}`);
} catch (error) {
    console.error(`Failed to delete the role with ID: ${roleToDeleteId}`, error);
}
```