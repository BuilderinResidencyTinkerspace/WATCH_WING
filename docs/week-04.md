# Week 4

**Goal this week:** Get a suitable body material and a reliable cutting method ready so that construction of the UAV airframe could finally proceed.

## What we did

This week, we focused mainly on finding a suitable material for the UAV body and figuring out a practical way to cut the airfoil and body components. We first tested **Sunboard (PVC foam)**, which we had previously used, but rejected it because it was too thick and dense for our aircraft and would add too much weight to the final airframe.

We then tried **Styrofoam (EPS)** as another possible material. Although it was lightweight, we found that it was not firm enough for our requirements. When we tried cutting it with a blade, the material crumbled easily and did not maintain enough rigidity, making it unsuitable for building the airframe.

After testing the different materials, we decided to use **Thermocol (low-density EPS)** instead. It was considerably lighter while still providing enough rigidity for the structure. However, we quickly realized that cutting it accurately with a normal blade would be difficult, so we decided to use a **hot-wire cutter** instead.

We finalized the CAD design for the **Clark-Y airfoil** and exported the required STL file to create the cutting template. Since a proper nichrome wire was not available locally, we decided to experiment with **gear cable wire** as a substitute. We then built our own DIY hot-wire foam cutter from scratch using the available materials.

Before trying to cut the actual foam, we connected the cutter to a variable DC power supply and tested it at around **16 V and 3.5 A**. The wire heated up properly, confirming that the basic setup was working. However, the wire initially had problems with sagging and kinking. We solved these issues by re-tensioning the wire and manually straightening it instead of replacing it.

By the end of the week, the material and cutting setup were finally ready. We had not yet started cutting the actual Thermocol body panels, but the hot-wire cutter had been successfully bench-tested and was ready for the next stage of construction.

## Problems and blockers

One of the biggest problems we faced was the unavailability of **Depron**, which was our originally intended body material. Due to the ongoing war affecting its supply, we were unable to source it locally and had to look for alternative materials.

We also could not find proper **nichrome wire** locally for the hot-wire cutter. Because of this, we decided to experiment with gear cable wire as a substitute. Although it worked during the initial test, we still need to determine whether it will be durable enough for repeated cutting.

Another issue we faced was that the cutter wire initially **sagged and had some natural kinks**, which could have affected the accuracy of the airfoil cuts. We managed to correct this by re-tensioning the wire and manually straightening it.

The actual Thermocol cutting had also not started yet, so the performance of the cutter on the real material was still something we needed to verify.

## Decisions

After testing the available materials, we decided to use **Thermocol (EPS)** as the main body material for the UAV.

We also finalized the **Clark-Y airfoil** for the wing and completed the CAD/STL template that would be used with the hot-wire cutter.

Since proper nichrome wire was not available, we decided to continue using **gear cable wire as a temporary substitute**, unless we were able to find a reliable source of nichrome wire.

With the material, airfoil design, and cutting method decided, we were finally ready to start constructing the actual airframe.

## Next week

Next week, we will complete the **body of the UAV**, including the wings, fuselage, and tail, using the Thermocol and the hot-wire cutting setup. Once the panels are completed, we will weigh the finished airframe and check the actual weight against our target **AUW and wing loading**.

After completing the main body, we will also start working on the **electronics**, including the flight controller, servos, motor, ESC, GPS, and other components required for the UAV.

## Links
- Code:
- Photos / CAD: <img width="1200" height="1600" alt="WhatsApp Image 2026-08-09 at 08 46 01" src="https://github.com/user-attachments/assets/c6ea2641-2871-4bfc-b6f4-484bcb062295" />

