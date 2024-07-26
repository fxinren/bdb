# BerkeleyDB 5.3.28 
	from https://github.com/berkeleydb/libdb/releases/tag/v5.3.28

### Patch for Linux:
	sed -i 's/\(__atomic_compare_exchange\)/\1_db/' src/dbinc/atomic.h

### Patch for maxOS:
	sed -i 's/\(__atomic_compare_exchange\)/\1_db/' src/dbinc/atomic.h
	sed -i 's/\(atomic_read\)/\1_db/' src/dbinc/atomic.h
	sed -i 's/\(atomic_init\)/\1_db/' src/dbinc/atomic.h

