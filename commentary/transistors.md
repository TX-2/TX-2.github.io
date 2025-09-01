# Transistors in the TX-2

The TX-2 was created in order to determine how reliable transistors
would be as the basis of a computer.

## Applications of Valves and Transistors

Much of the TX-2's logic was constructed from transistors, for example
logic gates, flip-flops (see the "LOGIC" section of [Fadiman58]),
address decoding, lamp supply, and some of the circuits around core
memory.

However, there were still circuits using valves. The 2.5MHz clock used
Sylvania type 6888 tubes, for example.

The TX-2 used mainly Philco L-5122 and L-5134 Surface-Barrier
transistors.  Philco 2N501 micro-alloy diffused-base transistors (or
L-5432) were used for high frequency, high current applications.  One
such use was the X-adder.  Use of this part made it possible to reduce
the carry time for the X-adder circuit to 0.42 microseconds for 18
digits.

## Transistor Parts Used

The appendix of [Fadiman58] lists the transistor parts used in the TX-2:

| Type Number  |  Manufacturer    | Equivalent Number  | Remarks |
| ------------ |  --------------  | -----------------  | ------- |
| GA-52830     | Western Electric |                    | PNP Core Switch |
| GT-901       | Sylvania         |                    | NPN Core Switch |
| H-3          | Minneapolis Honeywell | | PNP Power |
| H-6          | Minneapolis Honeywell | 2N539 | PNP Power |
|L-5122 |  Philco and Sprague | 2N240 (Similar) | PNP SBT |
|L-5134 |Philco and Sprague |  2N393 (Similar) | PNP Micro-alloy SBT |
|L-5409| Philco |2N501| PNP Micro-alloy diffused-base transistor - Very high speed switch.|
|L-5432| Philco ||PNP Micro-alloy diffusedbase transistor - High voltage, high power 2N501.|
|2N123| General Electric| | PNP Medium Speed|
|2N167| General Electric| |  NPN Audio, Grown Junction|
|2N174| Delco| |PNP Power|
|2N188A| General Electric|| PNP Audio |
|2N241A| General Electric| |PNP Audio |
|2N321| General Electric|| PNP Audio|
|2N357 |General Transistor|| NPN Medium Speed|
|2N396| General Electric| 4JD1D1| PNP Medium Speed|
|2N534| Philco|| PNP Audio, Miniature|
|2N536| Philco|| PNP Audio, Miniature|
|2N580| RCA ||PNP Medium Speed|
|2N635| General Electric|| NPN Med|
|4JD1A21|General Electric| 2N43 (Similar) | PNP Audio |

## Logic Levels

The TX-2 used ground and -3V as logic levels, but what these
represented in any given output depended on the polarity of the input
[Fadiman58].

Flip-flops specifically were said to be in the "ONE" state when the
"ONE" output was at -3V.

## References

The information in this page is taken from the following materials.
These are (linked from the [Documentation](documentation.md) page).

| Mnemonic | Reference |
| -------- | --------- |
| Fadiman58| A Discussion of the Circuitry Used In the Lincoln TX-2 Computer, Jonathan R. Fadiman.|
| Best57   | Memory Units in the Lincoln TX-2, Richard L. Best |
