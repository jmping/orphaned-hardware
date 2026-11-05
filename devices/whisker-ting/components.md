# Component and marking inventory

The entries below record markings read from photographs or transcribed during the teardown. **Marking confidence is not the same as functional identification confidence.** References to exact PCB nets, test-pad functions, and debug pin assignments have not been established.

| Location / marking | Observation | Identification status |
| --- | --- | --- |
| PCB silkscreen | `TING REV 17/2021-10-15` | Observed board revision/date marking |
| Main IC | `LPC4370FET100` | NXP LPC4370 processor identification; high confidence |
| Shielded RF module | `STERLING-LWB`, `453-00012 R1` | Laird Sterling-LWB module; label read from photograph |
| Antenna | `Inventek W24P-U-NT` | Antenna marking; **not** the identity of the wireless module |
| Small logic IC near MCU | `LVC125A` followed by apparent `YM24911`, `TXD21`, `09D` | Likely 74LVC125A-family logic buffer; exact manufacturer/lot decoding unverified |
| Pushbutton | `SW401` | Tactile switch physically reached by case button; reset/provisioning function unverified |
| Nearby test pads | `TP4`, `TP5`, `TP6` | Visibly adjacent to SW401; **no electrical connection proven** |
| Other test pads | Multiple `TP` designators | Unmapped; their being test pads does not establish UART, JTAG, or SWD |
| Small ICs | Three marked `17MD` (as transcribed) | Part numbers/functions unknown |
| Small ICs | Three marked `K127` (as transcribed) | Part numbers/functions unknown |
| Additional small devices | `M7Q`, `LTFRM`, `5CL`, `FR` (as transcribed) | Short package codes; ambiguous without package, manufacturer, and circuit context |
| Four passives | `1543` | Could encode 154 kΩ **if** standard four-digit SMD resistor marking is being used; value unverified |
| Power section | Magnetics, inductors, electrolytic capacitors, rectifier-looking parts | Exact power architecture, grounding, and mains isolation **unverified** |

## Corrections and caveats

- A prior visual identification described the switch as `SW404`; a closer image supports **`SW401`** instead.
- The `LVC125A` part was initially suspected to be external flash. This was **not supported** once the marking was read; no external firmware storage has been identified.
- A visible Inventek marking belongs to the **antenna**, not necessarily the RF module. The shield label identifies the **Laird Sterling-LWB** module.
- The `17MD`/`K127` devices *might* be part of repeated analog or power-related circuits, but no specific purpose should be assigned from package markings or proximity alone.
- An apparent isolation transformer is **not proof** that exposed MCU ground or any test pad is safe to contact while connected to AC mains.
