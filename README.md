# multiRegionReactingFoam
OpenFOAM transient solver for laminar or turbulent fluid flow and solid heat conduction with conjugate heat transfer between solid and fluid regions, plus combustion with chemical reactions (psi thermo model)

Notes

1. Compiles with OpenFOAM 4.0 and OpenFOAM-dev (as of 5-Oct-16)
2. Release includes transient and steady state solvers (multiRegionReactingFoam and multiRegionSimpleReactingFoam)
3. Unsteady state solver benchmarked against DETCHEM, FLUENT and reactingFoam.
4. The main difference with chtMultiRegionReactingFoam is the form of PEqn.H.  PEqn in chtMultiRegionReactingFoam
   is based on PEqn from chtMultiRegionFoam, while PEqn in multiRegionReactingFoam is based on reactingFoam. One may find
   multiRegionReactingFoam to be better than chtMultiRegionReactingFoam for some situations, especially where there
   are large pressure changes during the simulation.
5. LTS is based on a one fluid region (region 0). Therefore, if there are multiple fluid regions, LTS time steps will
   be chosen based on the characteristic times of the fluid assigned to region 0. Therefore, in a multiple fluid region
   application where LTS will be used, one may wish to assign the most "time step sensitive" fluid region to fluid region
   0 (e.g., by placing the name of this more sensitive fluid region first in under "fluid" in constant/regionProperties.
