# OpenFOAM
- keep copy of _0_ folder as _0.orig_  
- `touch (filename).OpenFOAM` - generate file for __ParaView__  
- `foamToVTK` - generate VTK folder for __VisIt__

## interFoam / interMixingFoam
### Steps
- `blockMesh` - generate mesh
- `setFields` + `setExprFields` - intialize _alpha.*_
- (if parallel) `decomposePar` - split over processors
- (if parallel) `mpirun -np (processors) interFoam -parallel` / `interFoam` - run simulation
- (if AMR) `reconstructParMesh` - combine mesh regions
- `reconstructPar` - combine fields
### Workflow
- setup case for a _interMixingFoam_ simulation (F1 immiscible and F2,F3 miscible)
- set _alpha.F3_ as one of the fluids and either _alpha.F1_ or _alpha.F2_ as "blank"
- in _dynamicMeshDict_ - `field alpha.F3`
- to toggle miscibility
  - rename _alpha.F1_ and _alpha.F2_
  - update _setFieldDict_ and _setExprFieldDict_

## Adaptive Mesh Refinement
- precision error - check `writePrecision` in _controlDict_
- for 2D - needs `symmetryPlane`
