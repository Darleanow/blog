---
title: "Demystifying Raycasting: Building 2D and 2.5D Ray cast Engines in C++"
datePublished: Tue May 16 2023 14:18:41 GMT+0000 (Coordinated Universal Time)
cuid: clhqd0ft1000a0alf8fhr3uu8
slug: demystifying-raycasting-building-2d-and-25d-ray-cast-engines-in-c
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684246601338/5de415f3-fadb-4079-a4ff-73397b5ce803.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1684246704708/2b471372-ae30-46a1-9a7b-de74cdd317e1.jpeg
tags: cpp, sfml, raycasting

---

Raycasting is a core technique used in computer graphics and game development. It's like casting a line into a scene to find out what it hits. A ray cast can answer questions like "What object is under the mouse cursor?" or "What's in the player's field of view?" Today, we'll delve into the fascinating world of raycasting, focusing on 2D and 2.5D engines. We'll explore how they work, key algorithms, and how you can build your engines.

##   
Mathematical Underpinnings of Raycasting

Raycasting may seem like a primarily graphical technique, but at its heart, it's a mathematical process. To truly understand raycasting, we need to delve into the mathematical principles it's based upon.

1. **Ray Casting**: The fundamental math operation in raycasting is the projection of a ray from a point in a specific direction. A ray in 2D can be represented as a vector originating from a point. This vector is typically defined by an angle from a reference direction. For example, if we take the positive x-axis as our reference, a ray cast at a 45-degree angle would be represented by the vector (cos(45), sin(45)).
    
2. **Intersection Tests**: The next mathematical operation is determining whether and where a ray intersects with a line segment (representing a wall). This can be done using line-line intersection formulas derived from the equations of the two lines. One common approach is to use the parametric form of the line equation and solve for the point of intersection.
    
3. **Distance Calculations**: Once an intersection point is found, we calculate its distance from the origin of the ray. This can be done using the Euclidean distance formula. In a 2.5D raycasting engine, this distance is used to calculate the height of the wall slice to be drawn.
    
4. **Perspective Projection**: In a 2.5D raycasting engine, we also need to create the illusion of 3D perspective. This is done by drawing the wall slices taller as they get closer to the player. The height of a wall slice is inversely proportional to its distance from the player, creating a simple perspective projection.
    
5. **Fishbowl Correction**: A common issue with raycasting is a distortion known as the "fishbowl effect," where lines that should appear straight are curved. This happens because rays are cast in a fan-like pattern, but the distances are calculated as if they were all perpendicular to the player's view. This effect can be corrected by multiplying the calculated distance by cos(BETA), where BETA is the difference between the angle of the ray and the player's viewing angle.
    

Understanding these mathematical principles can provide a deeper insight into how raycasting works and how it can be tweaked and optimized for various applications.

## Building a 2D Raycast Engine

Creating a 2D ray cast engine involves several steps:

* **Casting Rays**: The first step is to cast rays from the player's position in all directions within the player's field of view. The number of rays and the field of view can be adjusted to suit your needs.
    
* **Detecting Collisions**: Once the rays are cast, the next step is to determine where they collide with the walls. This can be done using a simple line-segment-to-line-segment intersection test for each ray and wall segment.
    
* **Rendering the View**: After determining the intersection points, the next step is to draw the rays or the walls that they hit. This can give the player a sense of the environment around them.
    

## Building a 2.5D Raycast Engine

Creating a 2.5D ray cast engine involves a few more steps, building upon the 2D raycasting:

* **Casting Rays**: Just like in 2D, we begin by casting rays from the player's position. However, in 2.5D, we only cast rays horizontally across the player's field of view.
    
* **Detecting Collisions**: Next, we find where each ray intersects with the walls. This is done using a variation of the digital differential analyzer (DDA) algorithm, which is a fast method for line rasterization.
    
* **Calculating Wall Heights**: For each ray, we calculate the height of the wall it hits on the screen. This height is inversely proportional to the distance from the player to the wall to create a perspective effect.
    
* **Rendering the View**: Finally, we draw vertical slices of walls on the screen, where each slice corresponds to a ray. The result is a 3D perspective created from 2D information, hence the term "2.5D."
    

Exploring the Engines

Let's take a look at two fantastic implementations of raycasting engines by me, available on GitHub: a 2D Raycast Engine and a 2.5D Raycast Engine. Both projects are excellent examples of raycasting in action and can serve as a great learning resource for anyone interested in the subject.

* **2D Raycast Engine**: In this project, I implemented a 2D raycasting engine using the SFML library. The engine casts rays from a point source, checks for intersections with walls and displays the result. The interactive nature of the project allows you to move the point source around and observe how the rays interact with the environment. The visualization provides a clear, intuitive understanding of how 2D raycasting works. You can check out the source code [**here**](https://github.com/Darleanow/UselessSFMLProjects/tree/main/2D%20raycast%20Engine).
    
* **2.5D Raycast Engine**: Moving onto the 2.5D Raycast Engine, the project takes things a step further. It demonstrates how to use 2D raycasting to create a 3D perspective, reminiscent of classic first-person shooter games. The engine casts rays across the field of view, calculates wall slice heights based on distance, and renders the view with simple shading for depth perception. The result is a simple, yet effective 3D environment. Explore the project's source code [**here**](https://github.com/Darleanow/2.5D-Raycast-Engine).
    

## Delving deeper into raycasting

While the above provides a general overview of building a raycasting engine, the true depth of raycasting lies in its intricacies. For instance, techniques like fishbowl correction can be applied to my 2.5D raycasting to correct the "curved" appearance of the rendered view caused by raycasting's inherent distortion.

Another nuance is performance optimization. How can we minimize the number of rays cast or intersections calculated while still achieving a convincing illusion of 3D space? Techniques like space partitioning or bounding volume hierarchies can be used to improve efficiency.

## Conclusion

Raycasting is a powerful technique, offering a unique blend of performance and visual impact. Its application stretches beyond games to fields like robotics and artificial intelligence for tasks like collision detection and path planning. By understanding raycasting and building your engines, you'll acquire a valuable toolset for your programming and game development journey.

Whether you're building a retro-styled FPS game or a robot that maps its own environment, the possibilities with raycasting are endless. So, why not check out my engines and start casting rays?