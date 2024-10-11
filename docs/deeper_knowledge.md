# Deeper Knowledge

If you have no problems with python and understanding examples from documentation, there is a chance that you are thinking about more complex projects. There are some useful things, that you might need.

## Templates

Here is one of the simplest structures for your first project. Most of the module names are self-explanatory. I would suggest putting configuration settings in the `utils` module, along with any additional helper files.

```.
├── bot/
|   ├── filters/
|   ├── handlers/
|   ├── keyboards/
|   ├── middlewares/
|   └── utils/
|   .env
└── main.py
```

There are some more complex community templates available for you to explore.

[`Latand/tgbot_template_v3`](https://github.com/Latand/tgbot_template_v3)
[`wakaree/aiogram_bot_template`](https://github.com/wakaree/aiogram_bot_template)
[`andrew000/aiogram-template`](https://github.com/andrew000/aiogram-template)

## Databases

If you are planning to make somewhat complex bots you would most definitely use databases. There is also a [CS50SQL](https://cs50.harvard.edu/sql/2024/) course that teaches basic of SQL language. They mostly use SQLite to grasp the basics, but it's not recommended to use it with telegram bots (as any file database can be locked while working with async requests).

Look into [PostgreSQL](https://www.postgresql.org/) with [SQLAlchemy](https://www.sqlalchemy.org/) ORM and [Alembic](https://alembic.sqlalchemy.org/en/latest/) if you want an SQL database or into [MongoDB](https://www.mongodb.com/) for NoSQL one.

## APScheduler

If you are planning to have scheduled or intervaled tasks you should look into [APScheduler](https://apscheduler.readthedocs.io/en/3.x/).

Check out [this part of Telegram Bot API FAQ](https://core.telegram.org/bots/faq#broadcasting-to-users) before sending messages to all of your users

## Redis

There is a lot of data in bots' memory storage that could be lost after restarting. To prevent it you should use [Redis](https://redis.io/).

## ngrok

If you are trying to localhost an aiogram bot using webhooks you definitely need to use [ngrok](https://ngrok.com/) to get the webhook link.

## i18n

If you want to have several localizations and don't know how implement that - use [aiogram i18n](https://github.com/aiogram/i18n) library.

## Deploying

If you are ready to show off your bot you would need to host it somewhere. There are a lot of [affordable hostings](https://t.me/about_aiogram/12) that you can choose from.

!!! Tip "My experience"
    I have personally been using [MVPS.net](https://www.mvps.net/) and have no complaints. However,  it's important to understand the basics of SSH protocol usage.

To make the deployment as smooth as possible you'd better be familiar with [Docker](https://www.docker.com/) and [Git](https://git-scm.com/) (with, for example, [GitHub](https://github.com/)).
