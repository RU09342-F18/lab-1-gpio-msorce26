# Offboard Blink

The purpose of the offboard blink programs in this section is to show that the processor can still be used when disconnected from its dev board.

The program downloaded on the G2553 is the same MSP430G2553 program used in the multi_blink section of this lab. Explanation of that code can be seen there.

A circuit diagram can be seen in the Lab1_Offboard_Blink_Circuit.png. In this image it shows the mandatory connections needed to make the program work seperated from the dev board. Pin1 of the MSP430G2553 needs to be connected to VCC and pin20 needs to be connected to ground. The resert pin needs to be connected to vcc through a 47kohm resistor, and groud through a 1nF capacitor. The orientation of this connection can better be understood through the circuit diagram.

Finally, the pins that are usually automatically connected to LEDs need to be manually connected. Pin 2 and 14 on the processor are connected in series with a 1kohm resistor, LED and ground.

This set up allong with the pre-programmed processor allows for the two LEDs to blink at different frequencies as in the multi_blink programs.
