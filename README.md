# Intelligent Traffic System (ITS) Plugin for Unreal Engine

## Table of Contents
- [Bring Realistic Traffic to Your Unreal Engine Projects](#bring-realistic-traffic-to-your-unreal-engine-projects)
- [Key Features](#key-features)
- [Getting Started](#getting-started)
    - [Installation](#installation)
    - [Usage](#usage)
        - [Vehicle System Setup](#vehicle-system-setup)
        - [Pedestrian System Setup](#pedestrian-system-setup)
        - [UI Manual](#ui-manual)
            - [NPC Controls](#npc-controls)
            - [Pedestrian Crossing Controls](#pedestrian-crossing-controls)
            - [Pedestrian Spline Controls](#pedestrian-spline-controls)
            - [Player Interaction Controls](#player-interaction-controls)
            - [Debugging Controls](#debugging-controls)
        -  [Error Checking](#error-checking)
            - [Pedestrian Path Spline Errors](#pedestrian-path-spline-errors)
            - [NPC Errors](#npc-errors)
             - [Spawner Errors](#spawner-errors)
             - [Traffic Pole Errors](#traffic-pole-errors)
            - [Master Sim Controller Errors](#master-sim-controller-errors)
            -  [Nav Mesh Bounds Volume Errors](#nav-mesh-bounds-volume-errors)
- [Support and Community](#support-and-community)


<br/>

## <a id="bring-realistic-traffic-to-your-unreal-engine-projects"></a>Bring Realistic Traffic to Your Unreal Engine Projects

Unleash the full potential of your Unreal Engine projects with the **Intelligent Traffic System (ITS)**. Whether you're a seasoned developer or just starting your journey, this innovative system is designed for accessibility and performance. ITS brings lifelike traffic simulations to your scenes with AI-controlled vehicles driven by Behavior Trees, ensuring adaptive speed, steering, and realistic interactions.

Create convincing intersections with a fully functional traffic light system, complete with pedestrians who engage with AI vehicles at traffic lights, breathing life into your virtual world. Fine-tune your traffic settings in real-time with an intuitive menu, all without the need for advanced programming skills.

This package includes low poly vehicles, city buildings, and props, guaranteeing smooth performance even on less powerful PCs. ITS offers a unique community-driven approach, where your voice matters.

Join our Discord community to shape the future of ITS through your ideas and feedback. Elevate your Unreal Engine projects with the Intelligent Traffic System and experience the immersive realism of traffic simulations.

Take the first step toward creating vibrant urban environments in your projects with the Intelligent Traffic System. Utilize its robust capabilities, including versatile parking options, working vehicle lights, and error-free handling, all integrated into Unreal Engine with blueprint-based simplicity. Our AI vehicles, driven by Behavior Trees, bring the road to life, adapting to traffic conditions dynamically. The authentic intersections, complete with pedestrian interactions, make your scenes more engaging and believable. Enjoy low poly assets that ensure smooth performance on a wide range of hardware, enabling a broader audience to experience your creations. With community-driven updates, you have a say in shaping the future of ITS. Join our official Discord community to influence upcoming features and share your insights. Elevate your Unreal Engine projects and bring urban environments to life with the Intelligent Traffic System. Try it today and experience traffic simulations like never before.

## <a id="key-features"></a>Key Features

*   **Realistic Traffic Interactions:** Watch as AI-controlled vehicles adjust their speed, steering, and braking based on spline curve angles and vehicle speed for an authentic traffic flow.
*   **Adaptive Lane Changing:** Our system intelligently calculates safe opportunities for AI vehicles to change lanes.
*   **Authentic Intersections:** Create convincing intersections with a fully functional traffic light system.
*   **Collision Avoidance:** AI vehicles intelligently dodge accidents, adding authenticity to your scenes.
*   **Pedestrian Engagement:** Experience realistic interactions between pedestrians and AI vehicles.
*   **Simple Real-Time Tweaks:** Fine-tune traffic settings with an intuitive traffic menu – no advanced programming skills needed.
*   **Low Poly Assets Included:** The package features low poly vehicles, city buildings, and props for accessible and efficient scene creation.
*   **Effortless Error Handling:** Stuck vehicles are seamlessly teleported to empty parking spots for a smooth traffic flow.
*   **Versatile Parking Options:** Choose from two types of parking spots - one for cars that reverse when exiting and another for forward exits.
*   **Working Vehicle Lights:** AI vehicles come equipped with functioning headlights and brake lights for added realism.
*   **Utilizes Default Chaos Vehicle Plugin:** ITS uses the default Chaos vehicle plugin within Unreal Engine.
*   **Vehicle Spawn System:** Enjoy a seamlessly integrated vehicle spawn system that randomly spawns and despawns vehicles around you.
*   **Compatibility:** The ITS is designed for ease of integration into your Unreal Engine projects.

## <a id="getting-started"></a>Getting Started

### <a id="installation"></a>Installation

1.  Download the ITS plugin from our store.
2.  Place the plugin folder in your Unreal Engine project's `Plugins` directory.
3.  Enable the plugin in the Plugins window within the Unreal Editor.

### <a id="usage"></a>Usage

#### <a id="vehicle-system-setup"></a>Vehicle System Setup
1.  Create a new level.
2.  Drag the **vehicle system BP** into the level.
3.  Drag the **master sim BP** into the level (this is found in the pedestrian system blueprint folder and is used to control pedestrians in the level).
4. Both of these actors have variables to control the pedestrian and vehicle AI in the level.
5. Start placing vehicle paths. There are two types of paths: normal paths and parking spots.
6. Each path has variables that can be tweaked, e.g., setting the maximum speed, setting the next path the vehicle will take when it reaches the end of the current path.
7.  Make sure the paths reference each other properly.
8. There are also two types of parking spots: one where the vehicle simply drives forward and exits, and another where the vehicle needs to reverse to exit.
9. Drag in the traffic light actor and place them at junctions to act as traffic lights to control traffic.

#### <a id="pedestrian-system-setup"></a>Pedestrian System Setup

##### **System Setup:**

*   **Pedestrian Path Spline:**
    *   Used to specify where NPCs can walk. One or more splines must be laid out in the map to specify walkable paths. Each instance has a “Closed Loop Toggle” that toggles between a closed and an open spline.

*   **Spawners:**
    *   Spawners specify the areas where NPCs are spawned from, or relocated to. One or more spawners must be placed around the map, preferably in areas hidden from the player’s view. Ensure that there is at least one spawner inside the player region radius as only spawners inside the radius will spawn NPCs.

*   **Traffic Poles:**
    *   Traffic poles come in pairs. They use a user specified ID system to detect their pair. Each instance will contain an “ID” parameter under the “Crossing ID” section. Any NPC interacting with a traffic pole will cross to its other pair, at the correct time depending on the traffic light colour.

*  **Master Sim Controller:**
    *   The master sim is used to take in all the parameters of the pedestrian system to aid with the customisation and functionality of the tool. One instance must be placed on the map, in order to edit and interact with the system.

*   **Nav Mesh Bounds Volume:**
    *   The Nav Mesh Bounds Volume is required for the navigation invoker to build the nav mesh dynamically during run time, and it’s necessary for the NPCs to move around. Place at least one instance in the map, ensure full coverage of the pathways the NPCs can take.

##### **Project Configuration Settings:**

*   **Project Settings – Crowd Manager:**
    *   These settings control the Detour Crowd AI Controller. The “max agents” is set to 100. If more NPCs are required, the required number needs to be set. The settings can further be customised as needed.

*   **Dynamic Navigation Invoker:**
    *   Inside the `BP_Custom_Player` blueprints, in the “components” tab, the navigation invoker component can be found. The “tile generation radius” is set to 6000. If the player region radius needs to be above 6000, the tile generation radius must be set accordingly. The “tile removal radius” can also be modified accordingly.

##### <a id="ui-manual"></a>UI Manual

###### <a id="npc-controls"></a>NPC Controls

*   **NPC Count:** Number of NPCs required within the player region radius.
*   **Min and Max Walk Speed:** Each NPC will get a random walk speed between this range.
*  **NPC Colour, Colour Variation, and Randomization:**
    *   Colour sets the NPC colour, which has a deviation factor set by the variation.
    *  Randomize randomizes the colors. If true, the system will ignore the colour and variation parameters.
*  **NPC Height and Variation:**
   *  Height sets the scale of the NPC and has a deviation factor set by the variation.

###### <a id="pedestrian-crossing-controls"></a>Pedestrian Crossing Controls

*   **Traffic Light Pole:** Set this so that the pedestrians know which traffic light to follow when crossing the road.
*   **Crossing Probability:** The probability of an NPC crossing if it encounters a traffic pole in its path. For example, a 0.5 probability will mean half of the NPCs will cross at a traffic pole.

###### <a id="pedestrian-spline-controls"></a>Pedestrian Spline Controls

*   **Path Noise:** Sets the amount of noise / variation in the target positions generated along the pedestrian spline.
*   **Gap Length:** Sets the distance between each target generated along the spline path.
    *   **(Tip:** Turn on “NPC Target Visibility” in the “Debugging Controls” to see the changes reflected in-game.)

###### <a id="player-interaction-controls"></a>Player Interaction Controls

*   **Player Region Radius:** The region around the player inside which all NPCs are supposed to exist. If they go outside this radius, they get relocated to one of the spawners inside the radius.
*  **Player Look At Radius:** The radius around the NPC that the player must be inside, for the NPC to look at / notice the player.
*   **NPC Scare Radius:** The radius around the NPC that the player must be inside, to trigger the NPC interaction animations.

######  <a id="debugging-controls"></a>Debugging Controls

*   **Player Walk Speed:** Sets player walk speed. Useful for moving fast across the map for debugging purposes.
*  **Spawner Visibility In Game:** If true, all spawners on the map will be visible during runtime. If false, they will be hidden in game.
*  **NPC Target Visibility In Game:** If true, all targets generated along the pedestrian spline paths will be visible during runtime. If false, they will be hidden in game.
*  **Player Region Radius Debug:** If true, will draw a debug sphere for the player region radius.
*   **NPC Scare Radius Debug:** If true, will draw a debug sphere for the NPC scare radius.
*    **NPC Look At Radius Debug:** If true, will draw a debug sphere for the NPC look at radius.

#### <a id="error-checking"></a>Error Checking
#####   <a id="pedestrian-path-spline-errors"></a>Pedestrian Path Spline Errors
*   “No Pedestrian paths found on the map!!! Place them to specify where the NPCs can walk.”

#####  <a id="npc-errors"></a>NPC Errors
*   “Min Walk Speed is greater than Max Walk Speed! To ensure proper working of the system, assign appropriate values.”

#####  <a id="spawner-errors"></a>Spawner Errors
*   “There are no spawners in the spawner range! Place spawners inside the range or increase the player region radius.”
*   “NPC Spawning Aborted!!! Could not spawn the specified NPC Count because collision was detected multiple times!” – It means the system tried to spawn too many NPCs per spawner, in a small radius, resulting in heavy collision between all of them. So spawning was aborted to prevent abnormal intersecting between the NPCs themselves and also the ground. To prevent this, either increase the number of spawners within the player region radius or decrease the NPC count.

#####  <a id="traffic-pole-errors"></a>Traffic Pole Errors

*   “{Pedestrian crossing} has no ID specified.”
*   “{ID} ID found less than 2 times! Cannot make a traffic pole pair. ID found in {pedestrian crossing}”
*   “{ID} ID found more than 2 times! Only 2 is required to make a pedestrian crossing pair. ID found in {pedestrian crossing}”

#####   <a id="master-sim-controller-errors"></a>Master Sim Controller Errors
*   "0 instances of BP_Master_Sim is present on the map. Please place one to ensure proper working of the system.”
*   “More than 1 instance of BP_Master_Sim is present on the map. Place make sure only one is present to ensure proper working of the system.”

#####   <a id="nav-mesh-bounds-volume-errors"></a>Nav Mesh Bounds Volume Errors
*   “No Nav Mesh Bounds Volume found! Add one to the map to ensure proper working of the system.”


## <a id="support-and-community"></a>Support and Community

For support, feature requests, and to share your creations, please join our Discord community: [Your Discord Link Here]

We value your feedback and are committed to making ITS the best traffic simulation solution for Unreal Engine.
