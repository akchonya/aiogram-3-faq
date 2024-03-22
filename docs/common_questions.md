# Common Questions

## Which aiogram version should I use?

Aiogram 2.x is essentially outdated at this point. While it can still be used, it lacks support for the latest TelegramBotApi versions. Understanding Aiogram 2.x may be necessary to maintain older projects, but aside from that, there's little reason to begin learning it now. It's advisable to start with the most recent version.

## Where should I start from?

Try the [Simple Usage](https://docs.aiogram.dev/en/latest/#simple-usage) example from the documentation.

## Can my bot use premium emojis?

Yes, but it [requires buying a custom Fragment username](https://stackoverflow.com/questions/74437942/how-to-send-custom-emoji-from-bot-in-telegram/76853897#76853897) for 5000 TON ($12k at the time of the acticle's creation).

## Can two of my bots communicate?

Short answer is [no](https://core.telegram.org/bots/faq#why-doesn-39t-my-bot-see-messages-from-other-bots).

However, you can establish their communication through third-party software, as they cannot directly see each other's messages on Telegram.

## How can I send code blocks?

If you use HTML parse mode, you can use an in-built shortcut:

```python
from aiogram import html

...

await message.answer(html.pre_language(value="your_code", language="language_name"))
```

In case of working with Markdown you have to use the following code:

```python
from aiogram import md

...

await message.answer(md.pre_language(value="your_code", language="language_name"))
```

**Output:**

![codeblock_output](images/codeblock.webp)

## Can my bot process messages received while it was offline?

As the [Telegram Bot API documentation](https://core.telegram.org/bots/api#getting-updates) states:

> There are two mutually exclusive ways of receiving updates for your bot - the getUpdates method on one hand and webhooks on the other. Incoming updates are stored on the server until the bot receives them either way, but they will not be kept longer than 24 hours.

In case of working with polling you can call the `getUpdates()` (for example, use can add `await bot.get_updates()` in the startup function) method to retrieve all the missed messages.

If you have a webhook - configure it while setting up:

```python
await bot.set_webhook(..., drop_pending_updates=False)
```
