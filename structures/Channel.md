# Slurcord Docs > Structures > Channel

This file defines a `channel` structure that lets you work with Discord channels.

## Methods:

### send()
Sends a message to the channel.

**Arguments:**
- `content` - The content of the message to send. This can be a string for a simple text message or an object with options like `content`, `embeds` (for embedded messages), and `attachments`.

**Example:**
```javascript
const channel = await bot.channels.fetch("123456789012345678"); // Replace with a real channel ID

// Sending a simple text message
await channel.send("Hello there!");

// Sending a message with an embed
const embed = new Embed().setDescription("This is an embedded message!");
await channel.send({ embeds: [embed] });

// Sending a message with an attachment
const attachment = new Attachment().setFile("./my_image.png", "image.png");
await channel.send({ content: "Check out this image!", attachments: [await attachment.toJSON()] });
```

### messages.fetch()
Fetches a specific message or the list of recent messages from the channel.

**Arguments:**
- `id` (optional) - The ID of a specific message to fetch. If this is not provided, it will attempt to fetch recent messages (though this functionality might need more implementation to handle multiple messages).

**Example:**
```javascript
const channel = await bot.channels.fetch("123456789012345678"); // Replace with a real channel ID

// Fetching a specific message by its ID
try {
    const message = await channel.messages.fetch("987654321098765432"); // Replace with a real message ID
    console.log("Fetched message:", message);
} catch (error) {
    console.error("Failed to fetch message:", error);
}

try {
    await channel.messages.fetch("ID");
    console.log("Attempted to fetch a message");
} catch (error) {
    console.error("Failed to fetch a message:", error);
}
```