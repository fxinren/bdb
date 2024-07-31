# BerkeleyDB 5.3.28 
    from https://github.com/berkeleydb/libdb/releases/tag/v5.3.28
    Final patch release of the 5.x series, last release before the license was changed to AGPLv3.

### Patch for Linux:
	sed -i 's/\(__atomic_compare_exchange\)/\1_db/' src/dbinc/atomic.h

### Patch for maxOS:
	1. sed -i 's/\(__atomic_compare_exchange\)/\1_db/' src/dbinc/atomic.h

    2. vi src/dbinc/atomic.h

    line 73:
    #define	atomic_init(p, val)	((p)->value = (val))

    change to:
    #if !defined(__cplusplus)
    #define	atomic_init(p, val)	((p)->value = (val))
    #endif

    3. vi dist/configure
    line 19147, insert:
    #include <stddef.h>

    so it looks like:
    19144               test -z "$ax_tls_defn_keyword" && continue
    19145           cat confdefs.h - <<_ACEOF >conftest.$ac_ext
    19146 /* end confdefs.h.  */
    19147 #include <stddef.h>
    19148 template <typename T>class TLSClass {
    19149               public: static  $ax_tls_decl_keyword  T *tlsvar;
    19150               };

### Patch for Windows (VS2022):
    1. vi src/dbinc/atomic.h
    line 73:
    #define	atomic_init(p, val)	((p)->value = (val))

    change to:
    #if !defined(__cplusplus)
    #define	atomic_init(p, val)	((p)->value = (val))
    #endif

    2. vi ./build_windows/db.h
    line 2816:
    #define        store(a, b)     __db_dbm_store(a, b)

    change to:
    #if !defined(__cplusplus)
    #define        store(a, b)     __db_dbm_store(a, b)
    #endif

    3. vi ./src/dbinc/win_db.h
    line 36, intert:
    #include <stdint.h>
