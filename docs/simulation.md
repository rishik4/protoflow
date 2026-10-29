# Simulation

ProtoFlow can simulate your schematic with ngspice, a SPICE engine that runs on your own computer. It turns the schematic into a netlist for you, runs the analysis, and plots the results, so you can check a circuit before you build it.

Simulation is in beta. The first time you run it, ProtoFlow shows a **Simulation Beta Notice**; click **Continue** to go on.

## Run a simulation

1. Open the schematic you want to simulate.
2. Press <kbd>F5</kbd>, or click **Run Simulation** in the schematic toolbar. ProtoFlow opens the **Simulation** panel and runs the circuit with the last analysis you used. The first time, that is a short time response.
3. Read the results in the panel. **WHAT I FOUND** lists rail voltages, supply current and anything that looks wrong.
4. Click any wire on the schematic to add a probe on it.

You can also open the panel without running it: search for **Open Simulation Panel** in the command palette (<kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>), or use **View > Simulation**.

While the circuit is running, the button reads **Stop Simulation** and shows progress. After a run, the panel button reads **Run Again**.

To leave simulation mode, press <kbd>F5</kbd> again or click the × on the **Simulation Mode Active** card at the bottom of the canvas. This clears the results and probes. Results are also cleared when you change the circuit or switch tabs. A run stops on its own after 60 seconds.

## Before the run: parts that can't be simulated

ProtoFlow checks every part first. If some parts have no simulation model, a dialog lists them under **Not simulated**, **Approximated (upgradeable)** and **Behavioral proxies**. For each one you can:

- **Create sim object**: let the AI write a model for the part from its datasheet. How many you can create depends on your plan. See [pricing](https://www.protoflow.ai/pricing).
- **Use generic behavioral proxy**: use a simple stand-in model.
- **Exclude from simulation**: leave the part out.

Click **Run without N parts** to simulate the rest of the circuit anyway. The panel also shows how many parts simulate, with a **Fix** or **Details** link.

## Choose the analysis

Click **Show advanced settings** in the panel header to see the analysis settings.

| Analysis | Label | Settings | Use it for |
|---|---|---|---|
| Transient | **Time** | **Step**, **Stop**, **Start** (seconds) | Waveforms over time |
| AC | **Freq** | **Sweep** (decade, octave or linear), **Points**, **Start**, **Stop** (Hz) | Frequency response of filters and amplifiers |
| DC sweep | **DC sweep** | **Source** (for example V1), **Start**, **Stop**, **Step** | Output while a source is swept |
| Operating point | **Bias** | None | Steady DC voltages and currents |

Type numbers as plain or scientific values, such as `0.000001` or `1e-6`. SPICE suffixes like `1u` or `10k` are not read in these fields.

For an AC analysis, give a source an AC value, for example `DC 0 AC 1`. The chart shows the real part of the result on a logarithmic frequency axis.

## Sources and models

### Power and sources

- Power symbols that nothing else drives become ideal DC supplies. The voltage comes from the symbol name, such as +3V3 or 5V. The panel lists these as **Assumed ideal supplies**.
- For a voltage or current source part, set the waveform in its **Value** field: a number for DC, or `DC`, `AC`, `PULSE(…)`, `SIN(…)`, `PWL(…)` or `EXP(…)` as in SPICE.

### Built-in models

ProtoFlow matches common parts by value, part number or symbol, including:

- Generic diodes, LEDs, NPN and PNP transistors, MOSFETs and an ideal op-amp
- Diodes such as 1N4001 to 1N4007, 1N4148, Schottky (1N5817, SS14, BAT54) and Zener
- Transistors such as 2N2222, 2N3904, BC547, 2N7002, AO3400 and IRLZ44N
- NE555, op-amps such as LM358, TL072 and NE5532, regulators such as AMS1117, 7805 and LM317, and PC817 optocouplers

### Your own models

Symbols can carry KiCad-style simulation fields. In the [symbol editor](symbol-editor.md), open **Advanced symbol properties** and the **Simulation model** tab to pick a built-in SPICE model or load a SPICE library, and to map pins. **Exclude from simulation** in the symbol properties leaves a part out.

## Probes

After a run, click a wire to add a voltage probe on it. Click the wire again, or click the probe marker, to remove it. Each probe gets a color, shows its value on the canvas, and is listed in the **Probes** legend at the bottom left. **Clear N probes** in the panel removes them all. Probes stay in place when you run again.

The panel can also color the schematic while simulating. Toggle **Voltage colors**, **Component values**, **Current flow (conventional)** and **LED glow (lit LEDs light up)**. Hover a part to see its voltage, current and power.

## Waveforms

The chart plots your probes. Each plotted signal has a pill above the chart; click a pill to remove that trace. Click **Signals** to pick from every signal, grouped into power rails, named nets, currents, unnamed nets and model internals.

On the chart:

- Hover to read values at the cursor. Click to pin a reference cursor and read the difference.
- Scroll to zoom the time or frequency axis. Hold <kbd>Option</kbd>/<kbd>Alt</kbd> to zoom the vertical axis.
- Drag to pan. Double-click to fit.

The table under the chart shows each signal's last value, minimum and maximum.

**Copy Netlist** (shown with the advanced settings) copies the SPICE netlist to the clipboard. The **Console** shows the engine log.

## If a run fails

The **Run Simulation Failed** dialog, or a **Simulation setup needs attention** card in the panel, explains why. Common reasons:

- No ground: add a GND symbol connected to the circuit's return path.
- Unconnected pins on simulated parts: connect them or remove the parts.
- No supported parts: add a resistor, capacitor, inductor, source, diode, transistor or op-amp.
- A DC sweep with no source: add a voltage or current source, or use an operating point run.
- No waveform data: check source values, wiring and the analysis settings.

## Simulation with AI

In [Max mode](max-mode.md), you can ask the AI to simulate the circuit. It runs the analysis and shows the graph in the chat. Click **Open in Simulation** to open it in the panel, where you can change the analysis or the SPICE circuit and run it again.

## Related

- [Schematic editor](schematic-editor.md)
- [Power and nets](power-and-nets.md)
- [Design checks](design-checks.md)
- [Symbol editor](symbol-editor.md)
