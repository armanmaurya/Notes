---
tags:
  - Microcontroller
---
Most programs use interrupts in their regular execution. The purpose of the microcontroller is mainly to respond to changes in its surrounding. In other words, when an event takes place, the microcontroller does something... For example, when you push a button on a remote controller, the microcontroller will register it and respond by changing a channel, turn the volume up or down etc. If the microcontroller spent most of its time endlessly checking a few buttons for hours or days, it would not be practical at all.

This is why the microcontroller has learnt a trick during its evolution. Instead of checking each pin or bit constantly, the microcontroller delegates the ‘wait issue’ to a ‘specialist’ which will respond only when something attention worthy happens.

The signal which informs the central processor unit about such an event is called an INTERRUPT.