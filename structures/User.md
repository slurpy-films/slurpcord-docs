# Slurcord Docs > Structures > User

This file defines a `user` structure that helps you work with information about Discord users.

## Methods:

### send()
Sends a direct message (DM) to the user.

**Arguments:**
- `content` - The message you want to send. This can be a simple text message (a string) or an object.

**Example:**
```javascript
const user = await bot.users.fetch("123456789012345678"); // Replace with a real user ID

try {
    await user.send("Hey there! How are you doing?");
    await user.send({ content: "This is another way to send a DM!" });
} catch (error) {
    console.error("Oops! Couldn't send a DM to that user.", error);
}
```

### avatarURL()
Gives you the URL of the user's avatar (profile picture).

**Arguments:**
- `options` (optional) - An object that lets you change how the avatar URL is generated. Right now, the only option you can use is:
    - `size`: A number that says how big you want the image to be (in pixels). Common sizes are 16, 32, 64, 128, 256, 512, and 1024. The default size is 1024.

**Example:**
```javascript
const user = await bot.users.fetch("123456789012345678"); // Replace with a real user ID

// Get the default avatar URL (size 1024)
const defaultAvatar = user.avatarURL();
console.log("Default avatar URL:", defaultAvatar);

// Get a smaller avatar (size 64)
const smallAvatar = user.avatarURL({ size: 64 });
console.log("Small avatar URL:", smallAvatar);
```