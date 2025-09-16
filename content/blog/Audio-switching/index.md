+++
title = "I Spent Hours Automating a 0.5 Second Task (And It Was Worth It)"
description = "Building a time-based audio automation script for Fedora that switches between speakers and headphones at login — because manually clicking is for peasants."
date = 2025-09-16
tags = ["Fedora","automation","bash","audio","PipeWire","productivity","over-engineering"]
+++

You know that bone-deep exhaustion from doing the same tiny task over and over? Yeah, I got tired of manually switching between my Speakers and 3.5mm headphones every time I boot up.

It's not that I forgot. It's that I'm lazy and got sick of clicking the same two buttons every single day.

So naturally, I did what any reasonable developer would do: spent an entire evening building an automation script to save myself 0.5 seconds of clicking.

## The Problem

My setup is simple:
- **Daytime**: Logitech 2.1 speakers connected through my display
- **Nighttime**: Headphones for those considerate late-night sessions

But manually switching got old fast. Boot up at 10 PM and have to switch to headphones. Boot up at 8 AM and switch back to speakers. Every. Single. Time.

Nah, I'm done with that.

## The Solution: Peak Developer Behavior

Built a bash script that runs at login and automatically switches based on time:

- **10:00 AM - 12:00 AM**: Speakers for daytime productivity
- **12:01 AM - 9:59 AM**: Headphones for quiet night sessions

```bash
# The core logic is beautifully simple
current_hour=$(date +%H)
if [ $current_hour -ge 10 ] || [ $current_hour -eq 0 ]; then
    target_device="$HDMI_DEVICE"  # Speakers
else
    target_device="$ANALOG_DEVICE"  # Headphones
fi
```

## The Technical Bits (Because I Went Overboard)

Of course I couldn't just write a simple script. It had to be bulletproof:

- Waits up to 45 seconds for PipeWire to initialize (because audio systems are moody)
- Handles device detection and graceful failures
- Moves existing audio streams to the new device
- Logs everything to debug when things inevitably break
- Uses lock files to prevent multiple instances
- Shows desktop notifications because why not

The script is way smarter than it needs to be. Classic over-engineering.

## Was It Worth It?

From a time perspective? Absolutely not. I'll never recoup those hours.

From a "my computer now reads my mind" perspective? Hell yes. Every boot, the right audio device is just there. No thinking, no clicking, no repetitive strain on my clicking finger.

That's the beauty of personal automation projects. They're rarely about efficiency. They're about that tiny dopamine hit when your environment just works the way you want.

## The Code

Threw it on [GitHub](https://github.com/yourusername/fedora-audio-automation) for anyone else who's tired of clicking buttons. It's heavily commented because future me will forget how any of this works.

Works on any Fedora system with PipeWire or PulseAudio. Just update the device names for your hardware.

---

*What's the most ridiculous thing you've automated to avoid a simple manual task? Please tell me I'm not alone in this madness.*
