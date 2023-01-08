---
sidebar_position: 1
---

# Getting Started

Here is how you can get started on the Discord bot portion of Analog-TSX (and Analog-ts).

### Resources
It is highly recommended, that you're familiar with [Discord.js](https://discord.js.org/#/).
We also highly recommend you read their guide, [Discord.js Guide](https://discordjs.guide/) a lot of the methods being taught there can be applied to this framework.

- Discord.JS Docs: [https://discord.js.org/#/docs/main/stable/general/welcome](https://discord.js.org/#/docs/main/stable/general/welcome)
- Discord.JS Guide: [https://discordjs.guide/](https://discordjs.guide/)
- Discord API Types: [https://discord-api-types.dev/](https://discord-api-types.dev/)
- Discord.JS Discord: [https://discord.gg/bRCvFy9](https://discord.gg/bRCvFy9)

### Dev environment 
If you want to setup a developer environment where you can restart the bot and compile it
```bash
cd apps/bot
```
```bash title="/analog-tsx/apps/bot"
npm run watch
```


Do `cd ../` to move up a directory

```bash title="/hoanalog-tsxme/"
npm run dev
```
:::tip Pro tip

You can also just start the bot in the bot directory without starting the dashboard
```bash title="/analog-tsx/apps/bot"
npm run dev
```
:::

### Developer Config
There is a config file you can create by copying `devconfig.example.ts` in the root directory of the bot:
> `/analog-tsx/apps/bot/devconfig.example.ts` 

Then rename it to `devconfig.ts`. This file is ignored by git since it isn't really needed.
It should look like this:
```ts title="/analog-tsx/apps/bot/devconfig.ts"
export const devConfig = {
    registerCmd: true
}
```

The `registerCmd` property is a boolean that determines if the bot should register the commands on startup. This is useful if you want to test the bot without registering the commands. You can also set this to false if you want to test the bot without registering the commands.

:::danger
Its best advised to sparingly use this feature since Discord might rate limit you if you register too many commands too quickly.
:::