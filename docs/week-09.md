# Week 9

**Goal this week:**
Mount all the electronics into the body, get everything wired and confirmed working, and take it up for a first flight

## What we did
We started mounting the components inside the body of the plane. First, we mounted the servos for both ailerons, the elevator, and the rudder. The hardest part here was bending the rods correctly to connect each servo to its control surface — for this, we 3D-printed servo horns so the rods could actually connect properly at both ends.

We then placed the battery, working out the center of gravity of the plane first, and mounted it in position using double-sided tape. The Pixhawk was mounted onto the side wall, and the radio receiver was placed inside the body as well. The GPS was kept exposed, using a gap we'd already left for it during the design stage. We also designed a firewall for mounting the motor, 3D-printed it, and fixed it to the front of the body using a glue gun.

<img width="1200" height="1600" alt="WhatsApp Image 2026-09-19 at 19 44 54" src="https://github.com/user-attachments/assets/13f61bea-6acb-40e0-905c-8fdeb61fa4bd" />



Once all of that was in place, we made all the connections and started checking everything. The servos and motor were working fine, but we ran into an orientation issue — since the Pixhawk was mounted on the side wall rather than flat, we worked out that the correct orientation needed to be set as Yaw 180 and Roll 90. There was no preset option for this exact combination, so we had to figure out how to set up a custom orientation instead, which sorted the issue out.



https://github.com/user-attachments/assets/c18ed667-0398-4f2e-9c53-f4187ca28d09




After that came the bigger task of closing up the underside of the plane. We closed it using tape and added zip ties for extra security. We (Shan chettan lol)then checked the motor's thrust by arming it, and it gave a good amount of thrust, which had us fairly excited.



https://github.com/user-attachments/assets/7c95ffb8-d15e-42a9-8387-aaaa71229296






Looking back, that excitement is exactly where we went wrong — we went straight into our first flight attempt without simulating beforehand or properly checking the plane's control response first. In particular, we hadn't verified the elevator's orientation — pushing the stick down should have raised the elevator, but the direction was actually reversed. As soon as we moved the stick down in flight, the plane reacted the wrong way and crashed. The damage from this included a broken propeller and small cracks in the body.


https://github.com/user-attachments/assets/8a103069-e0ae-4b2f-8837-02de886d7a3d





-

## Problems and blockers

-

## Decisions

Fix the body and make subsequent flights

-

## Next week

-

## Links

- Code:
- Photos / CAD:
