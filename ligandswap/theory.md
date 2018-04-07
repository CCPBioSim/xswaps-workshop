# Ligandswap theory
Ligandswap is based on the same underlying idea as 
waterswap, which is described in full [here](http://dx.doi.org/10.1063/1.3519057) and 
[here](http://dx.doi.org/10.1039/c3fd00125c).

The method works by constructing and connecting two simulation boxes;

* a `protein box`, which contains the protein in a periodic box of explicit water molecules,
* and a `water box`, which is just a periodic box of explicit water molecules.

Both boxes are placed into the same heat bath and connected to the same 
thermostat, meaning that they can exchange energy.

Spatially, the two boxes are placed directly on top of each other. 
Except for the exchange of energy, atoms in one box do not interact with 
atoms in the other box. Effectively, the atoms in one box are invisible 
to the atoms in the other box.

Next, two ligands are added, called ligand A and ligand B. These 
ligands *can interact* with atoms in *both* the protein box and the atoms 
in the water box. However, the two ligands *cannot interact* with one another.

An energy expression is used to calculate the total energies of both boxes. 
This energy expression uses λ to scale the interactions between both

* the atoms in ligand A with the atoms in the protein box and water box,
* and the atoms in ligand B with the atoms in the water box and protein box.

This λ reaction coordinate acts such that;

* at λ = 0.0, ligand A only interacts with the atoms in the protein box, and ligand B only interacts with the atoms in the water box,
* at λ = 1.0, ligand B only interacts with the atoms in the protein box, and ligand A only interacts with the atoms in the water box,
* and at λ values in-between, ligand A’s interactions with the protein box are scaled by (1-λ), while its interactions with the water box are scaled by λ, while ligand B’s interactions with the protein box are scaled by λ, while its interactions with the water box are scaled by (1-λ). This means that, at λ = 0.5, the atoms of ligand A and ligand B both equally interact with the atoms in both the protein box and the water box.

The effect of λ is to swap ligand A and ligand B between the protein box and water box, as shown in the figures below.

![λ=0.0](images/ligandswap00.jpg)
![λ=0.5](images/ligandswap05.jpg)
![λ=1.0](images/ligandswap10.jpg)

The energy expression is given below;

<blockquote><!--latexit:AAAFy3jahVRbbxtFGP12dtKmqds4l6ZN0zYLcYNDaeqkpC0hKbGbC2lrp+3ajpM4
mPHu2NlmvWt2x01NFDRCKBIvXCqEKgSoNQjRByigCiHuD4gXXtqkPwAJIfHAEy+8
gMT4UhEgFbNazTdnZs63850zm86bhssCgbsSknFdPStEfczOJ3x2+iLVmJvwXaKO
a9jWjI842oIhRne2bI06ts24dNOrbGvo8h3sfsjf8/ChRw4ffXTw8VOjZyIXEsmn
SeaiZeefifmsgmmub/fs2LmnfTai9tZ44z7NJK47LZBFWnRvNHqbmltad7Xt5tu5
h+/iu3k738v38f38AO+8sbdj3/4DncoDD3LEZY55Hd/Ct/J6vo03xJjBTDrr2gVH
o1F6maW8jWmiLWYdu2Dpp2zTdhJ5h5Jc2qQxrTyM6oTRaM7WaSJNXGoaFp3Pkaxl
ZAyNMHHUc+u9RzyBvv5kRA0y5hjpAqNuIqKqIrayfCffwVtTTVLjmD9pCl6d9CjD
3cpYKslE+nRmOe/YjBqWkrYvryiHNkwsicTOf2HTyBJLV4KboqEymkw2KBtat+Lv
Uw4r97L7N889GLxP9kHB2bMp6/8xhu7HKFL1lEUeOH7i+jHu5S3XH+ON8Yg6blvs
7pBn+OQTI8GQGEdIjopONZ6loqCZcZNkXd7Em7tG/FBpXm88bFtEs9fGxidOJ6ou
oe5sNbDE9tKTkzViwTBVcVNtLLacDZfCk0K3UUMrK0mcogCnzpfOTaa8zRvk1Kta
bgquq55oLD4tWCruUfNEo8Kn0wsGo16Zt4X6QJDOzJVmJ6dra+71FeM81S8sskdY
xLuW1G2tkKMWq3z9XF8gz+aXicMMzaQrDcmCSwX5IsnSORGWD+fOL1c8uqIcFIiu
ZGxHvBZTKujGHcsk57rFXFqszBG24P57rgxuNjdXYJkT88uGlRcntrRqokzBVJit
sGKeKrrhiJKaRREQzTHEtyraAnGIJrR2G9bVtEfT47GIemEi5JXGA4p4gLetebIL
Rvk2MyNHeUdX8Cs8bN2+OSUqtZgrmWXJRoVbap0Xd0GtdY2EqoFY6bjvuGGhVEtE
DRcYETf2bx2bQVq9Ju52RD1Di1QP1n5GUA9N0Aad4Id+GIBBGIIUUDBhCZ6DVXgF
rsBr8DpchTfgTXgbrkEJ3oUP4SP4BG7Bp/AZfA5fwtfwLXwPd+An+BV+g9/hD6lO
apFapQ7JL/VJR6UB6Tg6jc4jFcXQNJpBcyiNFpGDiuh59AJaRS+jV9FV9BZ6D32M
bqEv0HfoB3QbraMf0c/oF/Sn3Cy3y91yrxyQ++UBeVAelsfksByV43JCnsVH8DE8
hE/iMTyBz+IojuMU1nEWW7iAlzDHL+KX8BX8Pv6gWick1Sp3Cf7R8Dd/Ae8S0hM=
--><math xmlns="http://www.w3.org/1998/Math/MathML"><mstyle><mrow><mtable columnspacing="0.167em" columnalign="right center left" displaystyle="true"><mtr><mtd><mi>E</mi><mo maxsize="1">(</mo><mi>&#x3BB;</mi><mo maxsize="1">)</mo><mo>=</mo></mtd><mtd><mrow><msub><mi>E</mi><mstyle mathvariant="bold"><mrow><mi>p</mi><mi>r</mi><mi>o</mi><mi>t</mi><mi>e</mi><mi>i</mi><mi>n</mi><mi>b</mi><mi>o</mi><mi>x</mi></mrow></mstyle></msub></mrow><mo>+</mo><mrow><msub><mi>E</mi><mstyle mathvariant="bold"><mrow><mi>w</mi><mi>a</mi><mi>t</mi><mi>e</mi><mi>r</mi><mi>b</mi><mi>o</mi><mi>x</mi></mrow></mstyle></msub></mrow><mo>+</mo><mrow><msub><mi>E</mi><mstyle mathvariant="bold"><mrow><mi>l</mi><mi>i</mi><mi>g</mi><mi>a</mi><mi>n</mi><mi>d</mi><mi>A</mi></mrow></mstyle></msub></mrow><mo>+</mo><mrow><msub><mi>E</mi><mstyle mathvariant="bold"><mrow><mi>l</mi><mi>i</mi><mi>g</mi><mi>a</mi><mi>n</mi><mi>d</mi><mi>B</mi></mrow></mstyle></msub></mrow><mo>+</mo></mtd></mtr><mtr><mtd><mspace/></mtd><mtd><mo maxsize="1">(</mo><mn>1</mn><mo>-</mo><mi>&#x3BB;</mi><mo maxsize="1">)</mo><mo maxsize="1">(</mo><mrow><msub><mi>E</mi><mstyle mathvariant="bold"><mrow><mi>p</mi><mi>r</mi><mi>o</mi><mi>t</mi><mi>e</mi><mi>i</mi><mi>n</mi><mi>b</mi><mi>o</mi><mi>x</mi><mo>:</mo><mi>A</mi></mrow></mstyle></msub></mrow><mo>+</mo><mrow><msub><mi>E</mi><mstyle mathvariant="bold"><mrow><mi>w</mi><mi>a</mi><mi>t</mi><mi>e</mi><mi>r</mi><mi>b</mi><mi>o</mi><mi>x</mi><mo>:</mo><mi>B</mi></mrow></mstyle></msub></mrow><mo maxsize="1">)</mo><mo>+</mo></mtd></mtr><mtr><mtd><mspace/></mtd><mtd><mo maxsize="1">(</mo><mi>&#x3BB;</mi><mo maxsize="1">)</mo><mo maxsize="1">(</mo><mrow><msub><mi>E</mi><mstyle mathvariant="bold"><mrow><mi>p</mi><mi>r</mi><mi>o</mi><mi>t</mi><mi>e</mi><mi>i</mi><mi>n</mi><mi>b</mi><mi>o</mi><mi>x</mi><mo>:</mo><mi>B</mi></mrow></mstyle></msub></mrow><mo>+</mo><mrow><msub><mi>E</mi><mstyle mathvariant="bold"><mrow><mi>w</mi><mi>a</mi><mi>t</mi><mi>e</mi><mi>r</mi><mi>b</mi><mi>o</mi><mi>x</mi><mo>:</mo><mi>A</mi></mrow></mstyle></msub></mrow><mo maxsize="1">)</mo></mtd></mtr></mtable></mrow></mstyle></math></blockquote>

Because the ligandswap λ reaction coordinate switches from ligand A 
being bound to the protein, and ligand B being bound to the protein, 
this means that the free energy difference between λ=1 and λ=0 is the 
relative binding free energy of the two ligands. Positive values 
indicate a penalty for switching A with B, meaning that ligand A is 
the stronger binder. Negative values indicate a benefit of 
switching A with B, meaning that ligand B is the stronger binder.

Any standard free energy method can be used to evaluate the free 
energy change along this λ coordinate. The `ligandswap` program 
uses [Free Energy Perturbation (FEP)](https://en.wikipedia.org/wiki/Free_energy_perturbation), 
[Bennetts Acceptance Ratio (BAR)](https://en.wikipedia.org/wiki/Bennett_acceptance_ratio) and 
[Thermodynamic Integration (TI)](https://en.wikipedia.org/wiki/Thermodynamic_integration) 
simultaneously. To improve convergence, 
[replica exchange moves](http://dx.doi.org/10.1021/jp0356620)
are applied across λ to allow sampling along this coordinate. In addition, 
to improve convergence 
and smooth the resulting potentials of mean force (PMFs), a 
[soft-core potential](http://dx.doi.org/10.1063/1.3519057) 
is used to soften the interactions between the atoms of the ligands and the 
atoms of the protein and water boxes at λ values between 0 and 1.

Because the free energy is evaluated over a single reaction coordinate, 
it is possible to decompose the energy expression into components. 
For example, we can evalute the contribution to the relative binding 
energy caused by interactions between the ligands and a single residue, e.g.

<body><blockquote><!--latexit:AAAFInjafVN7bBRFGP9m5gqlPej2QXkU6EoPuYJgW6zFWqBXSqFiD2Sv7dFerXN7
c9ele7vn7ix6NjXzDzUmmvhAY0xD6NE/ROQhMcQnMSaamBgjLYkxxsTEaDQxMTEm
/uNr7kFEJc5m8z3me8z8fvPFM6bh8paW6wgTX1k59yIBbmeiATt+jOncjQaOM8c1
bOtogDr6hCGta0uWRhzb5gJdVNRlFU2BTbdvDjZv2XrHth13dd67t/dg+Eg09hBN
HrPszMODAcszzcVK//IVq9eMhLXtpbpDAd2krjssPZMs656tUqprautW1q8SlcIv
VopVYo1YK9aJ9WKDaDy7tmHd+g2N6m0bBRZE+ESZWCKWinKxTFQMcoObbMS1PUdn
EfYoH1eq4lSfTDm2ZyX22qbtRDMOo+m4yQb1vBlJUM4iaTvBonHqMtOw2Fiapiwj
aeiUy6seXtx+p7+ltS0W1kKcO0bc48yNhjVN6lZKrBDLRd24kto3HuOyXzw55TDX
SHhsOhgzZZ8EbVZ3qcFWdZt6ww6q/wnuDE2rzepWNfh/MT0yJo9de8fOubuFImrn
7hFVQ2Gtz7b49S7/rt17ukM90g7TNJNCMx5j8pzJPpOmXFEtapq6g1BYijI0YFtU
txf29e2/L1oEn7kjRcWS6bkD/aXCssKhAkklW6bcP5Ab6Jdw9Bp6HiDqZKXz0AO5
w/3jSs1NKCWKEN3Suaj5I4NDw7JKgRQtQ3Um6R+eMDhTiKjvaQVZ9OhobqR/uBRz
Qxb4eLBNIr86j/xCLGHrXppZvHD60daWDB+bog43dJNNV8Q8l8nikzTFRqWav5w7
NlWgflrdJD0JNWk78re4WvDenDFF066bTcdlZJryCfffe3nnrfZGPZ7cOTZlWBl5
Y0svNkp6psptlWczTE0YjoTUzEqF6o4hz6rqE9ShOpfzVbGoxf16YmgwrB3Z36Og
vhZVfiDqF/ypCSM/JNxIM9HQFHrPt5vM/3FAIjWZzpl5ynrlay4JxdcEpdXU3VNU
ZKTjnnEHJFO1YW3A41QOwt881gCaOS1HJqwdZFmWCJVmHMqhGuqhEYLQBu3QCV0w
DgxMeAQehxl4Bp6Dk/AivAQvwyycgtOQg3m4AJfgMrwBV+BNeBvehavwPnwE1+Ab
+BF+hl/hN1SGalEdakBB1Ip2oHbUgebQK+hV9Bq6gC6hy+gt9AH6GH2GvkBfoq/Q
d+h79BP6Bf2Oy3ElrsENeCPejLfgDtyF9+AINnAGT+MT+An8JH4KP4tP4lk8j8/h
8/gifp3MkKfJ8+QFMktOkTPkHDlPrpB3yFXyIfmEfEo+J1+Tb8kP5E+fr4gTRiXk
jsM/lq/+L9e7p20=
--><math xmlns="http://www.w3.org/1998/Math/MathML"><mstyle><mrow><mtable columnspacing="0.167em" columnalign="right center left" displaystyle="true"><mrow><mrow><msub><mi>E</mi><mstyle mathvariant="bold"><mrow><mi>r</mi><mi>e</mi><mi>s</mi><mi>i</mi><mi>d</mi><mi>u</mi><mi>e</mi></mrow></mstyle></msub></mrow><mo maxsize="1">(</mo><mi>&#x3BB;</mi><mo maxsize="1">)</mo><mo>=</mo><mo maxsize="1">(</mo><mn>1</mn><mo>-</mo><mi>&#x3BB;</mi><mo maxsize="1">)</mo><mo maxsize="1">(</mo><mrow><msub><mi>E</mi><mstyle mathvariant="bold"><mrow><mi>r</mi><mi>e</mi><mi>s</mi><mi>i</mi><mi>d</mi><mi>u</mi><mi>e</mi><mo>:</mo><mi>A</mi></mrow></mstyle></msub></mrow><mo maxsize="1">)</mo><mo>+</mo><mo maxsize="1">(</mo><mi>&#x3BB;</mi><mo maxsize="1">)</mo><mo maxsize="1">(</mo><mrow><msub><mi>E</mi><mstyle mathvariant="bold"><mrow><mi>r</mi><mi>e</mi><mi>s</mi><mi>i</mi><mi>d</mi><mi>u</mi><mi>e</mi><mo>:</mo><mi>B</mi></mrow></mstyle></msub></mrow><mo maxsize="1">)</mo></mrow></mtable></mrow></mstyle></math></blockquote></body>

Thermodynamic integration can be used to average dE(λ)/dλ during the 
ligandswap calculation, thereby returning estimates of the relative 
free energy of binding for the ligands to each residue of the protein. 
These are estimates, and should not themselves be called free energies. 
This is because they are formed using the ensemble of structures 
generated using the total energy expression, and not the decomposed 
expression. However, they will include entropy, and they will give an 
indication of whether an individual residue contributes to the 
relative binding free energy, and if so, to which ligand the residue 
binds most strongly. As such, they are a very useful tool that help 
guide the process of rational drug design. The mathematics 
underlying this decomposition as applied to waterswap is described 
in [more detail here](http://dx.doi.org/10.1039/c3fd00125c).
