## Project: 3D Motion Planning
![Quad Image](./misc/enroute.png)

---


# Required Steps for a Passing Submission:
1. Load the 2.5D map in the colliders.csv file describing the environment.
2. Discretize the environment into a grid or graph representation.
3. Define the start and goal locations.
4. Perform a search using A* or other search algorithm.
5. Use a collinearity test or ray tracing method (like Bresenham) to remove unnecessary waypoints.
6. Return waypoints in local ECEF coordinates (format for `self.all_waypoints` is [N, E, altitude, heading], where the drone’s start location corresponds to [0, 0, 0, 0].
7. Write it up.
8. Congratulations!  Your Done!

Rubric Points

Writeup / README

1. Provide a Writeup / README that includes all the rubric points and how you addressed each one.

You're reading it! Below I describe how I addressed each rubric point and where in my code each point is handled.

Explain the Starter Code

1. Explain the functionality of what's provided in motion_planning.py and planning_utils.py

These scripts contain a basic planning implementation that includes grid generation, A* search, and waypoint smoothing.



Implementing Your Path Planning Algorithm

1. Set your global home position

The first line of colliders.csv is read to extract lat0 and lon0 as floating-point values. These are used in the self.set_home_position() method to set the global home.



2. Set your current local position

The local position relative to the global home is computed and updated accordingly.



3. Set grid start position from local position

This ensures the drone starts in a valid grid location corresponding to its real-world local position.

4. Set grid goal position from geodetic coords

This step allows goal selection based on latitude and longitude, which is then converted to a grid position.

5. Modify A* to include diagonal motion (or replace A* altogether)

The A* search algorithm was modified to include diagonal movements, with a cost of sqrt(2).

6. Cull waypoints

Waypoints are pruned using a collinearity test to remove unnecessary intermediate points, leading to a more efficient path.

Execute the Flight

1. Does it work?

Yes! The planned path is successfully executed.

Double check that you've met specifications for each of the rubric points.


# Extra Challenges: Real World Planning

For an extra challenge, consider implementing some of the techniques described in the "Real World Planning" lesson. You could try implementing a vehicle model to take dynamic constraints into account, or implement a replanning method to invoke if you get off course or encounter unexpected obstacles.


