IPS ARCH PROJECT
======================

![Sample Source Image](https://i.imgur.com/40Bvuur.png)

## Part #1, Brightness and Contrast Adjustments with x87 Instructions


![Brightness and Contrast Sample](https://i.imgur.com/ezN6oDV.png)

The overall formula is

```C
// ...
channel_value = (unsigned char) (channel_value * contrast + brightness);
```

The image is represented as an array of pixel color values. Every pixel is
represented as three-byte integers with channel values ranging from 0 to 255.


![BMP Image Structure](https://i.imgur.com/CKrcD9u.png)


## Part #2, Brightness and Contrast Adjustments with SIMD AVX-512 Instructions

This part accelerates assembly solution by utilizing the
AVX-512 SIMD instructions and registers ZMM0-ZMM31. Vector registers allows
to perform one instruction on multiple parts of one register at the same time in
parallel. 16 floating-point values are packed into one register
for up to 5 pixels and performs multiplication and addition on all of them at the
same time. Then it storesthe result back to memory.

## Part #3, The Sepia Filter

This part accelerates a C function that applies the Sepia filter.
The Sepia filter converts a color image to a duotone image with a dark
Brown-Gray color as explained in the following [paper](https://software.intel.com/en-us/articles/image-processing-acceleration-techniques-using-intel-streaming-simd-extensions-and-intel-advanced-vector-extensions)
written by Petter Larsson and Eric Palmer. You can also find out the weights to
use for the three color channels to apply the filter. The same approach is used to
speed-up the solution as in the second part of the project.

### x86 ISA

* [Intel x86 Software Developer Manuals](https://software.intel.com/en-us/articles/intel-sdm)
* [System V AMD64 ABI](https://software.intel.com/sites/default/files/article/402129/mpx-linux64-abi.pdf)
* [X86 Opcode Reference](http://ref.x86asm.net/index.html)
* [X86 Instruction Reference](http://www.felixcloutier.com/x86)
* [Optimizing Subroutines in Assembly Language](http://www.agner.org/optimize/optimizing_assembly.pdf)
* [Jump Quick Reference](http://unixwiz.net/techtips/x86-jumps.html)
* [SIMD Basics](https://www.codeproject.com/Articles/874396/Crunching-Numbers-with-AVX-and-AVX)
* [SIMD Intrinsics Guide](https://software.intel.com/sites/landingpage/IntrinsicsGuide)

### Assemblers

* [Linux assemblers: A comparison of GAS and NASM](https://www.ibm.com/developerworks/library/l-gas-nasm/index.html)
* [GAS Syntax](https://en.wikibooks.org/wiki/X86_Assembly/GAS_Syntax)

## Books

* C Programming: A Modern Approach, 2nd Edition by K. N. King
* Assembly Language for x86 Processors, 7th Edition by Kip R. Irvine

