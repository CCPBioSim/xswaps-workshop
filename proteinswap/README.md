# ProteinSwap

This will be a short tutorial on how to use the ProteinSwap method 
implemented in the `proteinswap` program that comes with [Sire](https://siremol.org) to calculate 
relative binding free energies of a ligand to two different proteins.

ProteinSwap is an efficient and theoretically robust method of predicting 
the relative binding affinities of a guest molecule (ligand) to two different host 
molecules (e.g. proteins).

For example, ProteinSwap can be used to calculate the relative binding 
free energy of a ligand to two different proteins, e.g. a wildtype and 
a mutant protein. It works by 
constructing a λ-coordinate that connects a periodic box of water 
containing the ligand bound to one protein (the `Protein0 Box`), with a 
second periodic box of water that contains a cluster of water  bound to another
protein (the `Protein1 Box`).

The λ-coordinate is similar to that in WaterSwap, and is used to swap
the ligand and water cluster between the two proteins, such that;

* at λ=0.0, the ligand is bound to protein0, and the water cluster is bound to protein1

* at λ=1.0, the ligand is bound to protein1, and the water cluster is bound to protein0

* and at λ values in between, both the ligand and water cluster are partially bound
to both proteins.

The free energy change along this proteinswap λ reaction coordinate can be
calculated using any standard free energy method, e.g. 
[free energy perturbation (FEP)](https://en.wikipedia.org/wiki/Free_energy_perturbation), 
[Bennett acceptance ratio method (BAR)](https://en.wikipedia.org/wiki/Bennett_acceptance_ratio) or 
[thermodynamic integration (TI)](https://en.wikipedia.org/wiki/Thermodynamic_integration). 
Indeed, to measure error, the proteinswap program with Sire calculates the free energy using all three methods at the same time.

## Training material

The workshop consists of a series of Jupyter notebooks. These are available below, and can be run using the [workshop Jupyter server](https://ccpbiosim.github.io/workshop/events/bristol2018/server.html).

Once you have started the server, navigate to the `xswaps/proteinswap` directory and you will find all workshop material there.

The workshops are numbered sequentially and should be followed in order. 

## Contents

### [01_running_proteinswap.ipynb](html/01_running_proteinswap.html)

How to run a proteinswap simulation

[download](01_running_proteinswap.ipynb)

### [02_understanding_output.ipynb](html/02_understanding_output.html)

How to understand the output of a proteinswap simulation

[download](02_understanding_output.ipynb)

### [03_analysis.ipynb](html/03_analysis.html)

How to analyse the outputs from proteinswap

[download](03_analysis.ipynb)

### [04_interactive_analysis.ipynb](html/04_interactive_analysis.html)

How to do a deeper analysis of the proteinswap free energy

[download](04_interactive_analysis.ipynb)

### [05_components.ipynb](html/05_components.html)

How to decompose the relative binding free energies to residue-based components, and then visualise them in 3D.

[download](05_components.ipynb)
