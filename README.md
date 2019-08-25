# IRedis (Interactive Redis)


[![CircleCI](https://circleci.com/gh/laixintao/iredis.svg?style=svg)](https://circleci.com/gh/laixintao/iredis)
[![PyPI version](https://badge.fury.io/py/iredis.svg)](https://badge.fury.io/py/iredis)
<img src="https://storage.googleapis.com/cloudrun/button.svg" height="21" href="https://console.cloud.google.com/cloudshell/editor?shellonly=true&cloudshell_image=gcr.io/cloudrun/button&cloudshell_git_repo=https://github.com/laixintao/iredis.gi://console.cloud.google.com/cloudshell/editor?shellonly=true&cloudshell_image=gcr.io/cloudrun/button&cloudshell_git_repo=https://github.com/laixintao/iredis.git" alt="Run on Google Cloud">

*Google Cloud Run Hint: You can try iredis on Google Clour Run. Note GCR will try to deploy this image to cloud run, but we actually don't need to deploy, it's just a cli tool, so you just run `docker run -it you-built-image` after deply fails.*

A Terminal Client for Redis with AutoCompletion and Syntax Highlighting. It is an alternative for redis-cli. IRedis is supposed to friendly for both user and redis-server, which means it is safe to use IRedis on production server. IRedis provide a `--strict` mode to prevent accidently running dangerous command, like `KEYS *`(See [here](https://redis.io/topics/latency), the *Latency generated by slow commands* section.

![](./docs/assets/auto-complete.png)

**This project is under development, any comments are welcome.**

## Features

- Advanced code completion. If you run command `KEYS` then run `DEL`, iredis will auto complete your command based on `KEYS` result.
- Command validation: `CLUSTER MEET IP PORT`
- Command highlighting, fully based on redis grammar. Any valide command in iredis shell is a valide redis command.
- <kbd>Ctrl</kbd> + <kbd>C</kbd> to clear cureent line, won't exit redis-cli. Use <kbd>Ctrl</kbd> + <kbd>D</kbd>  
- Say "Goodbye!" to you when you exit!
- <kbd>Ctrl</kbd> + <kbd>R</kbd> to open **reverse-i-search** to search through command history.
- Auto suggestions. (Like [fish shell](http://fishshell.com/).)
- Support `--encode=utf-8`, to decode Redis' bytes responses.
- Command hint on bottom, include command syntax, supported redis version, and time complexity.

## Install

```
pip install iredis
```

## Usage

```
$ iredis -h
```

## Development

### Setup Environment

iredis favors [poetry](https://github.com/sdispater/poetry) as a packagement tool. You can setup a develop envioment on your computer easily.

First, install poetry(You can do it in a python's virtualenv):

```
pip install poetry
```

Then run(which euqals `pip install -e .`):

```
poetry install --develop=DEVELOP
```

### Development Logs

Since this is a commandline tool, so we didn't write logs to stdout.

You can `tail -f iredis.log` to see logs, the log is pretty clear, you can see what actually happend from log files.

### Command Reference

There is a full Redis command list in [commands.csv](commands.csv) file, downloaded by:

```
python scripts/download_redis_commands.py > data/commands.csv
```

`commands.csv` is here only for test if redis.io was updated, do not package it into release.

Current implemented commands: [command_syntax.csv](command_syntax.csv).

## Planned Features

Please see issue. And you are welcome to submit one.

## Related Projects

- [redis-tui](https://github.com/mylxsw/redis-tui)
