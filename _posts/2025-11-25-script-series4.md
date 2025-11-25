---
title: "Script series 4"
date:   2025-11-25
categories:
  - Scripts
tags:
  - Scripts
  - tools
  - linux
  - posix
---

Ello

Today's script is a pomodoro timer which uses festival to use TTS to get you to stop working or start working again

This first part is to format time for the timer
```bash
function format_time() {
    local seconds=$1
    printf "%02d:%02d:%02d" $((seconds / 3600)) $(((seconds % 3600) / 60)) $((seconds % 60))
}
```


This function starts with setting work time and break time
and then for each cycle it sends a notification and TTS message
```bash
function pomodoro_timer() {
    local work_time="30 * 60"  # 25 minutes in seconds
    local break_time="10 * 60" # 5 minutes in seconds
    local cycles=3       # Number of Pomodoro cycles

    for ((cycle = 1; cycle <= cycles; cycle++)); do
        for ((time_left = work_time; time_left > 0; time_left--)); do
            echo -ne "Pomodoro $cycle: Work Time Left: $(format_time $time_left)\033[0K\r"
            sleep 1
        done

        echo "Time for a short break!" | festival --tts   # Notify using Festival
        notify-send "Pomodoro $cycle" "Time for a short break!" -t 5000  # Notify using notify-send

        for ((time_left = break_time; time_left > 0; time_left--)); do
            echo -ne "Pomodoro $cycle: Break Time Left: $(format_time $time_left)\033[0K\r"
            sleep 1
        done

        echo "Back to work!" | festival --tts # Notify using Festival
        notify-send "Pomodoro $cycle" "Back to work!" -t 5000  # Notify using notify-send
        
    done
    echo -ne "\033[0K\r"
    echo "Pomodoro completed!"
}
```