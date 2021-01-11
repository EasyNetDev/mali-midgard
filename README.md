# mali-midgard
Mali T6xx T7xx DKMS drivers for Debian Buster (based on Mali 16.0 Debian packages)

## Porting
I'm trying to fix the Mali OpenSource code to be ported to newer kernel versions (5.0 and up).
Issues I've faced:
- function `void *dma_buf_kmap(struct dma_buf *dmabuf, unsigned long page_num)` and `void dma_buf_kunmap(struct dma_buf *, unsigned long, void *);` were removed from Kernel 5.6. So I had to move the code to dma_buf_vmap and dma_buf_vunmap.
- fixing a lot of `case` statements to avoid `warning: this statement may fall through`. The original code had missing `brake` in the code in `backend/gpu/mali_kbase_jm_rb.c`
- fixing `snprintf(str, size, "%u", fence->seqno);` to `snprintf(str, size, "%lu", fence->seqno);` in `mali_kbase_fence.c`
- moved from `vm_insert_pfn` function to `vmf_insert_pfn` in `mali_kbase_mem_linux.c` 


At this point I don't know how to replace this function for Kernels >= 5.6.
