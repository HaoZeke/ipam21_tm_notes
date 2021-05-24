# Matrix product states for real materials

- By [Ulrich Schollwöck](https://homepages.physik.uni-muenchen.de/~Schollwoeck/)
- University of Munich
- [Video here](http://www.ipam.ucla.edu/abstract/?tid=16578&pcode=TMWS1)

> In this talk, I will present recent advances on how to combine MPS-based and similar algorithms to provide impurity solvers for dynamical mean-field theory (DMFT) in combination with density functional theory. Several physical applications, in particular to strongly correlated materials with Hund’s coupling and spin-orbit coupling (transition metal and rare earth oxides) will be presented, showing how this method can solve physical questions that are not easily accessible to competing methods.

## Notes

```{note}
Images cannot be embeded as only a video was provided. Timestamps are indicated.
```

The main problem with the Hamiltonian is the electron electron interactions. Where the system cannot be framed in terms of a delocalized interaction (e.g. where the valence electrons are bound to sites) then the many body problem needs to be solved. This is the realm of strongly correlated systems where model Hamiltonians are used to study such interactions.

```{admonition} Click to expand slide scribble
:class: dropdown
![Slide1](d4s1/wks1_d4s1_p1.*)
```

Strong correlations matter, and their study in every dimension is important:
- **0 dimensional** systems related to magnetic systems, impurity physics, and quantum dots
- **1 dimensional** systems model spin chains and ladders, along with the Luttinger liquid
- **2 dimensional** systems are relevant for modeling frustrated magnets and high-T_C superconductors
- **3 dimensional** models have the capacity to study realistic systems, and can describe transition metals and rare earth compounds
  - Focus area for talk

Dynamical mean field theory is the main bridging method.

```{info}
Main results are derived in {cite}`lindenImaginarytimeMatrixProduct2020` with applications described in {cite}`wolfImaginaryTimeMatrixProduct2015,brambergerBaOsOHundMetal2021,karpMathrmSrMathrmMoOMathrmSr2020`.
```

Essentially, the system is simplified in multiple stages.

```{admonition} Click to expand slide scribble
:class: dropdown
![Slide2](d4s1/wks1_d4s1_p2.*)
```

- Some transitions have no order parameter, atleast, not a symmetry breaking simple order parameter.

```{admonition} Click to expand slide scribble
:class: dropdown
![Slide3](d4s1/wks1_d4s1_p3.*)
```

For the Mott Hubbard transition there is no symmetry breaking, and the transition is due to energetic blocking

### DMFT

The dynamical mean field theory aims to recreate the temporal dependence by certain key aspects:
- interacting model $\to$ interacting impurity in a non-interacting effictive bath
- impurity **dynamically** exchanges electrons with bath
- **dynamical self-consistency** implies that the local lattice GF/SE is the same as the impurity GF/SE

This is exact in the limit of infinite coordination number or dimension. 

It can be made more realistic by virtue of:
- Having more bands
- Using cluster methods
- Combinations with DFT

The method is originally described in {cite}`georgesHubbardModelInfinite1992` with more details in {cite}`kotliarElectronicStructureCalculations2006,georgesDynamicalMeanfieldTheory1996`.

Green's function is required. This is done with an impurity solver like:
- Hirsch-Fye MC (Action) [Obsolete]
- continuous time QMC (Action)
  - analytic continuation
  - sign problem?
- exact diagnolization (Hamiltonian)
  - analytic continuation
  - computational cost (exponential)
- numerical renormalization group (Hamiltonian)
  - logarithmic discretization
  - computational cost (exponential)

### MPS Formulation
- Good for 1D
- No sign issues (unlike CT-QMC)
- Real frequency axis
- No logarihmic discretization of the spectral range
- Computational tractable
- Works best at zero temperature (unlike CT-QMC)

On the imaginary axis:
- smaller bath sizes
- no entanglement growth in time evolution
- more orbitals
- however, needs analytic continuation of spectral function
- worked upto 6 orbitals (in {cite}`wolfImaginaryTimeMatrixProduct2015`)

### Case study

Properties of strontium ruthenate are described in {cite}`mackenzieSuperconductivityMathrmSrMathrmRuO2003`. Overview:
- 2D, 3 relevant d-orbitals
- Strongly correlated
- Fermi liquid (Hund's metal)
- Unocnventional superconductor (p-wave)
- Appreciable spin-orbit coupling (SOC)

Good system for integrating MPS-DMFT with DFT band structure, since without SOC CTQMC-DMFT is very accurate and can be used for benchmarks, with SOC there is a sign problem.

```{admonition} Click to expand slide scribble
:class: dropdown
![Page4](d4s1/wks1_d4s1_p4.*)
```

Key questions were:
- does SOC affect the Fermi liquid behaviour
- interplay of Coulomb interaction and SOC
- calculation of new topology
- CTQMC has a sign problem at low temp.

Existing literature {cite}`tamaiHighResolutionPhotoemissionMathrmSr2019,zhangFermiSurfaceMathrmSr2016,kimSpinOrbitCouplingElectronic2018` suggested that Fermi liquid was a little affected with a strong SOC enhancement via a fitting process.

Effective steps for imaginary time DMFT-MPS [time=18m10s]:
- From Green's function and self energy
- Derive an effective Hamiltonian where the impurity is
- Time evolution and then feed into the SCF loop

The tensor related steps are the calculation of the ground state, excitation, and then time evolution. Without spin orbit coupling there are no interactions and the calculation is fairly straightforward.

```{admonition} Click to expand slide scribble
:class: dropdown
![Page5](d4s1/wks1_d4s1_p5.*)
```

### Issues

However, the mapping of a bath to a 1D MPS is non-trivial and was disputed {cite}`wolfSolvingNonequilibriumDynamical2014`.

```{admonition} Click to expand slide scribble
:class: dropdown
![Page6](d4s1/wks1_d4s1_p6.*)
```

The star geometry is an order of magnitude more efficient.
The star geometry has a growing potential, and the sites have a full/empty product state, and the impurity hopping causes some entanglement but is offset by the fact that the hoppings are energetically unfavorable. With the chain model, the potentials are constant, hopping is therefore cheap (intrabath) and effectively there is much more entanglement.

### Time Scaling

In order to capture the behavior of the anticommutator, a higher resolution is needed for lower times.

```{admonition} Click to expand slide scribble
:class: dropdown
![Page7](d4s1/wks1_d4s1_p7.*)
![Page8](d4s1/wks1_d4s1_p8.*)
```

[time=23:16 for benchmarks]

Linear predictions for the time work as well, empirically {cite}`barthelSpectralFunctionsOnedimensional2009`.

[time=24:00 for benchmarks]

### Spin Orbit coupling

The bath fitting becomes much more difficult, due to interactions. From two self energies to 21 self energies. However, the diagonal self-energies are essentially unchanged, that is when the impurity jumps in and out of the bath, does not change the Fermi liquid behavior, as expected.

The off diagonals show agreement with ARPES, angular resolved photo electron spectroscopy signals. This now allows for a fit free comparison for real systems.

[time=25:00 for benchmarks]

### Conclusions
- MPS for realistic non-1D problems
- Advanced complementary time evolution
- Krylov+2TDVP (time stepper combinations)
- MPS-DMFT allows a first principles treatment of SOC, reproduces CTQMC, is cheaper
