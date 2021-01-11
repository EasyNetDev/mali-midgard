# mali-midgard
Mali T6xx T7xx DKMS drivers for Debian Buster (based on Mali 16.0 Debian packages)

## Porting 
I'm trying to fix the Mali OpenSource code to be ported to newer kernel versions. Until now I have success to port the code partially, until I've notice the function `void *dma_buf_kmap(struct dma_buf *dmabuf, unsigned long page_num)` was removed from Kernel 5.6.

At this point I don't know how to replace this function for Kernels >= 5.6.
