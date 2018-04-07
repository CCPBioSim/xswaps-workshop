# WaterSwap

This will be a short tutorial on how to use the WaterSwap method 
implemented in the `waterswap` program that comes with [Sire](https://siremol.org) to calculate 
absolute binding free energies of a ligand to a protein.

WaterSwap is an efficient and theoretically robust method of predicting 
the absolute binding affinities of a guest molecule (ligand) to a host 
molecule (e.g. protein).

For example, WaterSwap can be used to calculate the absolute binding 
free energy of a ligand to a protein. It works by 
constructing a λ-coordinate that connects a periodic box of water 
containing the ligand bound to a protein (the `Protein Box`), with a 
second periodic box of water, with some of the water molecules
identified as a water cluster (the `Water Box`).

The λ-coordinate is similar to that in ProteinSwap, and is used to swap
the ligand and water cluster between the two boxes, such that;

* at λ=0.0, the ligand is bound to the protein, and the water cluster is in bulk water

* at λ=1.0, the water cluster is bound to the protein, and the ligand is in bulk water

* and at λ values in between, both the ligand and water cluster are partially bound
to the protein and in bulk water.

The free energy change along this waterswap λ reaction coordinate can be
calculated using any standard free energy method, e.g. 
[free energy perturbation (FEP)](https://en.wikipedia.org/wiki/Free_energy_perturbation), 
[Bennett acceptance ratio method (BAR)](https://en.wikipedia.org/wiki/Bennett_acceptance_ratio) or 
[thermodynamic integration (TI)](https://en.wikipedia.org/wiki/Thermodynamic_integration). 
Indeed, to measure error, the waterswap program with Sire calculates the free energy using all three methods at the same time.

For more information and example usage, take a look at these papers;

* [Woods, CJ, Malaisree, M, Hannongbua, S & Mulholland, AJ 2011, “A water-swap reaction coordinate for the calculation of absolute protein-ligand binding free energies”. Journal of Chemical Physics, vol 134.](http://dx.doi.org/10.1063/1.3519057)
* [Woods, CJ, Malaisree, M, Michel, J, Long, B, McIntosh-Smith, S & Mulholland, AJ 2014, “Rapid decomposition and visualisation of protein-ligand binding free energies by residue and by water”. Faraday Discussions, vol 169., pp. 477-499](http://dx.doi.org/10.1039/c3fd00125c)
* [Woods, CJ, Malaisree, M, Long, BJO, McIntosh-Smith, S & Mulholland, AJ 2013, “Computational Assay of H7N9 Influenza Neuraminidase Reveals R292K Mutation Reduces Drug Binding Affinity”. Scientific Reports, vol 3.](http://dx.doi.org/10.1038/srep03561)

[Cresset's Flare](https://www.cresset-group.com/flare/) contains a graphial interface
and analysis platform for WaterSwap simulations.

## Training material

The workshop consists of a series of Jupyter notebooks. These are available below, and can be run using the [workshop Jupyter server](https://ccpbiosim.github.io/workshop/events/bristol2018/server.html).

Once you have started the server, navigate to the `xswaps/waterswap` directory and you will find all workshop material there.

The workshops are numbered sequentially and should be followed in order. 

## Contents

### [01_running_waterswap.ipynb](html/01_running_waterswap.html)

How to run a waterswap simulation

[download](01_running_waterswap.ipynb)

### [02_understanding_output.ipynb](html/02_understanding_output.html)

How to understand the output of a waterswap simulation

[download](02_understanding_output.ipynb)

### [03_analysis.ipynb](html/03_analysis.html)

How to analyse the outputs from waterswap

[download](03_analysis.ipynb)

### [04_interactive_analysis.ipynb](html/04_interactive_analysis.html)

How to do a deeper analysis of the waterswap free energy

[download](04_interactive_analysis.ipynb)

### [05_components.ipynb](html/05_components.html)

How to decompose the relative binding free energies to residue-based components, and then visualise them in 3D.

[download](05_components.ipynb)

