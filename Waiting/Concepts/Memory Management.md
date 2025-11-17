These are some ideas about memory management that I learnt about.

### Dynamic Allocation
![[Dynamic Allocation]]

### Stack Allocator
![[Stack Allocator]]

### SubPoint: Heap Memory Allocation
This allocation has got nothing to do with the heap data structure. The name given to the memory space where any dynamic memory needed by the programmer is stored. The algorithm that handles memory allocation for heaps is supposedly not very efficient in nature, and can have overhead costs. Any and all memory in the heap is explicitly allocated by the programmer, and thus must be explicitly freed by the programmer.

### SubPoint: Memory Leak
A memory leak is a situation where the program written does not free memory that has been dynamically allocated. This leads to situations where the program 'forgets' that the memory existed, leading to a decrease in performance, as memory available for the program decreases. This can be handled by simply making sure to free every dynamically allotted memory.

### Double Ended Stack Allocator
![[Double-Ended Stack Allocator]]

### Pool Allocators
![[Pool Allocator]]
### Aligned Allocation
![[Aligned Allocation]]

## Single Frame and Double Buffered memory allocators
During a game loop, some or the other form of memory is used. This is generally just temporary memory needed for that frame, or memory that last for the current and the next frame. This is so common, that we have two kinds of memory allocators
### Single Frame Allocator
![[Single Frame Allocator]]

### Double Buffered Allocator
![[Double Buffered Allocator]]

## Fragmentation

![[Fragmentation]]
### Defragmentation and Relocation
![[Defragmentation and Relocation]]