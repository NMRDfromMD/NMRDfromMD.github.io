Best practice
=============

Choosing the right force field
------------------------------

.. container:: justify

    The agreement between experiments and simulations can only be as good as the
    force field used in the simulations. Although it has been shown that some
    force fields lead to excellent agreement with experimental data, as for instance
    for water, hydrocarbons, or polymer melts
    :cite:`singerMolecularDynamicsSimulations2017,gravelleNMRInvestigationWater2023,gravelleAssessingValidityNMR2023`,
    it is important to keep in mind that force fields are often parametrized
    to reproduce thermodynamic quantities, such as solvation energy.
    However, NMR relaxation times depend on both structural
    and dynamical quantities, and large differences between experiments
    and simulations are expected for poorly accurate force fields.

.. container:: justify

    As an illustration, the NMR relaxation time :math:`T_1`
    of bulk water was measured as a function of the temperature
    for three different water models:
    :math:`\text{TIP4P}-\epsilon` :cite:`fuentes-azcatlNonPolarizableForceField2014`,
    :math:`\text{SPC/E}` :cite:`berendsenMissingTermEffective1987`,
    and :math:`\text{TIP3P}` :cite:`jorgensenComparisonSimplePotential1983`.
    Our results show that the :math:`\text{TIP4P}-\epsilon` water models
    is in excellent agreement with experimental measurements from 
    Krynicki et al. :cite:`krynickiProtonSpinlatticeRelaxation1966`
    and Hindman et al. :cite:`hindmanRelaxationProcessesWater2003`.
    By contrast, :math:`\text{SPC/E}` and :math:`\text{TIP3P}`
    both overestimate the NMR relaxation time :math:`T_1`, in 
    excellent agreement with previous results
    by Calero et al. :cite:`calero1HNuclearSpin2015`. Note that Calero et al.
    used :math:`\text{TIP4P}-2005` water model instead of the :math:`\text{TIP4P}-\epsilon` model used here,
    however these two models show very similar structures and viscosities for liquid water :cite:`fuentes-azcatlNonPolarizableForceField2014`,
    and are thus expected to yield similar relaxation times.

.. image:: ../figures/illustrations/bulk-water/experimental_comparison-dark.png
    :class: only-dark
    :alt: NMR results obtained from the LAMMPS simulation of water

.. image:: ../figures/illustrations/bulk-water/experimental_comparison-light.png
    :class: only-light
    :alt: NMR results obtained from the LAMMPS simulation of water

.. container:: figurelegend

    Figure: NMR relaxation time :math:`T_1` between MD simulations of bulk 
    water obtained with three different water models:
    :math:`\text{TIP4P}-\epsilon` :cite:`fuentes-azcatlNonPolarizableForceField2014`,
    :math:`\text{SPC/E}` :cite:`berendsenMissingTermEffective1987`,
    and :math:`\text{TIP3P}` :cite:`jorgensenComparisonSimplePotential1983`.
    Results are compared with experiments 
    from Krynicki et al. :cite:`krynickiProtonSpinlatticeRelaxation1966`
    and from Hindman et al. :cite:`hindmanRelaxationProcessesWater2003`.

Simulation accuracy
-------------------

.. container:: justify

    NMR relaxation measurements are sensitive both thermodynamic and dynamic quantities, 
    and it is therefore important to ensure the accuracy of the molecular simulation.
    Several parameters are known to affect the accuracy of the simulations,
    such as the force field (as discussed previously), the time step, the cut-offs,
    or the sampling time
    :cite:`frenkelUnderstandingMolecularSimulation2002,allenComputerSimulationLiquids2017`.

.. container:: justify

    As an illustration, the NMR relaxation time :math:`T_1`
    of bulk water was measured as a function of the LJ cut-off.
    Our results show that, for the smallest cut-off,
    the inter-molecular :math:`T_1^\text{inter}` is slightly
    under-estimated, which is mainly due to an over-estimation
    of the inter-molecular characteristic time :math:`\tau_\text{inter}`.
    Our results also indicate that for a cut-off of 1\,nm,
    which is commonly used value, a small error of 
    about 1\,\% is induced. These observations are consistent
    with previous measurements :cite:`gravelleNMRInvestigationWater2023`,
    and confirm that care must be taken if one attempt in reproducing
    accurately NMR quantities.

.. image:: ../figures/illustrations/bulk-water/effect_cutoff-dark.png
    :class: only-dark
    :alt: NMR results obtained from the LAMMPS simulation of water

.. image:: ../figures/illustrations/bulk-water/effect_cutoff-light.png
    :class: only-light
    :alt: NMR results obtained from the LAMMPS simulation of water

.. container:: figurelegend

    Figure: a) Inter-molecular NMR relaxation time :math:`T_1^\text{inter}`
    as a function of the LJ cut-off for a bulk water system.
    b) Inter-molecular characteristic time :math:`\tau_\text{inter}`
    as a function of LJ cut-off.

Box size
--------

.. container:: justify

    NMR relaxation measurements are sensitive to the 
    finite-size effects that can occur with small simulation boxes :cite:`grivetNMRRelaxationParameters2005`.

.. container:: justify

    As an illustration, the NMR relaxation rate :math:`R_1`
    was measured for water with different number of molecules
    :math:`N \in [100,\,10000]`, which correspond to equilibrium
    box of lateral sizes :math:`L \in [1.4,\,6.7]\,\text{nm}`.
    Our results show that the inter-molecular
    relaxation rate :math:`R_1^\text{inter}` is sensitive to the 
    box size even for the largest boxes considered here.
    With small box size, the tail of :math:`G_\text{inter}`, 
    which decreases as :math:`G_\text{inter} \sim t^{-3/2}`, is cutoff
    which lead to an error on :math:`R_1^\text{inter}`.
    Note that :math:`R_1^\text{intra}`, which is the dominant contribution to 
    :math:`R_1` for water at ambient temperature, is barely affected
    by the box size and therefore the resulting error induced on the 
    total relaxation rate :math:`R_1` remains small for :math:`N > 1000`.

.. image:: ../figures/illustrations/bulk-water/effect_L_on_R1-dark.png
    :class: only-dark
    :alt: NMR results obtained from the LAMMPS simulation of water

.. image:: ../figures/illustrations/bulk-water/effect_L_on_R1-light.png
    :class: only-light
    :alt: NMR results obtained from the LAMMPS simulation of water

.. container:: figurelegend

    Figure: a) Inter-molecular NMR relaxation rate :math:`R_1^\text{inter}` as a function of the number of molecules :math:`N`
    for a bulk water system. For the smallest systems, results were averaged
    from up to 10 independent simulations and the error bar is calculated from
    the standard deviation. b) Inter-molecular correlation function :math:`G_\text{inter}`
    for two different numbers of molecules.

Dumping frequency
-----------------

.. container:: justify

    The dumping frequency sets the temporal resolution of the analysis.
    The maximum dumping period that can be used is system-dependent
    and must typically be much smaller than the correlation times.
    If the typical correlation times in the system is not known,
    the appropriate dumping frequency :math:`\Delta t` can
    be identified from convergence testing.
    Note however than using a high dumping frequency
    increases the size of the trajectory files, which in turn
    can make the computation of NMR relaxation rates
    computationally expensive.

.. container:: justify

    As an illustration, the NMR relaxation time :math:`T_1` was measured
    for an increasing dumping period from :math:`\Delta t = 0.02\,\text{ps}`
    to :math:`5\,\text{ps}`. Our results show that using a dumping period
    larger than about :math:`\Delta t = 0.5\,\text{ps}` leads to a significant decrease
    of the measured relaxation time :math:`T_1`. The decrease in :math:`T_1`
    is accompanied by an increase of the measured inter-molecular
    relaxation times :math:`\tau_\text{inter}`. 

.. image:: ../figures/illustrations/bulk-water/effect_dumping_frequency-dark.png
    :class: only-dark
    :alt: NMR results obtained from the LAMMPS simulation of water

.. image:: ../figures/illustrations/bulk-water/effect_dumping_frequency-light.png
    :class: only-light
    :alt: NMR results obtained from the LAMMPS simulation of water

.. container:: figurelegend

    Figure: a) Convergence testing showing the NMR relaxation time :math:`T_1`
    as a function of the trajectory dumping frequency :math:`\Delta t`
    for a bulk water system at :math:`T = 300 \text{K}`.
    The dashed line show the value for :math:`T_1`
    for :math:`\Delta t \to 0`.
    b) Inter-molecular relaxation times :math:`\tau_\text{inter}` as 
    a function of :math:`\Delta t`.