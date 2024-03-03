# Prior Knowledge

Many errors occur when people with no prior Python experience attempt to write their first project.

```python
from aiogram import Bot

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
ERROR!
Traceback (most recent call last):
  File "<string>", line 1, in <module>
ModuleNotFoundError: No module named 'aiogram'
```

Aiogram is a highly specialized library that involves complex concepts, making it unsuitable for starting your Python journey.

## What do I absolutely need to know?

- variables
- functions
- conditionals
- loops
- exceptions
- OOP
- testing
- venv
- decorators
- async

Most of those topics are covered at [CS50p](https://cs50.harvard.edu/python/2022/) course. It's absolutely free to take and has some great problem sets.

You would at least need to get a basic understanding of venv, decorators and async.

## What else could be useful?

### Databases

If you are planning to make somewhat complex bots you would most definitely use databases. There is also a [CS50SQL](https://cs50.harvard.edu/sql/2024/) course that teaches basic of SQL language. They mostly use SQLite to grasp the basics, but it's not recommended to use it with telegram bots (as any file database can be locked while working with async requests).

Look into [PostgreSQL](https://www.postgresql.org/) with [SQLAlchemy](https://www.sqlalchemy.org/) ORM and [Alembic](https://alembic.sqlalchemy.org/en/latest/) if you want an SQL database or into [MongoDB](https://www.mongodb.com/) for NoSQL one.

### APScheduler

If you are planning to have scheduled or intervaled tasks you should look into [APScheduler](https://apscheduler.readthedocs.io/en/3.x/).

### Redis

There is a lot of data in bots' memory storage that could be lost after restarting. To prevent it you should use [Redis](https://redis.io/).

### Deploying

If you are ready to show off your bot you would need to host it somewhere. There are a lot of [affordable hostings](https://t.me/about_aiogram/12) that you can choose from. To make the deployment as smooth as possible you'd better be familiar with [Docker](https://www.docker.com/) and [Git](https://git-scm.com/) (with, for example, [GitHub](https://github.com/)).

## Asking questions

You've taken a look at everything above, started working on your first bot and encoutered some difficulties that you can't deal with?

Before asking for help, consider [googling first](https://w0rrapss.github.io/google-first/), whether through search engines or the aiogram chat. Also, [documentation](https://docs.aiogram.dev/en/latest/) has proved to be very helpful, don't forget to take a look!

If you're convinced your issue is unique and hasn't been addressed before, please avoid [meta](https://nometa.xyz/) in the chat.

Choose an appropriate chat topic and provide a [MRE](https://en.wikipedia.org/wiki/Minimal_reproducible_example#:~:text=In%20computing%2C%20a%20minimal%20reproducible,to%20be%20demonstrated%20and%20reproduced.) along with your error traceback or an explanation of unwanted behaviour.

Please remember to be polite to those who are assisting you. It's not advisable to send private messages asking about your errors or providing your entire code for review. Those people usually get tons of messages like that and simply have no time to answer them. Instead, communicate through the chat or consider purchasing a private consultation if available.
