# heuristics-HTN-planning


## Requirements

1) [pandaPIparser](https://github.com/panda-planner-dev/pandaPIparser):
```bash
$ sudo apt install g++ make flex bison
$ make -j
```
Obs.: Your C++ compiler needs to support C++17.

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
$ ./pandaPIParser/pandaPIParser domains/total-order/SmartPhone/domain.hddl domains/total-order/SmartPhone/02-OrganizeMeeting_VerySmall.hddl smartphone.parsed 

$ ./pandaPIgrounder/pandaPIgrounder smartphone.parsed smartphone.sas

$ ./build/pandaPIengine smartphone.sas > smartphone.solution
```

```bash
$ ./pandaPIParser/pandaPIParser ipc2020-domains/total-order/Transport/domain.hddl ipc2020-domains/total-order/Transport/pfile01.hddl transport.parsed 

$ ./pandaPIgrounder/pandaPIgrounder transport.parsed transport.sas

$ ./build/pandaPIengine transport.sas > transport.solution
```

```bash
$ ./pandaPIParser/pandaPIParser ipc2020-domains/total-order/Rover-GTOHP/domain.hddl ipc2020-domains/total-order/Rover-GTOHP/p01.hddl rover.parsed 

$ ./pandaPIgrounder/pandaPIgrounder rover.parsed rover.sas

$ ./build/pandaPIengine rover.sas > rover.solution
```

```bash
$ ./pandaPIParser/pandaPIParser domains/total-order/UM-Translog/domain.hddl domains/total-order/UM-Translog/16-A-RegularTruck-4Locations.hddl um-translog.parsed

$ ./pandaPIgrounder/pandaPIgrounder um-translog.parsed um-translog.sas

$ ./build/pandaPIengine um-translog.sas > um-translog.solution
```



```bash
$ ./pandaPIParser/pandaPIParser ipc2020-domains/total-order/Towers/domain.hddl ipc2020-domains/total-order/Towers/pfile_01.hddl towers.parsed

$ ./pandaPIgrounder/pandaPIgrounder towers.parsed towers.sas

$ ./build/pandaPIengine towers.sas > towers.solution
```

```bash
$ ./pandaPIParser/pandaPIParser ipc2020-domains/total-order/Satellite-GTOHP/domain.hddl ipc2020-domains/total-order/Satellite-GTOHP/p01.hddl satellite.parsed

$ ./pandaPIgrounder/pandaPIgrounder satellite.parsed satellite.sas

$ ./build/pandaPIengine satellite.sas > satellite.solution
```

```bash
$ ./pandaPIParser/pandaPIParser ipc2020-domains/total-order/Entertainment/pfile01-domain.hddl ipc2020-domains/total-order/Entertainment/pfile01.hddl entertainment.parsed

$ ./pandaPIgrounder/pandaPIgrounder entertainment.parsed entertainment.sas

$ ./build/pandaPIengine entertainment.sas > entertainment.solution
```

```bash
$ ./pandaPIParser/pandaPIParser ipc2020-domains/partial-order/PCP/p-pcp01-domain.hddl ipc2020-domains/partial-order/PCP/p-pcp01.hddl pcp.parsed

$ ./pandaPIgrounder/pandaPIgrounder pcp.parsed pcp.sas

$ ./build/pandaPIengine pcp.sas > pcp.solution
```

```bash
$ ./pandaPIParser/pandaPIParser ipc2020-domains/total-order/Woodworking/domain.hddl ipc2020-domains/total-order/Woodworking/01--p01-complete.hddl woodworking.parsed

$ ./pandaPIgrounder/pandaPIgrounder woodworking.parsed woodworking.sas

$ ./build/pandaPIengine woodworking.sas > woodworking.solution
```

Using LM-Cut heuristic:
```bash
$ ./build/pandaPIengine --heuristic "rc2(lmc)"  um-translog.sas > um-translog.solution
```






## Reunião 07/05

- Objetivo geral:
Usar as informações heurísticas para melhorar a performance de solvers HTN com progression search.

- Ler e entender o paper *A Generic Method to Guide HTN Progression Search with Classical Heuristics* dos autores Daniel Holler, Pascal Bercher, Gregor Behnke, Susanne Biundo.

- Entender o algoritmo, entender como essas heurísticas bases são usadas (hAad, hFF, hLM-cut), como cada método faz a escolha, o quanto essa escolha importa, o quanto a ordem da *fringe* importa.

- Escolher um domínio, por exemplo Woodworking, para reproduzir os resultados do paper. Rodar o domínio com as diferentes heurísticas.

- Após entender o código e reproduzir os resultados, podemos pensar em como melhorá-lo.
