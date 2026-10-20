# Hacking

## Home Assistant integration

<!-- TODO: ZHA / Zigbee2MQTT / Matter support, quirks -->

## Custom firmware

<!-- TODO: feasibility, existing projects, flashing procedure -->

## Serial CLI access

Anyone with access to the [serial header](pinout.md#serial) gets an unauthenticated `matterCli>` shell. From it they can:

- dump the onboarding/pairing codes (`onboardingcodes`)
- start BLE advertising (`ble adv start`)
- factory reset the device (`device factoryreset`)

This needs the case opened, so it isn't a remote risk. It is useful for recovery, and for re-pairing a unit whose label has been lost.

## Ideas / open questions

<!-- TODO -->
