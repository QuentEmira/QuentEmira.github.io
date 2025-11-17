A game has multiple subsystems, which each have dependencies on other subsystems. Because of this, it is important the subsystems are started up and shut down in the right order. If they are not, it could lead to a situation where a subsystem is activated before its dependencies are, leading to the system crashing.

In C++ and C#, constructors and destructors are called in a random order. This is not good based on the above situation. We will need to be able to control the order of subsystem startup and shutdown.

There is one approach to solve this. The author calls it the Brute Force approach. In this approach, you make sure that the constructor and destructor for each subsystem do nothing, and then create separate functions for starting up and shutting down. After this, you call these functions in the order you want.
![[Pasted image 20240822124658.png]]![[Pasted image 20240822124721.png]]![[Pasted image 20240822124746.png]]![[Pasted image 20240822124804.png]]
