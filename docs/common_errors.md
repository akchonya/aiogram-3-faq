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

![what_am_i_supposed_to_do_then](https://i.imgur.com/MkWiqig.png)

1. Drop your outdated tutorial. If you are just learning aiogram [you shouldn't start with unsupported versions](https://akchonya.github.io/aiogram-3-faq/common_questions/#which-aiogram-version-should-i-use).
2. Make your [first steps](https://akchonya.github.io/aiogram-3-faq/common_questions/#where-should-i-start-from) into aiogram 3.

!!! info "Another option"
    Yes, you *can* downgrade your aiogram to 2.x via `pip install aiogram==2.25.2`, but do you really *want* to start learning the outdated and upsupported version?

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
