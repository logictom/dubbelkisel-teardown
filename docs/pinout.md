# Pinout

## Test points

| Pad | Signal | Notes |
| --- | --- | --- |
| <!-- TODO --> | | |

## Debug interfaces

The headers have no pin 1 marking. In this documentation, pin 1 is the pin nearest the top side of the board, and the same convention is used for both headers.

### SWD

A full SWD header is broken out on a 5-way 0.1" (2.54 mm) header.

| Pin | Signal |
| --- | --- |
| 1 | 3V3 |
| 2 | SWDIO |
| 3 | SWCLK |
| 4 | RESETn |
| 5 | SGND |

<!-- TODO: photo showing orientation; whether 3V3 can power the board from the probe -->

### Serial

There is a 2-pin serial header carrying TX and RX only. It has no ground pin, but ground is easy to reach on the SWD header next to it (pin 5, SGND).

| Pin | PCB legend | Connect to adapter |
| --- | --- | --- |
| 1 | Rx | RX |
| 2 | Tx | TX |

The PCB legend is labelled from the adapter's point of view, so wire it straight through: legend Rx to adapter RX, and legend Tx to adapter TX. Pin 1 is the device's output and pin 2 is its input.

- **Settings:** 115200 baud, 3.3 V logic
- **Adapter:** works with a 3.3 V USB FTDI cable
- **Output:** boot messages, plus an interactive CLI

See [Firmware](firmware.md#boot-log) for the boot output and CLI.

## Traced connections

<!-- TODO: GPIO → peripheral mapping -->
