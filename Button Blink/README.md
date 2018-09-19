# Button Blink

The purpose of the button blink programs in this section is to blink an LED on a dev board when an observer presses an external button.

Each programs begins be including the main msp430 header file so it can access the processors standard library. 

Next, a line of code is run to stop the watchdog timer. This allows us to run an infinite loop in our code without the watchdog timer thinking it is an error.

For both processors, P1DIR is set to  the proper pins so that the desired LEDs are set to output pins. For the G2 and F5529 P1DIR = BIT0 sets the desired LED pin to an output. By default, the pins that are connected to the buttons are set to 0, so it does not need to be manually changed.

Although, unlike LEDs, buttons need a pull up resistor enabled on them for their logic to work. Buttons use reverse logic, so when the button is not pressed the pull up resisor (connected to vcc) makes the input pin a 1 (or logic high). When the button is pressed, a path to ground from the vcc is provided, bypassing the input pin, resulting in an input of 0 (or logic low). To set this pull up resistor, P1REN is set to 1 at the pin at which the button is connected (BIT3 for G2, BIT1 for F55). Additionally, P1OUT has to be set equal to the button pin to set it as a pull up resistor, as opposded to a pull down resistor.

Both programs use an infinite loops to check if the button is pressed. An if statement within the infinite loop checks if the proper button is pressed, and if so changes the state of the LED using the XOR as seen in previous programs.

A delay is used in the loop to keep the LED from toggling too fast. If the delay is too low the button may turn on and off again on 1 press and appear not to work.

The button is configured continuously, so if the button is held down, the LED will toggle at the rate the delay allows for until released.
