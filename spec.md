# Crane Game
## Purpose
Players operate a tower crane in a side view, moving loads from a staging area to marked positions on a building under construction before a 3-minute timer expires. The goal is to complete deliveries without exceeding the crane load chart or tipping the crane.

## Inputs
### Keyboard controls
- **J:** move the trolley inward
- **L:** move the trolley outward
- **I:** raise the hook
- **K:** lower the hook
- **Left Arrow:** swing the jib left
- **Right Arrow:** swing the jib right
- **Space:** pick up a load or set a carried load on a matching building position

The crane has a tower, jib, trolley, cable, hook, and suspended-load indicator in a playful yellow construction setting.

## Calculations
The app calculates crane radius as the horizontal distance from the tower center to the suspended load or hook. A radius is compared against this example load chart:

| Radius (ft) | Capacity (lb) |
|---|---:|
| 50 | 20,000 |
| 75 | 13,000 |
| 100 | 9,000 |
| 125 | 7,000 |
| 150 | 5,500 |

For radii between table values, use the capacity at the next larger table radius. This is the conservative "round up" radius rule. For example, 62 ft uses the 75 ft capacity of 13,000 lb, and 138 ft uses the 150 ft capacity of 5,500 lb.

The capacity check uses the weight of the currently suspended load. The crane is not overweight below 100% of the allowed capacity. It warns exactly at 90% of capacity and tips at 100% or more.

## Outputs
A warning appears when the suspended load is exactly 90% of the capacity at the current radius. Crossing that threshold is also shown clearly as a caution state.

A dramatic crane tip-over occurs when the load reaches or exceeds 100% of capacity. The animation ends with an on-screen recovery/reset action; the player may reset the crane and continue the round.

Each round includes:
- A 3-minute countdown timer
- A current score
- The current load weight
- The current radius
- Current chart capacity and safety percentage
- An on-screen load chart with the current radius and load marked
- Delivery progress and the active level
- Per-level wind strength and direction

## Look and feel
The app is a fun, playful construction game with a yellow crane and a building under construction. It uses a clear side view and includes five distinct building levels. Each level has its own visible construction outline and labeled marked delivery positions.

The game has a light mode and a dark mode. It includes a visible theme toggle so the player can switch between bright, high-contrast construction colors and a darker, night-construction palette.

When the crane falls, show a huge, dramatic explosion with expanding fire and smoke effects, debris, and screen shake. When the player passes a level, celebrate with confetti that bursts across the screen.

Preset load weights appear in a randomized mix at the staging area. Wind varies by level and makes a suspended load swing. Loads are picked up by positioning the hook above a staging load and pressing Space. A load is delivered by positioning it over a matching marked position and pressing Space.

## Validation
Use the conservative next-larger-radius rule for all radii:

1. **62 ft:** 62 ft is above 50 ft and at or below 75 ft, so it uses the 75 ft capacity. Allowed load is 13,000 lb. Warning threshold is exactly 11,700 lb (`13,000 x 0.90`). Tip-over begins at 13,000 lb.
2. **125 ft:** 125 ft is exactly in the table, so it uses the 125 ft capacity. Allowed load is 7,000 lb. Warning threshold is exactly 6,300 lb (`7,000 x 0.90`). Tip-over begins at 7,000 lb.
3. **138 ft:** 138 ft is above 125 ft and at or below 150 ft, so it uses the 150 ft capacity. Allowed load is 5,500 lb. Warning threshold is exactly 4,950 lb (`5,500 x 0.90`). Tip-over begins at 5,500 lb.

Implement and test boundary behavior at 89.9%, 90%, 99.9%, and 100% of capacity. Verify the app does not warn below 90%, warns at exactly 90%, does not tip below 100%, and tips at 100% or above.

Also test delivery scoring and both pickup/setdown states:
- A delivered load awards points based on its weight.
- The round ends when the timer reaches zero.
- A load can only be set down on a matching level position.
- Warning and tip calculations update immediately as radius or suspended-load weight changes.

## Out of scope
This is a fictional game example, not a source of legitimate crane specifications or lifting instructions.