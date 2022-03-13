---
layout: post
title:  "PicoArcade: a fun project to discover microcontrollers"
date:   2022-01-09 12:00:00
categories: 
post_url: pico-arcade
---

I’ve wanted to get into microcontrollers for a little while. 2021 was a fun year for it, as:

  - Micropython (*uPython*) has reached an interesting level of maturity in the past years, meaning I could stay in relatively known territory for my skills (I’m more of a Python than C coder)
  - The [Raspberry Pi Pico](https://www.raspberrypi.com/products/raspberry-pi-pico/) came out, and with it some interesting possibilities for cool uPython projects on a very cheap board.
  - I started using a Raspberry Pi 4 for a project at work, but ran into issues with energy consumption. Raspberry Pis consume about [1 to 5 Watts](https://www.pidramble.com/wiki/benchmarks/power-consumption) of power, which is not compatible with long term usage in the field. The logical next step would be to port the application to microcontrollers, for their greatly lowered energy footprint (on the order of [0.01 to 0.1 Watts](https://www.jeffgeerling.com/blog/2021/raspberry-pi-pico-new-4-microcontroller)), and their near instantaneous startup time that would enable to deep-sleep between uses.

Then, I ran across [this cool Tweet](https://twitter.com/ghidraninja/status/1422900329369178113?s=21) showcasing a fun-looking arcade-like toy that could be built with a Pico and a bunch of buttons. Not a lot to go on though (the code wasn’t available yet, it has since been [released](https://github.com/stacksmashing/pico-light-arcade/)). Digging a little, I found another cool and relevant project, for a [Pico-based MIDI controller](https://learn.adafruit.com/raspberry-pi-pico-led-arcade-button-midi-controller-fighter).

The seed was planted, and the idea started to take shape in my mind. I tried looking for the components I would need and buy them in Europe. I ended up needing a lot of things since I was starting from scratch, and many shops had only parts of my list. A UK store called [Pi Hut](https://thepihut.com/) ended up being the best fit, notably with some really cool arcade buttons. I placed an order, and waited patiently…

I made a lot of mistakes along the way, probably more than I can remember, so I won’t write it all chronologically. Instead, I’ll mostly describe what I ended up with, and try to sprinkle some tips&tricks (for myself, notably…) here and there. I’ll split this series into 3 posts:

  - [Part 1: The Hardware]({% post_url 2022-01-10-picoarcade-hardware %}). This is very specific to what I had to do to make this project work, your mileage will definitely vary for other applications.
  - [Part 2: The Software]({% post_url 2022-01-11-picoarcade-software %}).
  - [Part 3: The Games]({% post_url 2022-01-12-picoarcade-games %}). PicoArcade is a platform for building games. I've gathered a dozen ideas for now, and more will hopefully come with time.