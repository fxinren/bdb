# BerkeleyDB 5.3.28 
	from https://github.com/berkeleydb/libdb/releases/tag/v5.3.28

### Patch for Linux:
	sed -i 's/\(__atomic_compare_exchange\)/\1_db/' src/dbinc/atomic.h

### Patch for maxOS:
	sed -i 's/\(__atomic_compare_exchange\)/\1_db/' src/dbinc/atomic.h

    vi src/dbinc/atomic.h

    line 73:
    #define	atomic_init(p, val)	((p)->value = (val))

    #if !defined(__cplusplus)
    #define	atomic_init(p, val)	((p)->value = (val))
    #endif
