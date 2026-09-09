# Week 5

**Goal this week:** Actually get a cuttable body material sorted and start making real progress on the airframe, without losing more time.

## What we did
- Found a source for Thermocol close by — a medical store, of all places — and picked up a sheet to work with.
- The sheet turned out to be way thicker than what we actually needed for the wing, so the plan was to slice it down ourselves using the hot-wire cutter, guided by a balsa wood template clamped on either side to keep the cut level and consistent.
- Tried this out, and the balsa template ended up scorching/burning where the hot wire ran along it for too long — not something we'd expected going in.
- On top of that, the wire itself was still a little jagged (a leftover issue from the cutter build), so even where it did cut, the Thermocol came out with an uneven, rough finish instead of a clean flat surface.
- The gear cable wire we'd been using as a nichrome substitute also snapped partway through, with no replacement wire on hand.
- Between the burnt template, the uneven cuts, and the broken wire, it became clear we were fighting the material and the tool at the same time, and that patching this together further wasn't going to get us a usable wing.
- Made the call to source genuine Depron sheet instead, even knowing it would take about a week to arrive.
- Rather than sit idle for that week, decided to start electronics work in parallel from this point on, instead of waiting on the airframe to be "done" first.
- Also, on Shan chettan's advice, decided to switch the camera module from ESP32-CAM to a Raspberry Pi Camera — the image quality difference (resolution, low-light performance, autofocus) matters directly for the round-to-round comparison work later, and it was a low-cost switch to make now rather than after more had been built around ESP32-CAM.

## Problems and blockers
- Thermocol from the medical store was too thick, and our attempt to resize it ourselves (hot-wire + balsa template) failed on multiple fronts — burnt template, jagged/uneven cuts, and a broken cutting wire, with no spare wire available.
- Waiting a week for Depron to arrive is real lost time on the airframe specifically, even though electronics work can fill that gap.

## Decisions
- Abandon Thermocol for the body, order genuine Depron sheet instead, and accept the ~1 week wait.
- Use the waiting period to start electronics bring-up in parallel, rather than treating it as dead time.
- Switch camera module from ESP32-CAM to Raspberry Pi Camera, per Shan chettan's advice.

## Next week
- Begin Raspberry Pi bring-up — OS flashing, headless SSH setup, picamera2 install and test capture.
- Begin bench-testing the RC transmitter/receiver/ESC/motor/servo chain, independent of the flight controller.

## Links
- Code:
- Photos / CAD:<img width="1600" height="1200" alt="image" src="https://github.com/user-attachments/assets/8e9ed856-229a-407a-a06d-1582b1a28a67" />


https://github.com/user-attachments/assets/4cb5d6a5-31f4-4e36-bd63-a17d4b966aa3

