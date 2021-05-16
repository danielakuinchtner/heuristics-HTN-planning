# heuristics-HTN-planning


## Reunião 07/05

- Objetivo geral:
Usar as informações heurísticas para melhorar a performance de solvers HTN com progression search.

- Ler e entender o paper *A Generic Method to Guide HTN Progression Search with Classical Heuristics* dos autores Daniel Holler, Pascal Bercher, Gregor Behnke, Susanne Biundo.

- Entender o algoritmo, entender como essas heurísticas bases são usadas (hAad, hFF, hLM-cut), como cada método faz a escolha, o quanto essa escolha importa, o quanto a ordem da *fringe* importa.

- Escolher um domínio, por exemplo Woodworking, para reproduzir os resultados do paper. Rodar o domínio com as diferentes heurísticas.

- Após entender o código e reproduzir os resultados, podemos pensar em como melhorá-lo.

## Requirements PANDA

1) [pandaPIparser](https://github.com/panda-planner-dev/pandaPIparser):
```bash
$ sudo apt install g++ make flex bison
$ make -j
```
Obs.: The C++ compiler needs to support C++17.

2) [pandaPIgrounder](https://github.com/panda-planner-dev/pandaPIgrounder):
```bash
$ sudo apto install zip gengetopt 
$ cd pandaPIgrounder
$ git submodule init
$ git submodule update
$ cd cpddl
$ make boruvka opts bliss lpsolve
$ make
$ cd ../src
$ make
```

3) [pandaPIengine](https://github.com/panda-planner-dev/pandaPIengine):
```bash
$ cd pandaPIengine
$ mkdir build
$ cd build
$ cmake ../src
$ make -j
```

## Running overview

Examples:

```bash
$ ./pandaPIParser/pandaPIParser ipc2020-domains/total-order/Transport/domain.hddl ipc2020-domains/total-order/Transport/pfile01.hddl transport.htn 
$ ./pandaPIgrounder/pandaPIgrounder transport.htn transport.sas
$ ./build/pandaPIengine transport.sas 
```

```bash
$ ./pandaPIParser/pandaPIParser domains/total-order/UM-Translog/domain.hddl domains/total-order/UM-Translog/14-A-RegularTruck-2Regions.hddl um-translog.htn 
$ ./pandaPIgrounder/pandaPIgrounder um-translog.htn um-translog.sas
$ ./build/pandaPIengine um-translog.sas 
```

```bash
$ ./pandaPIParser/pandaPIParser ipc2020-domains/total-order/Towers/domain.hddl ipc2020-domains/total-order/Towers/pfile_01.hddl towers.htn 
$ ./pandaPIgrounder/pandaPIgrounder towers.htn towers.sas
$ ./build/pandaPIengine towers.sas 
```

## Reunião 21/05
