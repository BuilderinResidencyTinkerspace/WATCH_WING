# WatchWing — Autonomous Fixed-Wing UAV 

WatchWing is a scratch-built, autonomous fixed-wing UAV . This document
walks through the entire build — airframe, electronics, wiring, and software
configuration — so it can be replicated from scratch.

This is a first-time build, and this README includes the mistakes we made
and what we'd do differently, not just the "correct" path. Read the
**Lessons Learned** section before you start — it will save you real time.

---

## 1. Overview

- **Airframe:** Flite Test "Simple Scout" (stock plan, no custom scaling)
- **Flight controller:** Pixhawk-class board (Pixhawk 2.4.8 / Pixhawk1) running ArduPilot's **ArduPlane** firmware
- **Ground control:** Mission Planner (Windows)
- **Radio:** FlySky FS-i6 transmitter + FS-iA10B receiver (PPM)
- **Power:** A2212 1400KV motor, SimonK 30A ESC, 3S LiPo battery
- **Navigation:** M10 GPS module with onboard compass (IST8310)
- **Mission logic:** GPS waypoint patrol, flight modes (Manual / FBWA / Loiter)

---

## 2. Full Parts List

| Component | Notes |
|---|---|
| Pixhawk-class flight controller | Pixhawk 2.4.8 or compatible, running ArduPlane |
| GPS + compass module (M10-based) | Two separate connectors: GPS over UART, compass over I2C |
| FS-i6 transmitter | Enable PPM output in transmitter menu |
| FS-iA10B receiver (or FS-iA6B) | Must support PPM output on a single wire |
| A2212 1400KV brushless motor | |
| SimonK 30A ESC | Signal wire connects to Pixhawk, not the battery |
| 3S LiPo battery (we used 3300mAh) | Connects directly to ESC, never to Pixhawk |
| Propeller | Sized to match motor/battery combo |
| SG90 servos ×4 | 2× aileron, 1× elevator, 1× rudder |
| Genuine Depron foam sheet, 5mm | **Do not substitute** — see Lessons Learned |
| Carbon rod or bamboo skewer | Wing spar |
| 3D printed parts | Motor mount/firewall, servo horns, linkage couplers |
| Hot glue gun | Foam assembly |
| Zip ties, tape | Securing the underbody hatch |
| USB cable, laptop | For flashing and Mission Planner |

---

## 3. Airframe — Build to the Flite Test Simple Scout Plan

We initially tried to custom-design our own wing dimensions. **Not preferred** The official Flite Test Simple Scout plan already matches a small
electric motor class well: - https://www.flitetest.com/articles/ft-simple-scout-build

- Wingspan: 952mm
- Wing area: 20.9 dm²
- Target AUW: ~535.8g
- Wing loading: ~25.6 g/dm²
- CG: 62mm (2.44in) back from the wing's leading edge

Download the plan (full-size or tiled, depending on your printer) from
Flite Test's site, print at verified **100% scale** (check the calibration
square before cutting anything), and trace it directly onto your foam.

### Material — genuine Depron

We went through three materials before landing on the right one:

1. **PVC "Sunboard"** — roughly 8x too dense. Do not use.
2. **Thermocol (EPS)** sourced generically — too thick, and cutting it down
   to size with a hot-wire cutter (using a balsa template guide) went badly:
   the balsa scorched, the wire was slightly jagged and produced an uneven
   cut, and the wire itself eventually snapped.
3. **Genuine Depron, pre-cut to 5mm** — this is what actually worked. It
   cuts cleanly with a sharp hobby knife, no hot-wire cutter needed.

If you're sourcing material yourself, ask specifically for **Depron** or
**RC/hobby-grade foam board** by name, not generic "foam board" or "foam
sheet" — those terms commonly return PVC signage board or packaging foam,
neither of which is suitable.

### Assembly

Follow the Flite Test build video/plan instructions for fold pattern, spar
placement, and tail assembly. 
---

## 4. Electronics Wiring

### Power path

```
Battery (3S) ──► ESC power input (thick wires, direct connection)
ESC ──► Motor (thick wires)
ESC's BEC ──► Powers Pixhawk's servo rail (this is what powers the
              servos AND Pixhawk's own logic — battery never
              connects to Pixhawk directly)
```

### Signal wiring — MAIN OUT channel assignments

| Pixhawk MAIN OUT | Connects to | Servo Function |
|---|---|---|
| 1 | Aileron servo (left) | `Aileron` |
| 2 | Elevator servo | `Elevator` |
| 3 | ESC signal wire | `Throttle` |
| 4 | Rudder servo | `Rudder` |
| 5 | Aileron servo (right) | `Aileron2` |

Note: ArduPlane handles the opposite-direction movement between the two
aileron servos automatically once one is set to `Aileron` and the other to
`Aileron2` — no manual reversing needed.

### Receiver

```
FS-iA10B PPM output (single wire) ──► Pixhawk RC IN port
```
Enable PPM output in the transmitter's RX Setup menu before connecting.

### GPS / Compass module

The module has two separate connectors:
- **4-pin connector (GPS, UART)** → Pixhawk's GPS port
- **I2C connector (compass)** → Pixhawk's I2C/compass port

---

## 5. Software Setup (Mission Planner)

### 5.1 Flash ArduPlane

`Setup → Install Firmware → Plane` — select your board and let it flash.
Confirm "Upload Done" before continuing.

### 5.2 Accelerometer Calibration

`Setup → Mandatory Hardware → Accel Calibration` — rotate the board through
all six prompted positions (level, left, right, nose-up, nose-down, upside
down) and hold each steady for a few seconds.

### 5.3 Compass Calibration — important limitation

`Setup → Mandatory Hardware → Compass` — you can calibrate the **internal**
compass on the bench immediately. The **external** compass (on the GPS
module) needs to physically rotate through varied orientations **together
with the Pixhawk as one rigid unit** for the calibration to mean anything.
If they aren't mounted together yet, skip external compass calibration
until they are — you cannot do it properly with the two loose and separate.

### 5.4 Radio Calibration

`Setup → Mandatory Hardware → Radio Calibration` — move every stick and
switch through its full range, then save.

### 5.5 Servo Output — assign functions

`Setup → Servo Output` — assign each channel's function per the table in
Section 4. Confirm live "Position" values change as you move the sticks.

### 5.6 ESC Calibration — use the manual method

Mission Planner's one-click **"Calibrate ESCs"** button is built around
ArduCopter's parameter set and will fail on ArduPlane with a
`"Please ensure your version is AC3.3+"` error. Use the manual method
instead:

1. **Remove the propeller.**
2. Disconnect the battery.
3. Move the throttle stick to full-up, hold it there.
4. Connect the battery — the ESC beeps to confirm it registered max throttle.
5. Move the throttle stick to full-down.
6. The ESC beeps again, confirming the minimum.
7. Disconnect and reconnect the battery normally.

### 5.7 Arming — the most common "nothing responds" cause

If your control surfaces move but the **motor won't respond to throttle at
all**, this is very likely **not** a wiring or configuration problem —
ArduPilot blocks all throttle output while disarmed, full stop. Check the
Messages/pre-arm list for what's actually failing (commonly an incomplete
compass calibration). Once pre-arm checks clear and the board is armed
(via the rudder-arm gesture, or Mission Planner's Actions tab), throttle
will respond immediately.

### 5.8 Custom AHRS Orientation (if mounting Pixhawk at an angle)

If your Pixhawk isn't mounted flat (ours was mounted on a side wall,
requiring Roll 90° + Yaw 180°), and the exact combination you need isn't in
the standard `AHRS_ORIENTATION` dropdown:

1. Set `AHRS_ORIENTATION` to **Custom1**.
2. Set `CUST_ROT_ENABLE = 1`.
3. Enter your actual mounting angles into `CUST_ROT1_ROLL`, `CUST_ROT1_PITCH`,
   `CUST_ROT1_YAW`.
4. Write, reboot, and verify the artificial horizon responds correctly to
   the board's real physical attitude.

### 5.9 Flight Modes

`Config → Flight Modes` — assign a spare channel (we used Channel 5) as
your mode switch (`FLTMODE_CH`). We used a 3-position switch mapped as:

- Position 1: **Manual**
- Position 2: **FBWA** (fly-by-wire — holds a target bank/pitch angle,
  meaningfully more forgiving than Manual for a first-time pilot)
- Position 3: **Loiter** (circles a fixed GPS point)

---

## 6. Mounting Into the Airframe

- Mount servos into the wings/tail using 3D-printed servo horns; connect
  with bent-wire pushrods.
- Calculate CG before placing the battery; secure it with double-sided tape.
- Mount the Pixhawk (note its orientation — see Section 5.8 if not flat).
- Mount the receiver inside the body.
- Leave the GPS module **exposed to the sky** — it needs a clear view for
  satellite lock and cannot be enclosed like the other electronics.
- 3D-print and glue a firewall at the nose for the motor mount. (given in cad section)
- Close the underside hatch with tape and zip ties.

Once the Pixhawk and GPS are mounted together on the airframe, go back and
complete the **external compass calibration** (Section 5.3) — this is the
point where it finally becomes possible.

---

## 7. Before Your First Flight

- **Practice on a simulator first.** We used [PicaSim](https://www.thepicasim.com/)
  (free). This is not optional — get real stick time before risking the
  airframe.
- **Physically verify every control surface's direction** against stick
  input before flying. A reversed elevator caused one of our crashes.
- **Double-check your flight mode switch positions** — know exactly which
  physical position corresponds to which mode, and rehearse switching
  between them without looking, before you're relying on it mid-flight.
- Remove the propeller for all bench/arming tests until you're actually
  ready to fly.
- Scout your flight location for obstacles (trees, power lines, buildings)
  before taking off.

---

## 8. Lessons Learned

- **Material sourcing is the single biggest time sink in this build.** Ask
  for Depron/EPP by name; verify density by weighing a sample before
  committing to a full sheet.
- **"Servo works, motor doesn't" is almost always an arming/pre-arm issue**,
  not a wiring problem. Check the Messages tab before assuming anything
  else is wrong.
- **Mission Planner's automated ESC calibration doesn't work for
  ArduPlane** — use the manual method from the start.
- **External compass calibration requires the GPS and Pixhawk to be
  mounted together** — don't attempt it while they're loose on a bench.
- **FBWA is a better default flying mode than pure Manual** for a
  first-time pilot — it limits how far the plane can bank/pitch, which
  meaningfully reduces stall risk during panicked, tight corrections.
- **Flight mode switch mix-ups are a real, common failure mode** — an
  accidental Loiter engagement mid-flight caused one of our crashes.
  Rehearse switch positions on the ground before trusting them in the air.
- **A broken firewall in a crash is often a good outcome, not a bad one** —
  so while 3d printing, give it low infill. it absorbed impact energy that would otherwise have gone into the motor
  or fuselage.

---

## 9. Status

WatchWing achieved three powered manual test flights.. The airframe was damaged beyond repair on the
third crash. 

