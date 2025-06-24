# Cuh

**Cuh** is an expander module that adds MIDI output and CV control for Scale/Wavetable selection to Helical.

## ⚠️ Warning

Connecting Helical to MIDI devices **without using Cuh** may cause overcurrent and result in permanent damage to the unit.\
Such damage is **not covered by the warranty**.

Cuh provides the following functions:

1. Outputs Helical's note data and all knob CC messages via USB-MIDI and TRS-**Type A** MIDI.
2. Provides CV inputs for controlling Scale and Wavetable selection.

> **Note:** Cuh functions **only as a MIDI Device**.\
> If you need MIDI Host functionality, please use a third-party converter.

---

# Controls and Outputs



### MIDI Output (USB-C / TRS-MIDI)

Outputs Helical's note data and knob CC messages.

- If Orbit is **unpatched**:
  - All note data is output on the channel set by [`midiChArc`](#midisettingtxt-parameters).
- If Orbit is **patched**:
  - Note data is output separately based on the channels configured for each output.

```
Helical supports high-speed MIDI transmission of up to 999 messages per second.  
Note messages are prioritized over CC messages.
```

### Scale CV IN

Controls the Scale preset selection via 0–5V CV input.\
Independently of the currently selected scale, 0–5V corresponds to presets 1–16.

### Wavetable CV IN

Controls the Wavetable preset selection via 0–5V CV input.\
Independently of the currently selected wavetable, 0–5V corresponds to presets 1–8.

---

# Velocity Setting

Note velocities sent via Cuh are determined by Helical's **Dynamic Setting**.

### How to Set

1. Double-click the **Scale knob** to enter Dynamic Setting Mode (LED blinks rapidly).
2. Hold **reloAd** (bottom-left button) while turning the Scale knob to set the volume center.
3. Hold **relOad** (bottom-right button) while turning the Scale knob to set the volume width.
4. Click the Scale knob to exit back to normal mode.

- An approximate range is shown via Helical's LEDs.
- For precise tuning, edit the SD card's `setting.txt` and set `volCenter` and `volWidth` (0–100%).
- MIDI output velocity will be remapped to the 0–127 range.

---

# Note / CC Output

All Note and CC messages are sent via Cuh's USB and TRS MIDI outputs.

You can configure the output channels by editing the `midiSetting.txt` file on the SD card.

- If Orbit is unpatched, all note data is output from `midiChArc`.

### `midiSetting.txt` Parameters

| Parameter    | Description                 | Range    |
| ------------ | --------------------------- | -------- |
| midiChArc    | Set Arc MIDI Channel        | 1 \~ 127 |
| midiChOrbit  | Set Orbit MIDI Channel      | 1 \~ 127 |
| ccEnable     | Enable/Disable CC Output    | 0 or 1   |
| midiCCCh     | Set CC Output Channel       | 1 \~ 127 |
| ccPoly       | CC Number for Poly knob     | 1 \~ 127 |
| ccRoot       | CC Number for Root knob     | 1 \~ 127 |
| ccGlide      | CC Number for Glide knob    | 1 \~ 127 |
| ccSpread     | CC Number for Spread knob   | 1 \~ 127 |
| ccHelicity   | CC Number for Helicity knob | 1 \~ 127 |
| ccWave       | CC Number for Wave knob     | 1 \~ 127 |
| ccEnv        | CC Number for Env knob      | 1 \~ 127 |
| ccLock       | CC Number for Lock switch   | 1 \~ 127 |
| ccCutoff     | CC Number for Cutoff knob   | 1 \~ 127 |
| ccQ          | CC Number for Q knob        | 1 \~ 127 |
| ccIndex      | CC Number for Index knob    | 1 \~ 127 |
| ccFilterType | CC Number for Filter type   | 1 \~ 127 |
| ccLength     | CC Number for Length knob   | 1 \~ 127 |

#### Sample `midiSetting.txt`

```txt
midiChArc 1
midiChOrbit 2
midiCCCh 1
ccPoly 20
ccRoot 21
ccGlide 22
ccSpread 23
ccHelicity 24
ccWave 25
ccEnv 26
ccLock 27
ccCutoff 28
ccQ 29
ccIndex 30
ccFilterType 31
ccLength 32
```

---

# How to Install

Connect the USB cable included with Cuh as shown in the diagram.

```
If Cuh is not recognized (LED does not light), turn off power and reconnect.  
The connector may be tight; insert with care to avoid damage.
```

---

# Update Firmware

Cuh is supported from firmware version **v2.08 and above**.
If your Helical has a serial number of **367 or higher**, no update is needed.

To update:

1. Download the firmware `.bin` file from Helical's GitHub.
2. Go to the [Daisy Web Programmer](https://electro-smith.github.io/Programmer/).
3. Follow the on-screen instructions to upload the firmware.
4. Disconnect the USB cable from DaisySeed.
5. Power on the Eurorack case and confirm the update was successful.

---

# Specifications

- Width: 4HP
- Max Depth: 30mm
- Current Draw:
  - +12V: 20mA
  - -12V: 5mA
- CV Input Range: 0–5V (depends on knob position)

---

# Warranty

Sdkc Instruments warrants this product to be free of material and manufacturing defects for **1 year** from the purchase date (proof required).

This warranty does **not** cover:

- Incorrect power supply voltages
- Reversed Eurorack bus cable connections
- Misuse or abuse
- Knob or faceplate removal
- Unauthorized firmware updates or modifications
- Environmental damage (excessive heat, humidity, etc.)

If warranty service is needed, contact your dealer.\
Sdkc Instruments will repair or replace the product if the defect is confirmed and covered under warranty.

Sdkc Instruments assumes **no responsibility** for personal injury or damage resulting from the use or misuse of this product.

---

# Contact

For inquiries, please email:\
**sdkc.store[a]gmail.com** (replace `[a]` with `@`)

