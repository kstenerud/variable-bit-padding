Variable Bit Padding
====================

A scheme for encoding an arbitrary number of padding bits in a field or bit stream.


### Features

* Padding can be decoded from the left or right side equally.
* Padding can be 0-based (filled with `0` bits) or 1-based (filled with `1` bits).



Fields
------

Variable Bit Padding is made up of the following sub-fields:

* The **padding initiator bit (PIB)** determines if there will be more than 1 bit of padding.
* The **sentinel bit** is the bit value that marks the end of the padding when there is more than 1 bit of padding.
* The **filler bit** is the bit value used as filler in between the PIB and the sentinel when there are more than 2 bits of padding.

The values are encoded differently, depending on whether you are using 0-based or 1-based encoding:

| Base    | PIB (off) | PIB (on) | Sentinel | Filler |
| ------- | --------- | -------- | -------- | ------ |
| 0-based |         0 |        1 |        1 |      0 |
| 1-based |         1 |        0 |        0 |      1 |

Note: there is always a minimum of 1 bit of padding (or if you prefer, think of the PIB as as a padding on/off flag instead).



Examples
--------

| Padding Count | Encoding (0-based) | Encoding (1-based) |
| ------------- | ------------------ | ------------------ |
|             1 | `0`                | `1`                |
|             2 | `11`               | `00`               |
|             3 | `101`              | `010`              |
|             4 | `1001`             | `0110`             |
|            10 | `1000000001`       | `0111111110`       |



License
-------

Copyright 2019 Karl Stenerud

Specification released under Creative Commons Attribution 4.0 International Public License https://creativecommons.org/licenses/by/4.0/
