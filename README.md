[![Binder](https://mybinder.org/badge.svg)](https://mybinder.org/v2/gh/gitesei/willard-chandler/master)

# Willard-Chandler Instantaneous Interface Calculator
Python-based tool to calculate instantaneous interfaces and concentration/orientation profiles from molecular simulation trajectories in slab geometry.

![](data/nglviewer.gif)

The method is described by A.P. Willard and D. Chandler in [_Instantaneous Liquid Interfaces_](https://pubs.acs.org/doi/10.1021/jp909219k) [1]. The tool uses the Lewiner marching cubes algorithm [2] and is partly an adaptation of the willard-chandler module of the [`pytim` code](https://github.com/Marcello-Sega/pytim) [3] with the addition of a routine to calculate the orientational distribution of free O-H groups at the interface [4].

# Usage

The Jupyter Notebook `example.ipynb` shows how to use the code to analyze and visualize the interfaces of a NaSCN aqueous solution in slab geometry.

### On the command line

To calculate concentration profiles, orientational distributions of linear ions and free OH groups w.r.t. the rough instantaneous interface:

python ./willardchandler.py -s TOPOLOGY -t TRAJECTORY -o OUTPUT PICKLE FILE -b FIRST FRAME -e FRAME INTERVAL -m MOLECULES -l LAYERS

for example (NaSCN aqueous solution)

python ./willardchandler.py -s npt.gro -t npt.xtc -o out.p -b 1000 -e 10 -m 'H1 O' 'NA' 'S1 C2 N3' -l -0.1 0.1 0.3 0.5

To calculate concentration profiles, orientational distributions of linear ions and free OH groups w.r.t. the planar Gibbs dividing surface:

python ./gds.py -s TOPOLOGY -t TRAJECTORY -o OUTPUT PICKLE FILE -b FIRST FRAME -e FRAME INTERVAL -m MOLECULES -l LAYERS

for example (NaSCN aqueous solution)

python ./willardchandler.py -s npt.gro -t npt.xtc -o out.p -b 1000 -e 10 -m 'H1 O' 'NA' 'S1 C2 N3' -l -0.1 0.1 0.3 0.5

# References

1. A. P. Willard and D. Chandler, “Instantaneous liquid interfaces”, The Journal of Physical Chemistry B 114, 1954–1958 (2010)
2. T. Lewiner, H. Lopes, A. W. Vieira, and G. Tavares, “Efficient implementation of marching cubes' cases with topological guarantees”, Journal of Graphics Tools 8, 1–15 (2003)
3. M. Sega, G. Hantal, B. Fábián, and P. Jedlovszky, “Pytim: A python package for the interfacial analysis of molecular simulations”, Journal of Computational Chemistry 39(25), 2118–2125 (2018)
4. F. Tang, T. Ohto, T. Hasegawa, W. J. Xie, L. Xu, M. Bonn, and Y. Nagata, “Definition of free O-H groups of water at the air–water interface”, Journal of Chemical Theory and Computation 14, 357–364 (2017)
