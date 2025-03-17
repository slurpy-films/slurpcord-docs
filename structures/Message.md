# Slurcord Docs > Structures > Message

# Methods:

## reply()
Reply to the message with the message.

**Arguments:**
- `content` - The content to reply with. String or object.

**Example:**
```javascript
bot.command("ping", async (msg) => {
    await msg.reply("This is a normal text message");
    await msg.reply({ content: "This is also a normal text message!" });
    const embed = new Embed()
        .setDescription("This is not a normal text message. This has an embed and an attachment!");
    let attachment = new Attachment()
        .setFile("./image.png", "An image!", "image/png")
    
    attachment = await attachment.toJSON();
    await msg.reply({ embeds: [embed], attachments: [attachment] });
});
```

## edit()
Edit the message.

**Arguments:**
- `content` - Same content as in `reply()`, except `attachment` is not a valid field.

**Example:**
```javascript
bot.command("ping", async (msg) => {
    const m = await msg.reply("Pinging...");
    await m.edit("Pong!");
});
```

## react()
React to the message.

**Arguments:**
- `emoji` - The emoji to react with.

**Example:**
```javascript
bot.command("react", async (msg, input) => {
    await msg.react(input); // Will reply with the emoji the user input. Example: ?react 👋.
})
```

## delete()
Delete the message.

**Arguments:**
No arguments

**Example:**
```javascript
bot.command("deletethis", async (msg) => {
    await msg.delete(); // Will delete the message.
})
```