# Simple Blink

The purpose of the simple blink programs in this section is to blink an LED on the dev board at any speed, as long as it has a 50% duty cycle (on half time, off half).

Each programs begins be including the main msp40 header file so it can access the processors standard library.

Next, a line of code is run to stop the watchdog timer. This allows us to run an infinite loop in our code without the watchdog timer thinking it is an error.

For both processors, P1DIR is set to 0x01 to turn the P1.0 port to an output, which is an LED for both boards. For the G2, P1DIR is ORed with 0x01, but for the FR the macro BIT0 is ORed with P1DIR. Both lines do the same thing.

The FR has an additional line of code (P1OUT &= ~BIT0) which clears the output latch for a defined power on state.

Both programs use an infinite loop (G2 uses do-while, FR uses while) to toggle the LED infinitely. To toggle the LED, P!OUT is XORed with BIT0. This will continuously flip the last bit in P1OUT, therefore toggling the LED.

A delay is used in the loop to keep the LED from toggling too fast for the observer to see. The rate that the LED is flashing can be increased by increasing the clock cycle delay in the loop.
