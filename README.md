# Desk Clock Timer

Compact Bluetooth desk clock that combines Pomodoro timing, and media display.

- Full-speed USB interface for time sync and alarm setup.
- Bluetooth connectivity for timer and media updates.
- E-ink display to show the clock, Pomodoro timer, and live Spotify/media information, driven directly by the STM32.
- 4200 mAh lithium battery rechargeable via USB-C for portability.

<details>
  <summary>PCB render coming soon</summary>
</details>

## Design Notes

Design notes and requirements are tracked in the [Public Notes](Public%20Notes) folder:

- [1 - Overall Architecture](Public%20Notes/1%20-%20Overall%20Architecture.md) - High-level system diagram and goals.
- [Inputs](Public%20Notes/Inputs.md) - Bluetooth, wired USB, and button input requirements.
- [On Device](Public%20Notes/On%20Device.md) - Power, display, and controller requirements.
- [Outputs](Public%20Notes/Outputs.md) - Output features.

## Altium Project

Schematics, layout, and fabrication outputs live in the [`altium/`](altium) folder.
The full schematic set is exported to [`Desk-Clock-Timer.pdf`](altium/Desk-Clock-Timer.pdf), and Gerber/drill files are available under `Project Outputs for Desk-Clock-Timer`.
