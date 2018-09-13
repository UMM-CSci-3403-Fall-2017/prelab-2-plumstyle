# Leak report

_Use this document to describe whatever memory leaks you find in `clean_whitespace.c` and how you might fix them. You should also probably remove this explanatory text._

==28140== Memcheck, a memory error detector
==28140== Copyright (C) 2002-2015, and GNU GPL'd, by Julian Seward et al.
==28140== Using Valgrind-3.12.0 and LibVEX; rerun with -h for copyright info
==28140== Command: ./check_whitespace
==28140== 
--28140-- Valgrind options:
--28140--    --leak-check=full
--28140--    -v
--28140-- Contents of /proc/version:
--28140--   Linux version 4.12.8-200.fc25.x86_64 (mockbuild@bkernel01.phx2.fedoraproject.org) (gcc version 6.4.1 20170727 (Red Hat 6.4.1-1) (GCC) ) #1 SMP Thu Aug 17 15:39:27 UTC 2017
--28140-- 
--28140-- Arch and hwcaps: AMD64, LittleEndian, amd64-cx16-lzcnt-rdtscp-sse3-avx-avx2-bmi
--28140-- Page sizes: currently 4096, max supported 4096
--28140-- Valgrind library directory: /usr/lib64/valgrind
--28140-- Reading syms from /home/anxxx154/CSCI3403/prelab-2-plumstyle/check_whitespace
--28140-- Reading syms from /usr/lib64/ld-2.24.so
--28140-- Reading syms from /usr/lib64/valgrind/memcheck-amd64-linux
--28140--    object doesn't have a symbol table
--28140--    object doesn't have a dynamic symbol table
--28140-- Scheduler: using generic scheduler lock implementation.
--28140-- Reading suppressions file: /usr/lib64/valgrind/default.supp
==28140== embedded gdbserver: reading from /tmp/vgdb-pipe-from-vgdb-to-28140-by-anxxx154-on-falcon.morris.umn.edu
==28140== embedded gdbserver: writing to   /tmp/vgdb-pipe-to-vgdb-from-28140-by-anxxx154-on-falcon.morris.umn.edu
==28140== embedded gdbserver: shared mem   /tmp/vgdb-pipe-shared-mem-vgdb-28140-by-anxxx154-on-falcon.morris.umn.edu
==28140== 
==28140== TO CONTROL THIS PROCESS USING vgdb (which you probably
==28140== don't want to do, unless you know exactly what you're doing,
==28140== or are doing some strange experiment):
==28140==   /usr/lib64/valgrind/../../bin/vgdb --pid=28140 ...command...
==28140== 
==28140== TO DEBUG THIS PROCESS USING GDB: start GDB like this
==28140==   /path/to/gdb ./check_whitespace
==28140== and then give GDB the following command
==28140==   target remote | /usr/lib64/valgrind/../../bin/vgdb --pid=28140
==28140== --pid is optional if only one valgrind process is running
==28140== 
--28140-- REDIR: 0x401d880 (ld-linux-x86-64.so.2:strlen) redirected to 0x3809fd01 (???)
--28140-- REDIR: 0x401c130 (ld-linux-x86-64.so.2:index) redirected to 0x3809fd1b (???)
--28140-- Reading syms from /usr/lib64/valgrind/vgpreload_core-amd64-linux.so
--28140-- Reading syms from /usr/lib64/valgrind/vgpreload_memcheck-amd64-linux.so
==28140== WARNING: new redirection conflicts with existing -- ignoring it
--28140--     old: 0x0401d880 (strlen              ) R-> (0000.0) 0x3809fd01 ???
--28140--     new: 0x0401d880 (strlen              ) R-> (2007.0) 0x04c30c70 strlen
--28140-- REDIR: 0x401c350 (ld-linux-x86-64.so.2:strcmp) redirected to 0x4c31d70 (strcmp)
--28140-- REDIR: 0x401e390 (ld-linux-x86-64.so.2:mempcpy) redirected to 0x4c35140 (mempcpy)
--28140-- Reading syms from /usr/lib64/libc-2.24.so
--28140-- REDIR: 0x4ecb160 (libc.so.6:strcasecmp) redirected to 0x4a28752 (_vgnU_ifunc_wrapper)
--28140-- REDIR: 0x4ec6ac0 (libc.so.6:strcspn) redirected to 0x4a28752 (_vgnU_ifunc_wrapper)
--28140-- REDIR: 0x4ecd450 (libc.so.6:strncasecmp) redirected to 0x4a28752 (_vgnU_ifunc_wrapper)
--28140-- REDIR: 0x4ec8f30 (libc.so.6:strpbrk) redirected to 0x4a28752 (_vgnU_ifunc_wrapper)
--28140-- REDIR: 0x4ec92c0 (libc.so.6:strspn) redirected to 0x4a28752 (_vgnU_ifunc_wrapper)
--28140-- REDIR: 0x4eca7d0 (libc.so.6:memmove) redirected to 0x4a28752 (_vgnU_ifunc_wrapper)
--28140-- REDIR: 0x4ec8c40 (libc.so.6:rindex) redirected to 0x4c30600 (rindex)
--28140-- REDIR: 0x4ec6f60 (libc.so.6:strlen) redirected to 0x4c30bb0 (strlen)
--28140-- REDIR: 0x4ec0a80 (libc.so.6:calloc) redirected to 0x4c2f9ca (calloc)
--28140-- REDIR: 0x4ec5510 (libc.so.6:strcmp) redirected to 0x4a28752 (_vgnU_ifunc_wrapper)
--28140-- REDIR: 0x4eda600 (libc.so.6:__strcmp_sse2_unaligned) redirected to 0x4c31c30 (strcmp)
--28140-- REDIR: 0x4ed1500 (libc.so.6:strchrnul) redirected to 0x4c34c70 (strchrnul)
--28140-- REDIR: 0x4ebfe60 (libc.so.6:malloc) redirected to 0x4c2db2f (malloc)
--28140-- REDIR: 0x4eca8c0 (libc.so.6:__GI_mempcpy) redirected to 0x4c34e70 (__GI_mempcpy)
The string 'Morris' is clean.
The string '  stuff' is NOT clean.
The string 'Minnesota' is clean.
The string 'nonsense  ' is NOT clean.
The string 'USA' is clean.
The string '   ' is NOT clean.
The string '     silliness    ' is NOT clean.
--28140-- REDIR: 0x4ec0210 (libc.so.6:free) redirected to 0x4c2ecdc (free)
==28140== 
==28140== HEAP SUMMARY:
==28140==     in use at exit: 46 bytes in 6 blocks
==28140==   total heap usage: 7 allocs, 1 frees, 1,070 bytes allocated
==28140== 
==28140== Searching for pointers to 6 not-freed blocks
==28140== Checked 66,408 bytes
==28140== 
==28140== 46 bytes in 6 blocks are definitely lost in loss record 1 of 1
==28140==    at 0x4C2FA50: calloc (vg_replace_malloc.c:711)
==28140==    by 0x400678: strip (check_whitespace.c:41)
==28140==    by 0x4006E3: is_clean (check_whitespace.c:62)
==28140==    by 0x40076B: main (check_whitespace.c:87)
==28140== 
==28140== LEAK SUMMARY:
==28140==    definitely lost: 46 bytes in 6 blocks
==28140==    indirectly lost: 0 bytes in 0 blocks
==28140==      possibly lost: 0 bytes in 0 blocks
==28140==    still reachable: 0 bytes in 0 blocks
==28140==         suppressed: 0 bytes in 0 blocks
==28140== 
==28140== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 0 from 0)
==28140== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 0 from 0)
