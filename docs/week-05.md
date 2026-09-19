# Week 5

**Goal this week:** Get a suitable body material sorted out and make progress on the airframe while starting the electronics work in parallel.

## What we did

This week, we finally found a source for **Thermocol** nearby. Interestingly, we found it at a medical store and were able to get medicine boxes made of thermocol to continue working on the airframe. However, when we brought it back and checked the dimensions, we realized that the sheet was much thicker than what we actually needed for the wings.

We decided to try reducing the thickness ourselves using the **hot-wire cutter** we had built earlier. To keep the cut level and consistent, we planned to use a **balsa wood template** clamped on either side of the Thermocol and guide the hot wire along the templates. This seemed like a simple solution, but when we actually tried it, we ran into another unexpected problem. The hot wire remained in contact with the balsa template for too long in some places, causing the wood to **scorch and burn**.

The cutting itself also did not turn out as expected. The wire we were using still had some **jagged sections** left over from the earlier problems with the cutter, and this caused the Thermocol to come out with an uneven and rough surface instead of the clean, flat surface we needed for the wing.

Things became even more difficult when the **gear cable wire** we had been using as a substitute for nichrome wire finally snapped during the process. Since we did not have a replacement wire available, we could not continue experimenting with the cutter. At this point, with the balsa template getting damaged, the Thermocol cuts coming out uneven, and the cutting wire broken, it became clear that we were spending too much time trying to make the material and cutting setup work.

After considering the options, we decided that continuing with Thermocol was no longer practical. We therefore decided to **order genuine Depron sheet** instead. Although it would take approximately a week to arrive, using the correct material would save us from repeatedly trying to modify an unsuitable material and would give us a much better starting point for the final airframe.

Rather than letting the week of waiting become completely unproductive, we decided to start working on the **electronics in parallel**. This would allow us to continue making progress on the project while waiting for the Depron.

We also made an important change to the camera system this week. Based on **Shan chettan's advice**, we decided to replace the **ESP32-CAM with a Raspberry Pi Camera**. Since the Watchwing project depends heavily on comparing images from different flights, image quality is particularly important. The Raspberry Pi Camera provides advantages in areas such as **resolution, low-light performance, and autofocus**, making it a more suitable option for the image-comparison part of the project. We decided that making this change now would be much easier than building more of the system around the ESP32-CAM and changing it later.

## Problems and blockers

The main problem this week was that the Thermocol we sourced was **too thick**, and our attempt to reduce its thickness using the hot-wire cutter did not work as planned. The balsa templates began to burn when the hot wire remained against them for too long, while the uneven sections of the cutting wire resulted in rough and inconsistent cuts.

The situation became more difficult when the **gear cable wire snapped** during the process. Since we did not have a spare wire available, we were unable to continue testing the cutter.

After several attempts, it became clear that trying to fix the existing setup further would take more time without guaranteeing a usable wing. We therefore decided to move to genuine Depron instead.

The Depron would take around **one week to arrive**, which meant that airframe construction would have to pause temporarily. However, we decided to use this waiting period to begin the electronics work rather than leaving the project idle.

## Decisions

After the failed Thermocol cutting attempts, we decided to **abandon Thermocol as the body material** and order genuine **Depron sheet** instead. Although this meant waiting approximately a week for the material to arrive, we felt that using the correct material would be more reliable than continuing to modify the Thermocol ourselves.

We also decided to begin **electronics bring-up in parallel** while waiting for the Depron. This would allow us to work on the electrical and control systems independently of the physical airframe.

Another important decision was to switch the camera system from the **ESP32-CAM to a Raspberry Pi Camera**, following Shan chettan's advice. Since image quality will directly affect the round-to-round change-detection process, we decided that the better image quality and camera capabilities were worth making the change at this stage.

## Next week

Next week, we will begin the **Raspberry Pi bring-up**, starting with flashing the operating system, setting up headless SSH access, installing `picamera2`, and testing image capture.

At the same time, we will begin **bench-testing the RC transmitter, receiver, ESC, motor, and servos as a standalone system**, without connecting them to the flight controller initially. This will allow us to verify each part of the control and propulsion system before integrating everything into the UAV.

## Links
- Code:
- Photos / CAD:<img width="1600" height="1200" alt="image" src="https://github.com/user-attachments/assets/8e9ed856-229a-407a-a06d-1582b1a28a67" />


https://github.com/user-attachments/assets/4cb5d6a5-31f4-4e36-bd63-a17d4b966aa3

