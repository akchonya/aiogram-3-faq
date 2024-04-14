# Common errors

## Migration related errors

Aiogram has recently had [a major version update](https://docs.aiogram.dev/en/latest/migration_2_to_3.html), so a lot of tutorials on the web are outdated now.

```python
Traceback (most recent call last):
  File "/root/bot_update/main.py", line 1, in <module>
    from aiogram.utils import executor
ImportError: cannot import name 'executor' from 'aiogram.utils' (/usr/local/lib/python3.10/dist-packages/aiogram/utils/__init__.py)
```

This is the most popular example. Previously, aiogram used `executor` to manage all of the execution proccesses. However, in aiogram 3.x, it's integrated into the dispatcher. As a result, even the simplest 2.x example wouldn't work on aiogram 3.x.

![what_am_i_supposed_to_do_then](images/migration.webp)

1. Drop your outdated tutorial. If you are just learning aiogram [you shouldn't start with unsupported versions](https://akchonya.github.io/aiogram-3-faq/common_questions/#which-aiogram-version-should-i-use).
2. Make your [first steps](https://akchonya.github.io/aiogram-3-faq/common_questions/#where-should-i-start-from) into aiogram 3.

!!! info "Another option"
    Yes, you *can* downgrade your aiogram to 2.x via `pip install aiogram==2.25.2`, but do you really *want* to start learning the outdated and unsupported version?

## Python versions related errors

### Invalid syntax

```python
File "main.py", line 15
  async def start(message: Message):
      ^
SyntaxError: invalid syntax
```

You use python < 3.8. You can check supported versions at [PyPi](https://pypi.org/project/aiogram/) and upgrade.

---

```python
File "/home/user/bot/main.py", line 30    
  match unit:
      ^
SyntaxError: invalid syntax
```

You've probably tested in on your local machine and everything was alright, but when you moved to VPS this problem occured.

Check your python version. The match case was intoduced in python 3.10.

### Wheels for aiohttp

```python
  note: This error originates from a subprocess, and is likely not a problem with pip.
  ERROR: Failed building wheel for aiohttp
Failed to build aiohttp
ERROR: Could not build wheels for aiohttp, which is required to install pyproject.toml-based projects
```

Chances are that you are using python 3.12 with an older version of aiogram 3.x.

You can either install python 3.11 or the most recent aiogram.

## Deprecation Warning

```python
DeprecationWarning: Passing parse_mode, disable_web_page_preview or protect_content to Bot initializer is deprecated. This arguments will be removed in 3.7.0 version
Use default=DefaultBotProperties(...) instead.
  bot = Bot(TOKEN, parse_mode=ParseMode.HTML)
```

!!! info "That's not an error *yet*"
    That's a warning concerning future updates. You still can use `parse_mode=ParseMode.HTML` in the current aiogram 3.4 version. However, it will be removed in the future.

That's what you should use now:

```python
from aiogram.client.default import DefaultBotProperties
...

bot = Bot(
  token=BOT_TOKEN,
  default=DefaultBotProperties(parse_mode=ParseMode.HTML),
    )
```

[DefaultBotProperties](https://github.com/aiogram/aiogram/blob/dev-3.x/aiogram/client/default.py) contains more properties than just a parse mode, including:

```text
- parse_mode
- disable_notification
- protect_content
- allow_sending_without_reply
- link_preview
- link_preview_is_disabled
- link_preview_prefer_small_media
- link_preview_prefer_large_media
- link_preview_show_above_text
```

## Bad Request: can't parse entities

!!! tip "If you have no idea what that formatting means.."
    Check out [infomation about text formatting in aiogram](https://akchonya.github.io/aiogram-3-faq/common_questions/#text-formatting).

If you are getting the following error:

```txt
exception=TelegramBadRequest('Telegram server says - Bad Request: can't parse entities: Unsupported start tag "<1;</code" at byte offset 59')>
```

chances are that your text contains special characters, that cannot be parsed (for example, "<" or ">" in html parse mode).

If your code looks something like that `html.bold(your_text)` you should change it to `html.bold(html.unparse(your_text))`.

!!! note "There is another way"
    You can use aiogram formatting classes directly instead of using the unparse method. In that case your code will look a bit different (arguably more complex).

```python
from aiogram.utils.formatting import Bold

@router.message(Command("bold"))
async def bold_command(message: Message):
    bold = Bold(your_text)
    await message.answer(**bold.as_kwargs())
```

<sub>*example by* [Avazart](https://t.me/Avazart)</sub>