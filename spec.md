# Crane Game

## Purpose
The purpose of this game is to show someone how much load a crane can handle and how far it can stretch out.
## Inputs
There is a radius and weight calculation from the crane. I want to use the arrow keys to pick up the load and move it somewhere on the building. It will be a side view of the crane
## Calculations
the calculations will be to see if the weight picked up exceeds the maximum weight for that certain radius. use this
Radius (ft)	Capacity (lb)
50	         20,000
75	          13,000
100	           9,000
125	           7,000
150	             5,500
## Outputs
I want it pick it up and move it if it works in the loading capacity.
A warning when the load reaches 90% of capacity at the current radius, and a dramatic tip-over when it passes 100%
## Look and feel
I want it to be fun and playful like a game. I want the crane to be yellow and a fun building that is under constuction. i want there to be multiple levels.
## Validation
Using the next larger radius in the table is conservative, and interpolating is less so. Then compute the allowed load by hand at three radii, including one just inside a table radius and one just outside, and check that the app warns and tips at the right points.
## Out of scope
this does not produce legit craning specs