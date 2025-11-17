This is the architecture of the game engine that runs during runtime. The components and their relations listed below can help in remembering the different components.

![[RunTime_Game_Engine_Architecture.excalidraw|center]]

Now, lets discuss about each separate part.

## Hardware
This is in regards to the hardware that is used by the system on which the game engine works. It could be the pc one is using, the laptop, the console, mobile phone, anything.

## Drivers
These are the low level software systems that handle the hardware and its resources. They create an abstraction between the OS and the other systems, and the hardware, protecting each from the detail of the other.

## OS
The OS just refers to the operating system. This is the software that handles the applications being run, while also being able to dictate which application gets what resources. Before, in consoles, this just used to be a basic layer for the game to access the hardware, a result of which the entire hardware worked in service of the game. Nowadays, the OS is much more powerful, and the game has to play nice and listen to the OS. Due to this, the OS can just, quite literally stop a game in between if a player access the menu or something else.

## 3rd Party SDKs
These are SDK's that are part of the particular system (Windows, Mac etc.) that provide additional features and capabilities for the engine to be able to use at anytime. Some of them are:
- Physics: Havok, PhysX
- Graphics: OpenGL, Vulkan, DirectX
- Animation: Granny, Havok Animation
- Boost
- Folly
- Kynapse etc.
## Platform Independence Layer
The job of this layer is to make sure that the engine is made in such a way that it is capable of running regardless of the platform its being run on. The way it works is to take common interface functions, and wrapping them to form custom functions that the game dev can use. So while the game dev works with the custom functions, the interface function unique to the platform will be used for the lower layers.

## Core Systems
Core Systems is just a collective name for every system that would be necessary for the game engine to operate properly, software utilities vital for any game. These include:
- Assertion: Code statement that are used to force check for errors.
- Memory management: Handling memory has a huge impact.
- Network
- Localisation service
- Parsers
- Math library
## Resources
This represents all the resources that are needed for the game, such as text, meshes, textures, sprites, 3D models, font etc. Generally, a separate system is created, kind of like a database, that allows for easy access for each of these resources based on an unique identifier. This is done by a resource manager.

## Low Level Render
Next comes the rendering engine. The rendering engine has multiple parts to it, its main job being rendering the different components and their relations in the game. A basic part of the rendering engine is the Low Level Render.

The low level render is used to handle geometric primitives that will be used to render more complicated parts of the game. Geometric primitives are basic shapes, such as polygons, triangles, cones, cylinders, spheres etc. that are used to make up the game world.

This system build up the world with regard to what is part of the system, just rendering whatever is needed. There are some parts to it, such as:
- Graphics Device Interface: Graphic SDKs require a lot of code in order make available graphics device visible, set up basic render processes, etc. This is handled in the Graphics Device Interface.
- Static and Dynamic Lighting
- Texture and surface management
- Materials and Shaders
- Cameras
- Text and Fonts

## Scene Graph and Culling optimization
The previous system tries to render everything without any consideration for what is actually in the scene. What this system does is to limit the things rendered, by only rendering what is visible through the camera. The is could be as simple as just rendering anything that can be seen be the camera, or using more sophisticated methods.