# ccalloc
A fast mmap based C++ memory allocator

__ccalloc__ is a fast mmap based memory allocator which overloads the default C++ new/delete operators.
It is fully implemented in __C++11__ and __pthreads__. The allocation trategy is bucket allocation with no free lists and
per thread independent allocation buckets. The performance is on par with __ptmalloc__ in bulk small object allocations.
Different from traditional allocators __ccalloc__ passes through only clean zeroed memory to the application eliminating
non-initialized data issues. Because __ccalloc__ is not managing free lists it is much more stable and scales much better for multi-threaded
applications. Long running single threaded applications are not well suited. For maximum performance you should at least use a dual core system.
valgrind support is included.

To use __ccalloc__ in your C++ applications simple drop the source files into your project and add them to your Makefile/project file.
The only tunable parameter is `CC_MEM_PAGE_PREALLOC` in Memory.cc. Set it to one for 1 for maximum security or to a greater number
for maximum performance.

Let me know if you like it!

----

Frank Mertens
<frank@cyblogic.de>
