# Whisker Labs Ting — teardown and reuse notes

**Status:** documentation only; no local integration or firmware modification demonstrated.

This is a collection of observations from a teardown of a formerly supported Ting plug-in electrical-monitoring device. The original unit reportedly operated before service/support was discontinued. The aim is to see whether *non-safety-critical* measurements (for example, line voltage or line frequency) could eventually be made available locally, perhaps in Home Assistant.

These notes are not a schematic, a verified pinout, or an implementation guide. Distinguish observed markings from inferred functions. See [components.md](components.md), [open-questions.md](open-questions.md), and [safety.md](safety.md).

## Observed hardware

- PCB marking: **TING REV 17/2021-10-15**.
- Main processor marking identified as **NXP LPC4370FET100** (LPC4370 MCU family).
- Shielded wireless module label read as **Laird Sterling-LWB**, part **453-00012 R1** (part identification from the module label; wireless interface to host is not mapped).
- A nearby IC is marked **LVC125A**; probably a 74LVC125A-family quad tri-state buffer, **not** firmware flash.
- Edge-mounted tactile switch marked **SW401**, contacted by the case's external button. Its electrical function is unknown.
- Numerous labeled manufacturing test pads; **none electrically mapped**.
- A section populated with multiple small ICs marked `17MD`, `K127`, and other short codes; their functions are not identified.
- AC power-conversion and analog-looking circuitry; topology and electrical isolation are not verified.

## Working hypothesis (unverified)

The LPC4370 may perform measurement and signal processing, while the Sterling-LWB module handles wireless communications. The available photos do **not** establish how these chips communicate, where the MCU boots from, or whether local measurement data is exposed.

Ting's original fire-risk analysis must **not** be equated with generic voltage or noise readings. No recovered sensor output or local protocol has yet been demonstrated.

## What might be reusable?

- Voltage measurements or frequency trends, **if** existing firmware exposes them through a usable interface.
- Read-only observation of normal network traffic or software behavior, **if** the unit is still operable and authorized.
- Documentation useful to future investigators even if repurposing is impractical.

No evidence presently establishes a local API, MQTT output, UART stream, accessible debug port, flash-extraction path, or Home Assistant integration that can work without the original service.

## Scope and privacy

This public entry intentionally omits unit-specific serial numbers, MAC addresses, network identifiers, account details, raw communication captures, and photographs that may expose such details. It contains no firmware dumps, passwords, or secrets. General component models and board revision are included to make the notes searchable.

## Suggested low-effort next steps

1. Search for independent community research or existing integrations before attempting hardware modification.
2. Review LPC4370 boot/debug documentation and Sterling-LWB host interface documentation.
3. If an intact unit still works, investigate whether any **documented or observable** data is available without opening or probing energized mains circuitry.
4. Stop if the only apparent path involves extensive firmware reverse engineering or unsafe bench work.

**Safety:** see [safety.md](safety.md). This device is not validated as a replacement fire alarm, electrical protection device, or safety monitor.
