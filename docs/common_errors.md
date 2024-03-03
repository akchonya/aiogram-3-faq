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
