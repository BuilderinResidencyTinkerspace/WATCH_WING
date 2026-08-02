# Week 2

**Goal this week:**
Present the Watchwing project formally to the group and firm up the technical direction.

## What we did
- Delivered a formal presentation covering the Watchwing project: goals, scope, and planned architecture
- Presented the autonomous UAV concept — a fixed-wing drone that flies a predefined GPS waypoint mission
- Explained the area/perimeter change-detection approach:
- The UAV flies a fixed route through a set of GPS waypoints (e.g. 5 points)
- At each waypoint, the camera is GPS-triggered to capture an image (Round A)
- On a later flight (Round B), the same route is flown and images are captured at the same 5 points
- Corresponding images from Round A and Round B (Point 1 vs Point 1, Point 2 vs Point 2, etc.) are compared
- Any significant differences between matching points are flagged as changes in that area
- Walked through the intended system stack: flight controller (Pixhawk), ArduPilot (ArduPlane) firmware, GPS/IMU, and MAVLink-based ground control (Mission Planner)

## Problems and blockers
- Still deciding between specific flight controller hardware options
- Need to figure out how precisely the UAV can return to the exact same position/orientation at each waypoint across flights, since image comparison accuracy depends on it

## Decisions
- Change detection method: GPS-triggered images capture at fixed waypoints, compared point-to-point across flight rounds
- will also have video log during the entire flight saved onto an onboard sd card for manual inspection

## Next week
- Start with the body of UAV

