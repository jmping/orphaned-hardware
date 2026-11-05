# Open questions and research leads

These are hypotheses to check, not instructions to probe a live mains circuit.

## Architecture

- Which LPC4370 boot mode is selected, and where is its executable firmware stored?
- Is any external nonvolatile memory fitted, perhaps on the inaccessible PCB reverse or elsewhere on the assembly?
- Which documented host interface connects the LPC4370 to the Sterling-LWB module on this board? Do not infer UART/SDIO from generic module capabilities alone.
- Are any test pads connected to a documented, safe diagnostic or programming interface? None are mapped.
- What signal-processing or power-control functions are performed by the repeated short-marked ICs?

## Home Assistant objective

The most useful outcome would be independently readable, **non-safety-critical** data such as voltage or frequency. To establish feasibility, first determine:

1. Whether original firmware exposes measurements at all.
2. Whether access requires a vendor account or cloud service.
3. Whether a documented local interface exists.
4. Whether integration is possible without compromising electrical safety or needing extensive new firmware.

A plug-in voltage-sensing device should **not** be assumed to measure whole-house watts or kWh without current sensing.

## Useful research starting points

- [NXP LPC4300 MCU family documentation](https://www.nxp.com/products/processors-and-microcontrollers/arm-microcontrollers/general-purpose-mcus/lpc4300-arm-cortex-m4-m0:LPC4300)
- [Home Assistant community search for Ting](https://community.home-assistant.io/search?q=Ting)
- [GitHub repositories search: Whisker Ting Home Assistant](https://github.com/search?q=whisker+ting+home+assistant&type=repositories)

Community integrations, if any, need to be evaluated for cloud dependence, maintenance status, authorization, and compatibility with a discontinued device. Their existence does **not** prove a standalone local connection is possible.

## Status

- No verified serial, SWD, JTAG, or test-pad pinout.
- No firmware dump or cryptographic analysis.
- No captured network protocol or recovered measurement stream.
- No validation of a local Home Assistant data path.

Contributions that replace guesses with **cited datasheets or reproducible, safely obtained evidence** would be especially useful.
