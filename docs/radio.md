# Radio

## Protocol

The device is **Matter over Thread**, with BLE used for commissioning. The radio is a Silicon Labs-based module with a PCB antenna (see [Hardware](hardware.md#wireless-module)).

- Thread role: router
- Matter operational port: UDP 5540
- Multi-admin: the boot log shows the device commissioned into two fabrics at the same time

### Matter endpoints

Clusters seen in the boot log:

| Endpoint | Cluster | Name |
| --- | --- | --- |
| 0 | 0x001D | Descriptor |
| 0 | 0x001F | Access Control |
| 0 | 0x0028 | Basic Information |
| 0 | 0x002A | OTA Software Update Requestor |
| 0 | 0x0030 | General Commissioning |
| 0 | 0x0031 | Network Commissioning |
| 0 | 0x0033 | General Diagnostics |
| 0 | 0x0035 | Thread Network Diagnostics |
| 0 | 0x003E | Operational Credentials |
| 0 | 0x003F | Group Key Management |
| 1 | 0x0003 | Identify |
| 1 | 0x0004 | Groups |
| 1 | 0x0006 | On/Off |
| 1 | 0x0008 | Level Control |

Endpoint 1 exposes On/Off and Level Control, so the [single output FET](hardware.md#outputs) is presumably dimmed with PWM. This has not been verified yet.

## Bluetooth

BLE advertising is off once the device is commissioned. With advertising turned back on, the GATT Device Information service reports:

| Characteristic | Value |
| --- | --- |
| Manufacturer Name | `Silabs` |
| Model Number | `Blue Gecko` |

These look like the default strings from the Silicon Labs SDK's GATT configuration, which IKEA hasn't customised. They confirm the Silicon Labs platform but don't identify the exact SoC. Blue Gecko is a Silicon Labs family name, not a specific part.

Advertising can be started from the [serial CLI](firmware.md#cli) with `ble adv start`.

<!-- TODO: advertised name, other GATT services -->

## Pairing behaviour

<!-- TODO: reset/pairing procedure, observed join process -->

## Captures

<!-- TODO: sniffer setup, notable clusters/endpoints/messages -->
