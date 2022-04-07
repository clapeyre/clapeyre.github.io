---
layout: post
title:  "PicoArcade Part 3: Games"
date:   2022-01-12 12:00:00
categories: 
post_url: pico-arcade-games
---

This is part 3 of a series on the PicoArcade project. Check out the [main page]({% post_url 2022-01-09-picoarcade %}) to see the full series.

# Interacting with the board

While in a game, the board is simply seen as a 4 x 4 array of *both* LEDs and
buttons. They are numbered from 0 to 15, vertically and from left to right
(check out the layout image on the [hardware page]({% post_url
2022-01-10-picoarcade-hardware %}) for a visual guide).

The LEDs have 2 states: on and off. The buttons don't really have "states";
instead, there are two flag buffers of length 16, all set to False. They can
easily be accessed using two `Arcade` attributes: `arcade.pressed` and (you
guessed it) `arcade.released`. An asynchronous function runs perpetually to
detect button events, with debouncing. Buffers can be reset at any time with
the `.reset_pressed()`, `.reset_released()` and `reset_flags()` methods.

As the finishing touch, a buzzer is available to play (usually asynchroneously)
some simple tones.

That's pretty much it, all games have to work with these functions to produce
the desired behavior. From that, I built a series of games, some very easy (I
have a 2 year old that loves to play with the lights and sounds) and some
tougher. I also tried some single and some 2-player variations, when I could.

## Grownup single-player games

I started with some simple games, the first being directly inspired by
[@ghidraninja's setup](https://twitter.com/ghidraninja/status/1422900329369178113?s=21),
and then gradually implemented some new ideas as they came.

### Light chaser

The light chaser is simple: a timer (20s), 3 of the 16 LEDs lit at any point,
hitting an LED turns it off. At the end of the timer, your score is the number
of lit LEDs you smashed.

Interestingly, I gave this to some sneaky thinkers, who quickly gamed it by
pressing everything repeatedly like mad. So I then added a "hardcore" mode,
where unlit button presses count negatively towards the score.

### Sequence

This basic game uses only 4 buttons. Each button has a dedicated sound. The
board produces a random sequence incrementally, and you must follow along by
reproducing it as it goes. So it plays one, which you repeat, then it replays
the same plus a new one, and you repeat them both in order, and so on. It get's
tough quickly, the current record (with a "lucky" sequence) is 16.

### Memory

This one was fun to code. It's based on the "Memory" game, where you turn cards
facing down around in pairs, and keep matching pairs facing up. Except here,
each button produces a short melody. 16 buttons means that 8 melodies are
randomly affected to the buttons. This is a bit tough, and while you can play
solo, it's also fun to play with someone else.

## Grownup 2-player games

Under construction

## Child and baby games

Under construction

### Symmetry (ooh, goodie)
### Baby stuff

## Utilities
Under construction
### Buzzer (Fake…ish?)
### Blinky lights
