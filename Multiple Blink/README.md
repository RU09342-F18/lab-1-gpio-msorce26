# Multiple Blink

Sample code by TI, edited by Michael Sorce
Last updated: 9/19/18

The purpose of the multiple blink programs in this section is to blink two LED on the dev board at two different frequencies.

Each programs begins be including the main msp430 header file so it can access the processors standard library. The MSP432 program also includes the standard integar header file so that it can use an unsigned 32bit int later on.

Next, a line of code is run to stop the watchdog timer. This allows us to run an infinite loop in our code without the watchdog timer thinking it is an error.

For both processors, P1DIR is set to  the proper pins so that the desired LEDs are set to output pins. For the G2, P1DIR is ORed with 0x41 to turn the LED pins to outputs. For the MSP432, P1DIR BIT0 is set to 1, and P2DIR BIT0 and BIT2 are set to 1. P1DIR set one stand alone led to an output, and P2DIR sets the red and blue of an RGBLED to outputs (making a purple light when both on).

Both programs use an infinite loop (G2 uses for loop, MSP432 uses while loop) to toggle the LED infinitely. To toggle the LEDs at different rates, the same code used in the single LED blink is ustilized. The P2outputs are toggled 3x more often then the P1outputs.

A delay is used in the loop to keep the LED from toggling too fast for the observer to see. The rate that the LED is flashing can be increased by increasing the clock cycle delay in the loop. By having these delays properly placed between toggling the LED, it causes them to blink at different frequencies.

*Note* The MSP432 has slightly different syntax than the G2. This can be seen in setting the watchdog timer, as well as the name for ports such as P1DIR and P1->DIR.
