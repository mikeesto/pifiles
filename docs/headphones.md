---
title: USB headphones (PulseAudio)
---

Connect your USB headphones to the Pi and then run:

```bash
pactl list
```

In the output of `pactl list`, you will see a list of sinks. Each sink has a `Name` and a `Description`. The `Description` will usually contain the name of the device. For example, if you have a USB headset, the `Description` might be `USB Audio Device`.

Set the sink (for example, sink #2) as the default sink:

```bash
pactl set-default-sink 2
```

Then, try to unsuspend and activate the sink:

```bash
pactl suspend-sink 2 0
```

You might also want to unmute and set the volume of the sink:

```bash
pactl set-sink-mute 2 0
pactl set-sink-volume 2 80%
```

If you want to test if the sound is working, you can play a test sound:

```bash
paplay /usr/share/sounds/alsa/Front_Center.wav
```
