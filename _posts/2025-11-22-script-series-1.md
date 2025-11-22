---
title: "Script series 1"
date:   2025-11-22
categories:
  - Scripts
tags:
  - Scripts
  - tools
  - linux
  - posix
---

Ello today shadow is gonna talk about some script that they have been using for a while

todays script is a countdown timer... here is the code that works in both bash and zsh

## script
```bash
countdown() {
    start="$(( $(date '+%s') + $1))"
    while [ $start -ge $(date +%s) ]; do
        time="$(( $start - $(date +%s) ))"
        printf '%s\r' "$(date -u -d "@$time" +%H:%M:%S)"
        sleep 0.1
    done
    notify-send "countdown timer done"
}
```

## explaination
here follows an explaination of how the script works

start line: take current time since unix epoch using date command and add time in seconds from first parameter input

while loop: loop until start time is greater or equal to current time

printf: print out the timer in a nice looking format and send return char to update it nicely in terminal window

and finally notify-send where we send a notification that the countdown timer has finished

## sign off

and that is all for todays post about scripts

shadow out
