Fragmentation is a phenomenon that occurs with dynamic heap allocation, where because free memory is broken and freed based on the needs of the program, it might reach a stage where the memory is fragmented and present as multiple parts. The problem with this is the whenever memory is allocated for something, a *contiguous* array of memory must be allocated. But because memory is fragmented, it will not be able to find a continuous block of memory, even if there is enough space.

![[Pasted image 20240822104755.png]]

One way to overcome this is to use virtual memory. Virtual memory makes the program think that non contiguous spaces of memory is contiguous, making the program use the different fragments.
In virtual memory speak, these fragments are called pages, and these pages are used together to form the 'contiguous' memory. Virtual memory is generally not used in games due to the overhead cost incurred by it.

Another way to overcome is to [[Defragmentation and Relocation|Defragment]]

[[Stack Allocator|Stack Allocators]] by their nature cannot get fragmented. [[Pool Allocator|Pool Allocators]], while they do get fragmented (by nature they are fragmented), never fail in allocating contiguous memory, as all fragments are of the same size.