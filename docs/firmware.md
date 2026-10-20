# Firmware

## SoC and memory

The firmware is built on the Silicon Labs Matter SDK. The boot log shows a `silabs` platform tag, Bluetooth stack v9.0.1 and RAIL v2.18.1.

<!-- TODO: exact SoC part, internal/external flash, sizes -->

## Dumping

<!-- TODO: method, tools, read-protection status -->

## Boot log

The device prints boot messages on the [serial header](pinout.md#serial) at 115200 baud. A full log from an already-commissioned device is in [boot.log](boot.log).

Network identifiers have been replaced with placeholders such as `<compressed-fabric-id-1>` and `<mesh-local-prefix>`. These are fabric/node IDs, Thread addresses and partition ID, and the controller hostname.

Notable lines:

- `DUBBELKISEL 30W EU starting` is the device name/model.
- `Init CHIP Stack` / `Initializing OpenThread stack` show it is Matter over Thread.
- `Setting OpenThread device type to ROUTER` means it is a mains-powered Thread router.
- `Fabric already commissioned. Disabling BLE advertisement` means BLE is only used for commissioning.
- `Reset info: 0x0B (BRO)` was the reset cause recorded for this boot.
- `Starting the periodic query timer, timeout: 86400 seconds` means the OTA requestor checks for updates once a day.

## CLI

A CLI is available on the serial header after boot. The prompt is `matterCli>`. This is the standard Matter SDK shell. A session exploring it is in [cli.log](cli.log).

### Commands

| Command | Description | Notes |
| --- | --- | --- |
| `help` | List top-level commands | |
| `version` | Software version | Returns `CHIP 0.0.0`, so the build doesn't set a version string |
| `config` | Dump/set device configuration | Prints vendor/product/hardware IDs, then errors with `CHIP:0x0000002D` |
| `device factoryreset` | Factory reset | |
| `onboardingcodes` | Dump onboarding (pairing) codes | `none\|softap\|ble\|onnetwork [qrcode\|qrcodeurl\|manualpairingcode]` |
| `ble adv start\|stop\|state` | Control BLE advertising | See [Radio](radio.md#bluetooth) |
| `ota` | OTA commands | |
| `dns` | DNS client commands | |
| `stat peak\|reset` | Peak system resource usage | |
| `tracing help\|list\|watermarks\|flush` | Silicon Labs time tracing | |
| `log`, `rand`, `echo`, `exit` | Utilities | |
| `otcli` | OpenThread CLI passthrough | Errors with `CHIP:0x0000002F`, so it's probably compiled out |
| `silabs` | Silicon Labs CLI passthrough | Errors with `CHIP:0x0000002F`, so it's probably compiled out |

### Device identity

From `config`:

| Field | Value |
| --- | --- |
| VendorId | 4476 (`0x117C`) <!-- TODO: confirm assignment to IKEA in the CSA DCL --> |
| ProductId | 36891 (`0x901B`) |
| HardwareVersion | 2 |

### Resource usage

`stat peak` on a commissioned device, idle, after one controller subscription was resumed:

| Resource | Peak |
| --- | --- |
| Packet buffers | 3 |
| Timers | 7 |
| TCP endpoints | 0 |
| UDP endpoints | 1 |
| Exchange contexts | 2 |
| Unsolicited message handlers | 4 |
| Platform events | 0 |
| Heap allocated | 34,960 bytes |

The heap figure only gives a lower bound on RAM, so it doesn't pin down the SoC variant.

<!-- TODO: explore `ota`, `dns`, `log` -->

## OTA updates

The device runs a Matter OTA requestor that queries for updates every 24 hours (86400 s).

<!-- TODO: observed firmware versions, OTA provider -->
