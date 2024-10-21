# n-queens-benchmark

```
apt install libomp-16-dev
gcc -fopenmp -o nqueens nqueens.c
```

Running using 4 threads

```
root@explorer:~# perf stat -B -e cache-references,cache-misses,cycles,instructions,branches,faults,migrations taskset --cpu-list 0-3 ./q 4
Using 4 thread(s).
Elapsed time (hh:mm:ss:cs):  7.50
 Performance counter stats for 'taskset --cpu-list 0-3 ./q 4':

           231,480      cache-references
            61,767      cache-misses              #   26.684 % of all cache refs
    25,488,987,626      cycles
    31,986,113,200      instructions              #    1.25  insn per cycle
     3,022,895,600      branches
               158      faults
                 1      migrations

       3.195841208 seconds time elapsed

       7.496717000 seconds user
       0.004004000 seconds sys
```

For MacOS

```
# use #include "/opt/homebrew/Cellar/libomp/19.1.2/include/omp.h" instead of #include <omp.h>
brew install libomp
/opt/homebrew/Cellar/gcc/14.2.0/bin/g++-14 -fopenmp nqueens.c -o nqueens
```
