title: Schedule jobs in MacOSX (a guide to launchd)
updated: 2017-10-04 0:17:00
description: As of MacOSX 10.4, cron became deprecated in favor of launchd. The biggest advantage of launchd is that it does not assume that your computer is always on (as cron does). Therefore, if your Mac is asleep when a scheduled job was supposed to run, it will automatically run when your Mac is awake. 
os: [macosx]
tags: [ops]
deps: []
contributors: ["http://www.github.com/sloria"] 

## Optional (but recommended): Install Lunchy

Lunchy makes it easier to manage your agents. 

```bash
# Install lunchy
$ gem install lunchy
```

## Create a plist

Instead of using crontab's text files, launchd jobs (or "agents") are stored in XML files with a `.plist` extension.

Your plist files should go in `~/Library/LaunchAgents/` so that they will be loaded automatically when you log in.

Let's say we want to run a python script called `email.py` at a regular interval. The script takes one argument, an email address.

Make a file using reverse domain syntax, like `~/Library/LaunchAgents/org.yourusername.email-mom.plist`.

```bash
# Make a plist file
$ touch ~/Library/LaunchAgents/org.yourusername.email-mom.plist
# Open this file in your text editor
```

Your plist might look like this:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <!-- The label should be the same as the filename without the extension -->
    <string>org.yourusername.email-mom</string>
    <!-- Specify how to run your program here -->
    <key>ProgramArguments</key>
    <array>
        <string>/usr/local/bin/python</string>
        <string>/Users/yourusername/bin/email.py</string>
        <string>mom@home.com</string>
    </array>
    <!-- Run every hour -->
    <key>StartInterval</key>
    <integer>3600</integer><!-- seconds -->
</dict>
</plist>
```

You can use this as a template.

If you want to schedule the job for calendar intervals (like in cron), you can use `StartCalendarInterval` instead of `StartInterval`.

```xml
<!-- StartCalendarInterval examples -->

    <!-- Run every Sunday (weekday 0) at 15:30/3:30PM -->
    <key>StartCalendarInterval</key>
    <dict>
          <key>Weekday</key>
          <integer>0</integer>
          <key>Hour</key>
          <integer>15</integer>
          <key>Minute</key>
          <integer>30</integer>
    </dict>

    <!-- You can use an array of dicts to specify multiple intervals -->
    <!-- Run at the beginning and middle of every hour, every day -->
    <key>StartCalendarInterval</key>
    <array>
        <dict>
            <key>Minute</key>
            <integer>0</integer>
        </dict>
        <dict>
            <key>Minute</key>
            <integer>30</integer>
        </dict>
    </array>
```

Now you need to load your agent and start it.

```bash
# Load and start your new agent

## With the built in `launchctl`
$ launchctl load ~/Library/LaunchAgents/org.yourusername.email-mom.plist
$ launchctl start org.yourusername.email-mom

## Or with Lunchy
## `restart` will unload your agent (if it's loaded), load it, then start the job
## Lunchy sees the argument as a pattern, so you don't have to specify the entire agent-name
$ lunchy restart email-mom
```

You can also see a list of loaded agents.

```bash
# Show loaded agents
$ launchctl list
# OR
$ lunchy list
```

To stop an agent:

```bash
# Stop an agent
$ launchctl stop org.yourusername.email-mom
# OR
$ lunchy stop email-mom
```

See also:

- [nathangrigg's launchd tutorial][]
- [Alvin Alexander's launchd examples](http://alvinalexander.com/mac-os-x/launchd-plist-examples-startinterval-startcalendarinterval)
- [Why cron was deprecated](http://web.archive.org/web/20060314034955/http://developer.apple.com/macosx/launchd.html)
- [Launchd plist man page, including all options](https://developer.apple.com/library/mac/#documentation/Darwin/Reference/ManPages/man5/launchd.plist.5.html)

[nathangrigg's launchd tutorial]:http://nathangrigg.net/2012/07/schedule-jobs-using-launchd/





