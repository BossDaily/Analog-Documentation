---
sidebar_position: 2
---

# Basic Commands

Creating Slash commands in Analog-TSX is similar to how [Discordjs.guide](https://discordjs.guide/creating-your-bot/slash-commands.html#individual-command-files) teaches you to create slash commands. 
The difference is that Analog-TSX uses Typescript, meaning you're going to have to specify the types on the interaction.
Ex:
```ts title="/analog-tsx/apps/bot/src/commands/findPlayer.ts"
async execute(interaction: ChatInputCommandInteraction) {

}
```
The upside of using our framework is there is a command handler built in so all you have to worry about is the logic

### Individual files for the commands
Each new command should have its own file for the command and sub commands. Create a new file in the `src/commands` directory and name it whatever you want. Then import the neccessary methods from discord.js (and other libraries you're using).

```ts title="/analog-tsx/apps/bot/src/commands/ping.ts"
import {
  Interaction,
  EmbedBuilder,
  CommandInteractionOptionResolver,
  Message,
  CommandInteraction,
  ApplicationCommand,
  SlashCommandBuilder,
  SlashCommandStringOption,
  ActionRowBuilder,
  ButtonBuilder,
  ButtonStyle,
  MessageActionRowComponentBuilder,
} from "discord.js";
```

### Creating the command
Create a `module.exports` so the command can be used in the command handler. The `module.exports` should have a `data` property and an `execute` property. The `data` property is where you will create the slash command. The `execute` property is where you will put the logic for the command.

```ts title="/analog-tsx/apps/bot/src/commands/ping.ts"
module.exports = {
  data: new SlashCommandBuilder()
    .setName("ping")
    .setDescription("Replies with pong!"),
  async execute(interaction: CommandInteraction) {
    await interaction.reply("Pong!");
  },
};
```

The file should look like this so far:
```ts title="/analog-tsx/apps/bot/src/commands/ping.ts"
import {
  Interaction,
  SlashCommandBuilder,
  CommandInteraction,
} from "discord.js";

module.exports = {
  data: new SlashCommandBuilder()
    .setName("ping")
    .setDescription("Replies with pong!"),
  async execute(interaction: CommandInteraction) {
    await interaction.reply("Pong!");
  },
};
```

### Registering the command
Now that you have created the command, you need to register it. They're two methods you can use to register the command:

- `registerCmd: true` in the [devConfig](./intro#developer-config)
- In the commandline by doing
```bash title="/analog-tsx/apps/bot"
npm run reg-cmds
```

:::tip You can clear __ALL__ the commands
If you want to clear the commands, you can do:
```bash title="/analog-tsx/apps/bot"
npm run delete-cmds
```
:::
**__Its actually best advised to register the commands before you start working on the logic, that way you can easily test the commands__**