# Hardware

## Opening the device

<!-- TODO: tools needed, clips/screws, photos -->

## PCB overview

<!-- TODO: front/back photos with annotations -->

### Outputs

The 8 outputs are wired in parallel and driven by a single switching FET. They cannot be controlled individually; they all switch on and off together.

The FET is marked `LT1000N04`.

<!-- TODO: confirm manufacturer/datasheet, gate drive, output voltage -->

### Wireless module

The device uses a module with a PCB antenna. The module's shield can is marked with a QR code. It decodes to the same data as the QR code on the outside of the casing, followed by a semicolon and some extra digits.

<!-- TODO: module/SoC identity, photo -->

### Debug header

A full SWD header is broken out on a 5-way 0.1" header. There is also a separate 2-pin serial header. See [Pinout](pinout.md#debug-interfaces).

## Bill of materials

| Ref | Markings | Part | Function |
| --- | --- | --- | --- |
| <!-- TODO --> | `LT1000N04` | <!-- TODO --> | Output switching FET |
| <!-- TODO --> | | | |

## Power

<!-- TODO: supply/battery, regulators, measured current draw -->
