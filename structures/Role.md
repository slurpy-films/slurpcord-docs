# Slurcord Docs > Structures > Role

This file defines a `role` structure that lets you manage roles in your Discord server.

## Methods:

### delete()
Deletes the role from the server.

**Arguments:**
- `reason` (optional) - Audit log reason.

**Example:**
```javascript
const role = await bot.guilds.roles.fetch("123456789012345678"); // Replace with a real role ID

try {
    await role.delete("This role is no longer needed.");
    console.log(`Successfully deleted the role: ${role.name}`);
} catch (error) {
    console.error("Failed to delete the role!", error);
}
```

### edit()
Changes different settings of the role.

**Arguments:**
- `options` - An object that can have the following properties. You can change one or more of these at the same time.
    - `name` (optional) - The new name for the role.
    - `color` (optional) - The new color for the role (as a number).
    - `permissions` (optional) - The new permissions for the role (as a number).
    - `hoist` (optional) - Set to `true` to make the role show up separately in the member list, or `false` to hide it.
    - `mentionable` (optional) - Set to `true` to let people mention the role, or `false` to prevent it.

**Example:**
```javascript
const role = await bot.guilds.roles.fetch("123456789012345678"); // Replace with a real role ID

try {
    const updatedRole = await role.edit({
        name: "Super Cool Role",
        color: 0x00FF00, // Green color
        hoist: true,
        mentionable: false
    });
    console.log(`Successfully updated the role to: ${updatedRole.name}`);
} catch (error) {
    console.error("Failed to edit the role!", error);
}
```

### setColor()
A quick way to change the color of the role.

**Arguments:**
- `color` - The new color for the role (as a number).

**Example:**
```javascript
const role = await bot.guilds.roles.fetch("123456789012345678"); // Replace with a real role ID

try {
    await role.setColor(0xFF0000); // Red color
    console.log(`Successfully set the role color to red.`);
} catch (error) {
    console.error("Failed to set the role color!", error);
}
```

### setPermissions()
A quick way to change the permissions of the role.

**Arguments:**
- `permissions` - The new permissions for the role (as a number).

**Example:**
```javascript
const role = await bot.guilds.roles.fetch("123456789012345678"); // Replace with a real role ID
// Example: Giving the role administrator permissions (this is usually a bad idea to do lightly!)
const ADMINISTRATOR_PERMISSION = 8;

try {
    await role.setPermissions(ADMINISTRATOR_PERMISSION);
    console.log(`Successfully set the role to have administrator permissions.`);
} catch (error) {
    console.error("Failed to set the role permissions!", error);
}
```

### setHoist()
A quick way to make the role show up separately in the member list (or hide it).

**Arguments:**
- `hoist` - Set to `true` to show the role separately, or `false` to hide it.

**Example:**
```javascript
const role = await bot.guilds.roles.fetch("123456789012345678"); // Replace with a real role ID

try {
    await role.setHoist(true);
    console.log(`Successfully set the role to be hoisted.`);
} catch (error) {
    console.error("Failed to set the role hoisting!", error);
}
```

### setMentionable()
A quick way to let people mention the role (or prevent it).

**Arguments:**
- `mentionable` - Set to `true` to allow mentions, or `false` to disallow them.

**Example:**
```javascript
const role = await bot.guilds.roles.fetch("123456789012345678"); // Replace with a real role ID

try {
    await role.setMentionable(true);
    console.log(`Successfully set the role to be mentionable.`);
} catch (error) {
    console.error("Failed to set the role mentionability!", error);
}
```