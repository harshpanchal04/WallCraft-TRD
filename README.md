<h1>Technical Requirement Document</h1>

<h3>WallCraft Meta Quest Application</h3>

<h2>Objective</h2>
1. Create an application which can detect walls. <br>
2. Allow users to select a wall panel from a list of wall panel designs and superimpose it over the vertical walls excluding other objects in the room.<br>

<h2>Assumptions</h2>
1. Users will possess a Meta Quest headset compatible with the application.<br>
2. Users have a basic understanding of how to operate the Meta Quest controllers. <br>
3. A stable internet connection is available for potential online functionality<br>

<h2>COnstraints</h2>
1. The application's initial focus will be on vertical wall surfaces, excluding floors, ceilings, and slanted surfaces. <br>
2. The initial range of wall panel designs will be limited based on data storage and processing considerations.<br>

<h2>Focus</h2>
1. Environment Scanning and Plane Detection.<br>
2. Wall Segmentation and Object Exclusion.<br>
3. Wall Panel Selection UI Selection. <br>
4. Mixed Reality Visualisation.<br>

<h2>Technical Documentation</h2>

<h3>Approach</h3>

<h3>Environment Scanning and Plane Detection:</h3>
1. Using Meta Quest's built-in plane detection capabilities (using XRPlaneSubsystem class from XR Plugin) to identify vertical surfaces (walls) within the user's environment. <br>
<h3>Wall Segmentation and Object Exclusion:</h3>
2. Implement spatial mapping (creating mesh representation) to create a mesh representation of the room. <br>
 Implement image segmentation to differentiate between walls and other objects based on colour or texture information. <br>

<h3>Wall Panel UI Selection:</h3>
1. Utilise Unity's built-in UI toolkit (Unity UI) to create the carousel and other UI elements. Prefabs and UI components can simplify the process. <br>
2. Integrate user interaction features for seamless selection of desired designs. <br>

<h3>Mixed Reality Visualisation :</h3>
1. Implement image segmentation (if textures are available for the environment) to differentiate between walls and other objects based on colour or texture information. <br>
2. Utilise image registration techniques(using Unity's built-in functionalities for image registration like custom shaders and culling) to map the chosen wall panel texture onto these planes. <br>
3. To ensure only visible portions of the walls are covered by the texture, implement culling techniques (using backface culling discard polygons facing away from the viewer, as they won't be visible in the final rendering to achieve standard optimization.). <br>

<h2>Pseudocode</h2>
