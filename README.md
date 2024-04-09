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
<br>
function VisualizeWallPanel(environmentMesh, selectedPanel)

   **Step 1: Identify Walls**
  // - Leverage the spatial mapping capabilities of the SDK to detect planar surfaces in the environment mesh.
  // - Store the detected planes, representing potential walls, in the wallPlanes variable.
  
  wallPlanes = DetectPlanes(environmentMesh) // Call a function provided by the SDK for plane detection.

  // **Step 2: Segment Walls **
  // - If necessary, refine the wall detection by isolating wall planes from other objects or clutter in the mesh.
  // - This step might involve computer vision techniques or additional filtering.
  
  segmentedWalls = SegmentWalls(wallPlanes, environmentMesh) // Call a function to filter or segment walls, if needed.

   **Step 3: Apply Wall Panel Texture**
  // - Iterate through each segmented wall plane:
  for each wallPlane in segmentedWalls:
      // - Apply the selected wall panel texture onto the current wall plane.
      // - Align the texture accurately using image registration techniques.
      RegisterTexture(selectedPanel, wallPlane) // Map the texture onto the wall, aligning edges/features.

      // - Exclude regions of the wall that shouldn't be covered by the texture (occlusion culling).
      CullInvisibleRegions(wallPlane) // Hide parts of the wall behind objects or outside the viewable area.

  // **Step 4: Render Augmented View**
  // - Render the final scene, combining the real-world environment mesh with the virtual walls and applied textures.
  // - Ensure a seamless blending of virtual elements into the physical space.
  RenderEnvironment(environmentMesh, segmentedWalls) // Render the scene with both real and virtual elements.

end function
