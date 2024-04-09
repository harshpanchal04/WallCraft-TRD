<h1>Technical Requirement Document</h1>h1>

**###WallCraft Meta Quest Application**

**##Objective**
1. Create an application which can detect walls.
2. Allow users to select a wall panel from a list of wall panel designs and superimpose it over the vertical walls excluding other objects in the room.

**##Assumptions**
1. Users will possess a Meta Quest headset compatible with the application.
2. Users have a basic understanding of how to operate the Meta Quest controllers. 
3. A stable internet connection is available for potential online functionality

**##Constraints**
1. The application's initial focus will be on vertical wall surfaces, excluding floors, ceilings, and slanted surfaces. 
2. The initial range of wall panel designs will be limited based on data storage and processing considerations.
Focus
Environment Scanning and Plane Detection.
Wall Segmentation and Object Exclusion.
Wall Panel Selection UI Selection. 
Mixed Reality Visualisation.
Technical Documentation
Approach
Environment Scanning and Plane Detection:
Using Meta Quest's built-in plane detection capabilities (using XRPlaneSubsystem class from XR Plugin) to identify vertical surfaces (walls) within the user's environment. 
Wall Segmentation and Object Exclusion:
Implement spatial mapping (creating mesh representation) to create a mesh representation of the room.
 Implement image segmentation to differentiate between walls and other objects based on colour or texture information.

Wall Panel UI Selection:
Utilise Unity's built-in UI toolkit (Unity UI) to create the carousel and other UI elements. Prefabs and UI components can simplify the process.
Integrate user interaction features for seamless selection of desired designs.

Mixed Reality Visualisation :
Implement image segmentation (if textures are available for the environment) to differentiate between walls and other objects based on colour or texture information.
Utilise image registration techniques(using Unity's built-in functionalities for image registration like custom shaders and culling) to map the chosen wall panel texture onto these planes.
To ensure only visible portions of the walls are covered by the texture, implement culling techniques (using backface culling discard polygons facing away from the viewer, as they won't be visible in the final rendering to achieve standard optimization.).
Pseudocode
