An Iterator is a method to sequentially access the elements in a container, while also making sure that all elements are eventually accessed.
### What is the necessity?
- If one can access the container and go through them using a loop, why use an iterator?
- Its because of encapsulation. Any container needs to hide its internal working, without exposing it to the outside world. An Iterator would be a 'friend' to the class, and would handle creating a sequence to go through by its own.
- Also, an iterator would simplify the process, as all we would do is access them like its an array, even if it is doing a depth first left to right traversal of a tree.
- Also, iterators would be built for efficiency. Using loops can lead to unoptimized access of elements.