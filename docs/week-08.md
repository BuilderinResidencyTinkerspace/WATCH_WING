# Week 8

-Get the Pixhawk actually talking to the servos and motor correctly, and work through ArduPilot's setup and calibration process cleanly enough to start real bench testing, before anything gets mounted into the body.

## What we did


So initially, what we did was read through the ArduPilot documentation to get a basic understanding of how everything fit together. We then uploaded the ArduPlane firmware onto the Pixhawk using Mission Planner's ground control software. After that, we went through the basic configuration steps — accelerometer and compass calibration — though only the internal compass could actually be calibrated, not the external one that comes with the GPS module. What we've come to understand is that in order to calibrate the external compass, it needs to be moved around together with the Pixhawk, both mounted on a single fixed unit, so we decided to leave that calibration for after both were attached to the main body.

We then moved on to radio calibration, and from there to the servo output section. The Pixhawk was powered through a 3300mAh 3S LiPo battery connected to the ESC, which was then wired into MAIN OUT channel 3, and that in turn powers the board. The remaining four servos were attached across the rest of channels 1 to 5.

https://github.com/user-attachments/assets/d9e56841-344a-40bb-9b3b-cab85152925d


In the Servo Output screen, all the servos moved correctly in response to radio input, except for throttle on channel 3. We went through pretty much every component individually to try and find the cause. We checked the RCMAP parameters — RCMAP_ROLL, RCMAP_PITCH, RCMAP_THROTTLE, RCMAP_YAW — and they were all sitting at their correct default values. We checked the servo function assignment again and confirmed channel 3 really was set to Throttle. We checked the physical wiring, checked that the receiver's channel order matched what Pixhawk expected, and confirmed on the transmitter's own screen that the throttle stick's output value was genuinely changing when we moved it, so the signal was leaving the transmitter correctly. It also showed up correctly in the radio calibration screen. This told us the input signal was being sent correctly, it just wasn't translating to an actual output. We decided to set that issue aside for the moment and moved on to ESC calibration.


https://github.com/user-attachments/assets/6a6e90e5-7b14-45b2-b108-5be83ae9cdb1



We tried Mission Planner's one-click "Calibrate ESCs" button, and it failed outright with an error saying to make sure our version was "AC3.3+." After looking into it, it seems this automated calibration flow is really built around ArduCopter's parameter set rather than ArduPlane, which is probably why it didn't work cleanly for a fixed-wing setup like ours. We switched to the manual ESC calibration method instead — throttle stick held all the way up, connect the battery, wait for the ESC to beep confirming it caught the top of the range, then throttle down to get the bottom of the range confirmed the same way. That part worked fine.

The actual explanation for the frozen throttle turned out to be arming, not anything wrong with the wiring or configuration at all. ArduPilot simply will not let throttle output do anything while the board is disarmed, and our pre-arm checks were failing — as far as we can tell, this was tied to the compass not being fully calibrated yet. Once we forcefully armed it through the Actions tab on the Data page in Mission Planner, we were able to get an actual output signal from throttle on channel 3.

## Problems and blockers

-

## Decisions





-

## Next week
Attach the components to the main body

-

## Links

- Code:
- Photos / CAD:
