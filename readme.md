# phpBB Notifier for macos

A command line tool that watches desired forum threads and on a given interval, creates a Macos notification badge if new messages have been posted.

## Requirements

1. You need to have [uv](https://docs.astral.sh/uv/) installed.
2. Built to work with phpBB version 3.2.2.

> [!NOTE]
> Different themes and customisations may affect the functionality. It may work with earlier versions too but hasn't been tested on them.

## Usage

First, create a `phpbbnotifier.config.toml` file:

```toml
[forum-name]
    baseurl = "base-url-for-forum"
    [forum-name.sub-forum-name]
        id = sub-forum-id
        threads = [thread-id-1, thread-id-2, ...]
```

**Note:** You can't use spaces in the forum or sub forum names. The names are for your organisation only, they are not used anywhere in the script currently.

You can add multiple forums, subforums and threads to go through.

Make the script executable with

```shell
chmod +x phpbb-notifier
```

Then, start the script with

```shell
./phpbb-notifier
```

and it will run every 5 minutes and add a notification banner if new posts have been made.

If any URLs return 4xx or 5xx status codes, they will be removed from the checks until restarted.
