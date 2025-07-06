# lammps_e2

Instructivo, archivos de entrada, auxiliares y log's de la simulación del ejemplo 2,

Comandos para la ejecucion en terminal:

    gfortran micelle2d.f -o datagen  

para la normal:

    datagen < def.micelle > data.micelle
.

    less in.micelle
. para salir presiona "Q" .

    less data.micelle
.

    lmp_serial < in.micelle
.

    ovito < dump.micelle

para la extendida:

    datagen < def_2.micelle > data_2.micelle
.

    lmp_mpi < in_2.micelle
.

    ovito < dump_2.micelle 
