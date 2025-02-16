For this, we need to understand alignment. Alignment in memory is when a certain struct can only be stored in certain memory addresses. For example, a 4 byte struct (32 bit) can only be stored in 0x0, 0x4, 0x8, and 0x12. This is generally done because of the way the memory architecture is, hardware wise. Probably, the memory reads in the form of 4 bytes at a time.

Why can't we just store it anywhere else? This is because storing it anywhere else can lead to inefficient memory access, and sometimes run time error as the hardware refuses to work. This example will explain the inefficiency:

![[Drawing 2024-08-22 09.17.00.excalidraw|1000]]

Due to the above, compiler prioritises aligning. If free space is left, it pads out the free space until the next possible memory space, and uses it from there. Because of this, it is important to properly specify the order of reserving memory for different structs.

Now, aligned allocation is just a program that accounts for alignment. The way it works is simple. Check the code below.

```cpp
// Shift the given address upwards if/as necessary to
// ensure it is aligned to the given number of bytes.
inline uintptr_t AlignAddress(uintptr_t addr, size_t align)
{
const size_t mask = align - 1;
assert((align & mask) == 0); // pwr of 2
return (addr + mask) & ~mask;
}

// Shift the given pointer upwards if/as necessary to
// ensure it is aligned to the given number of bytes.
template<typename T>
inline T* AlignPointer(T* ptr, size_t align)

{

const uintptr_t addr = reinterpret_cast<uintptr_t>(ptr);
const uintptr_t addrAligned = AlignAddress(addr, align);
return reinterpret_cast<T*>(addrAligned);

}

// Aligned allocation function. IMPORTANT: 'align'
// must be a power of 2 (typically 4, 8 or 16).
void* AllocAligned(size_t bytes, size_t align)
{
// Allocate 'align' more bytes than we need.
size_t actualBytes = bytes + align;

// Allocate unaligned block.
U8* pRawMem = new U8[actualBytes];

// Align the block. If no alignment occurred,
// shift it up the full 'align' bytes so we
// always have room to store the shift.
U8* pAlignedMem = AlignPointer(pRawMem, align);
if (pAlignedMem == pRawMem)
pAlignedMem += align;

// Determine the shift, and store it.
// (This works for up to 256-byte alignment.)
ptrdiff_t shift = pAlignedMem - pRawMem;
assert(shift > 0 && shift <= 256);

pAlignedMem[-1] = static_cast<U8>(shift & 0xFF);

return pAlignedMem;

}
```

Lets look at each function
```cpp
inline uintptr_t AlignAddress(uintptr_t addr, size_t align)
{
const size_t mask = align - 1;
assert((align & mask) == 0); // pwr of 2
return (addr + mask) & ~mask;
}
```

This is where the magic happens. This function finds the next viable address, given the current address and align size. Read the below to understand why:
1. First, realize that the align value will always be a power of 2. This means its 2, 4, 8, 16 and so on. This also means the binary value of align would always be 10..0 (a 1 followed by 0's).
2. Second, to get an address that is a multiple of the align, all we need to make sure is that the $log_2(align)$ least significant bits are 0. So, for align = 16, $log_2(16) = 4$, so we need to make sure the 4 least significant bits are 0. 16 -> 10000.
3. The function does this. First, it creates a mask, that is one less than the align. The number one less than the align has all the least significant bits that we focus on be one. For 16 -> 10000, 15 -> 01111.
4. Next, it makes sure that align is a power of two, as bitwise and of a power of 2, and one less of that is always 1.
5. Finally, to get the new address, the mask is added to the address, pushing the current address above the next viable address, if it was not above it already. Then, we bitwise and it with the inverse of the mask, where the least significant bits we focus on now will become 0.
6. Thus, we get the new address.

```cpp
template<typename T>
inline T* AlignPointer(T* ptr, size_t align)

{

const uintptr_t addr = reinterpret_cast<uintptr_t>(ptr);
const uintptr_t addrAligned = AlignAddress(addr, align);
return reinterpret_cast<T*>(addrAligned);

}
```

Next, is this function. It just converts the pointer into an integer to pass to the previously explained function and thus be able to manipulate the value of the pointer.

```cpp
// Aligned allocation function. IMPORTANT: 'align'
// must be a power of 2 (typically 4, 8 or 16).
void* AllocAligned(size_t bytes, size_t align)
{
// Allocate 'align' more bytes than we need.
size_t actualBytes = bytes + align;

// Allocate unaligned block.
U8* pRawMem = new U8[actualBytes];

// Align the block. If no alignment occurred,
// shift it up the full 'align' bytes so we
// always have room to store the shift.
U8* pAlignedMem = AlignPointer(pRawMem, align);
if (pAlignedMem == pRawMem)
pAlignedMem += align;

// Determine the shift, and store it.
// (This works for up to 256-byte alignment.)
ptrdiff_t shift = pAlignedMem - pRawMem;
assert(shift > 0 && shift <= 256);

pAlignedMem[-1] = static_cast<U8>(shift & 0xFF);

return pAlignedMem;

}```

Here, what the function does is to allocate memory based on the bytes needed and align. This program first calculates the amount of space to be aligned, which would be the free space until the next viable align, and then the bytes. For this, the first two lines within the function help. Then, if the aligned pointer is equal to the actual pointer, the aligned pointer is shifted up by alignment. This is because when it comes to freeing the aligned memory back, we need to know the actual size of the free space allocated, and thus need to store this value in a location. This is stored as the last byte in the aligned memory. But this would be problematic if the pointer is already aligned, at which point no shifting is necessary, but the computer won't know the difference. For this, 1 extra byte is allocated for everything, thus making sure a shift is always needed. It feels complicated and wasteful.