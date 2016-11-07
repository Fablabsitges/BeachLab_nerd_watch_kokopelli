# Assembly nerd's watch

## Why Assembly
The arduino code only has a small glitch. It is so inefficient that the battery only last for 3 days. So I am going to rewrite from scratch the nerd's watch code in Assembly. I will compare it against the arduino code in terms of power consumption and .hex file size. I cannot imagine anything better than assembly to code this project. So simple, so basic, so nerd. Let's derive the principles.

## The Principle
The code is just a counter that keeps track of the time in 2 registers. When the button is pressed it blinks according to the time in binary code. It blinks 2 sequences of 4 numbers like `1100 0011` which translates into `8+4+0+0=12` and `0+0+2+1=3` and `3x5=15` so it is 12:15. The first number  are the hours and ranges from 1 to 12, so we need to store 12 values in a register `hh`. The second number are the minutes, the watch has a 5 minutes precision so ranges from 1 to 12, again 12 values that we need to store in a `mm` register. When the `mm` reaches 12, it overflows and adds another number to the `hh` register.

The clock runs at 1Mhz internal RC clock. That means 1 million clock cycles per second. We don't need that much so using the clock divider 1024 
