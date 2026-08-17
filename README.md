# Desk Clock Timer

Compact STM32-controlled Bluetooth desk clock powered over USB-C with a [4200 mAh lithium battery](https://www.amazon.ca/4200mah-Rechargeable-Lithium-Replacement-Electronic/dp/B095BP7V1D?th=1) for portability. It connects to Windows/Linux over USB and Bluetooth for time sync, alarm setup, and media data, and drives a [7.5 inch E-ink display](https://www.waveshare.com/product/7.5inch-e-paper-b.htm) to show the clock, Pomodoro timer, and live Spotify/media information.

> Assembly and firmware are in progress. Images coming soon.

## Architecture

```mermaidE-ink display
flowchart TD
	subgraph Inputs
	I1("`Laptop/Computer (wired)`")
	I2(Bluetooth)
	end

	subgraph PCB
	D1(Power)
	D2(Display)
	D3(Controller)
	end

	subgraph Outputs
	FO1(Clock)
	FO2(Pomodoro Timer)
	FO3(Media Display)
	end

	Inputs --> PCB --> Outputs
```

## Hardware Design Notes

### Layer Stack-Up

The board is 2-layers. Routing is split between the two layers and the empty space is filled with a 
GND pour.

### 2.4 GHz Antenna

The board uses a meander PCB antenna for the 2.4 GHz Bluetooth link. The antenna is designed to 
present a 50 ohm impedance directly to the feedline, so the transceiver sees a clean match across 
the 2400–2480 MHz operating band.

### RF Signal Routing & Integrity

- The RF trace is routed as a coplanar waveguide, with the
  reference ground on the layer directly beneath the trace to maintain the 50 ohm characteristic
  impedance.
- Shielding vias are placed along the RF trace to stitch the top-side ground
  pour to the inner ground plane. These vias form a cage around the trace that reduces
  coupling and keeps the impedance consistent along the run.
- The antenna keep-out zone is clear of copper pours and ground planes to avoid detuning.

### E-Ink Boost Converter

The E-ink display requires a higher drive voltage than the 3.3 V rail. A **boost
converter** steps the battery/rail voltage up to the display's operating level. The boost
switching node and inductor loop are kept tight, short and away from the RF traces to minimize 
EMI and switching losses.

### USB-C Differential Pair

The USB connection is routed as a 90-ohm differential pair for the D+/D− signals. It is length matched 
and tightly coupled.

## Altium Project

Schematics, layout, and fabrication outputs live in the [`altium/`](altium) folder.
The full schematic set is exported to [`Desk-Clock-Timer.pdf`](altium/Desk-Clock-Timer.pdf), and Gerber/drill files are available under `Project Outputs for Desk-Clock-Timer`.
