# Kajetan R. Gułaj

Aerospace engineering student at TU Delft.

I build CFD tools meant to be driven by automation, then by AI agents under the supervision of the orchestrating engineer. A production-scale data pipeline and a meshing kernel reached through a plain Python import are the first pieces. The next step is turning the simulation loop itself into an agent-driven design search.

## [pySMESH](https://github.com/KRGulaj/pySMESH)

Python bindings to SALOME SMESH and Open CASCADE, packaged as one self-contained wheel. No SALOME platform, no CORBA, no GUI.

I built it to run unattended inside a CFD workflow. Its core is SMESH's structured meshing: mapped quadrangle faces, block-structured hexahedra, swept prisms and radial O-grids, with exact control of the node spacing on every edge and viscous layers grown from named walls. Body-fitted Cartesian and free algorithms cover the rest, and one model mixes them per sub-shape. Around the mesher sits a stateful CAD modelling session with persistent ids and snapshots. The package exposes 21 meshing algorithms and 31 hypotheses across 216 top-level names, carries OCCT, Boost and VTK privately inside the wheel, and is on PyPI.

## [mesher-baseline](https://github.com/KRGulaj/mesher-baseline)

A measured reference baseline for seven meshing tools: Gmsh, TetGen, Netgen, fTetWild, Mmg, cfMesh and snappyHexMesh. 33 cases at three sizes about a decade apart, regenerated from a seeded catalogue so every input can be rebuilt. Only one of the seven produces a mesh that tracks its input. For the rest the exponent measures the cost of reading a surface, not the cost of meshing a volume. I ran it to find the requirements for a mesh engine of my own.

## [conical-shells-repo](https://github.com/KRGulaj/conical-shells-repo)

Five paper cones from 30 to 150 degrees apex angle, with geometry as the only variable. 30 accepted drops out of 50, filmed against a calibrated wall and counted frame by frame.

Newtonian impact theory gives $C_d = 4\sin^{2}(\alpha/2)$, which vanishes as the apex sharpens. The measurements do not. A weighted fit returns $C_d = 0.6956\sin^{2}(\alpha/2) + 0.4796$ at $R^{2} \approx 0.99$, and the intercept is the base pressure and skin friction contribution the impact model has no term for. The fit is weighted because the propagated uncertainties are heteroscedastic, at 17.7 to 25.4 per cent on $C_d$.

## Not public

**PinnFlux.** A 29,094-case CFD dataset built to train a graph neural network that predicts mesh sizing fields. 26,943 cheap Euler cases and 2,151 RANS cases with k-ω SST for viscous ground truth. The Euler tier is split exactly 50/50 between airfoils and randomised bluff bodies, so neither attached nor separated flow is the default case. 18,400 vCPU-hours on a 64 vCPU instance.

**Flux Engineering.** A desktop application covering the full CFD workflow. mfoil, XLB and SU2 behind one interface span viscous-inviscid analysis, lattice Boltzmann, and finite-volume CFD from Euler through LES. The goal is to turn the simulation loop into an agent-driven design search, sampling broadly at low fidelity and raising fidelity as the design space narrows. Selected for the Aerospace Innovation Hub accelerator at TU Delft.

**Ramificatio.** An out-of-core mesh engine in Rust, with a Python API through PyO3. Disk holds the source of truth and RAM only the chunks an operation touches, so mesh size stops being bounded by memory. Target is generating and editing a $10^{9}$ cell mesh on a workstation laptop.

## Earlier work

[openai-parameter-golf-2026](https://github.com/KRGulaj/openai-parameter-golf-2026), a full development cycle on 16 MB-constrained language modelling.

[personal-vector-db](https://github.com/KRGulaj/personal-vector-db), a document processing pipeline into a Qdrant vector database.

## Contact

[LinkedIn](https://www.linkedin.com/in/kajetan-r-gulaj/) · kajetan.gulaj@gmail.com
