.. include:: additional/links.rst

NMRD from MD
============

Dipolar Nuclear Magnetic Resonance from Molecular Dynamics
(NMRDfromMD) is a Python toolkit designed for the
computation of dipolar NMR relaxation times (the so-called :math:`T_1` and
:math:`T_2`) from molecular dynamics simulations. Used in combination
with |MDAnalysis|, NMRforMD allows for the analysis of
trajectory files from any MDAnalysis-compatible simulation package, including
|LAMMPS| and |GROMACS|.

This package builds on the now discontinued |NMRforMD|.

.. image:: ../../avatars/avatars.png
    :class: only-dark
    :alt: molecular dynamics systems used in these examples 

.. image:: ../../avatars/avatars.png
    :class: only-light
    :alt: molecular dynamics systems used in these examples

.. container:: figurelegend

   Figure: Examples of systems that can be analyzed using NMRDfromMD, from
   left to right: a bulk water system, a Lennard-Jones fluid, and a lysozyme
   protein in contact with a thin layer of water molecules.

Datasets
--------

Two molecular dynamics datasets are available on GitHub: a |polymer in water|
system generated using LAMMPS, and a |water confined in silica| system
generated using GROMACS. These datasets can be downloaded to follow the
tutorials or simply to test NMRDfromMD.

.. toctree::
   :maxdepth: 2
   :caption: Theory
   :hidden:

   theory/context
   theory/theory

.. toctree::
   :maxdepth: 2
   :caption: Tutorials
   :hidden:
   
   tutorials/installation
   tutorials/isotropic-system
   tutorials/anisotropic-system

.. toctree::
   :maxdepth: 2
   :caption: Illustrations
   :hidden:

   illustrations/lennard-jones-fluids
   illustrations/bulk-water
   illustrations/lysozyme-in-water

.. toctree::
   :maxdepth: 2
   :caption: Best practices
   :hidden:

   best-practices/best-practices

.. toctree::
   :maxdepth: 2
   :caption: Additional
   :hidden:

   additional/bibliography
   additional/acknowledgments
