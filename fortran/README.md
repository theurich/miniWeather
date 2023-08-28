GJT's Derecho Exploration
=========================

Building
--------
```
mkdir BLD
cd BLD
cmake ..
make VERBOSE=1
```

Running
-------
```
qinteractive -A P93300606 --ngpus 4
cd BLD
mpiexec -n 4 ../my_get_local_rank ./miniWeather_mpi_openacc 
```
