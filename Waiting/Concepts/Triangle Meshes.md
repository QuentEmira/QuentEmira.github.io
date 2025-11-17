Triangle Meshes are used by Game engines to represent 3D surfaces. Now, in general, every object is represented in a scene by rendering only their surface. To do this effectively, and to be able to represent different kinds of surfaces, triangle meshes are used.

## Why Triangles?
Triangle are used in triangle meshes for the following reasons:
- There is no simpler polygon other than a Triangle. One cannot form a polygon with two line segments, without curving one of them.
- Second, Triangles remain planar. Other polygon of four or more vertices can be non planar.
- Triangles remain triangles after transformation. At most, they can degenerate to a line segment.
- Triangles have been used for a very long time.