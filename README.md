# OpenFOAM
- keep copy of _0_ folder as _0.orig_  
- `touch (filename).OpenFOAM` - generate file for __ParaView__  
- `foamToVTK` - generate VTK folder for __VisIt__

## interFoam / interMixingFoam
(working off standard file directory structure)  
- `blockMesh` - generate mesh - _blockMeshDict_
- `setFields` / `setExprFields` - intialize _alpha.*_ - _setFields_ / _setExprFields_
- (if parallel) `decomposePar` - split regions over processors - _decomposeParDict_
- (if parallel) `mpirun -np (processors) interFoam -parallel` / `interFoam` - run simulation
- (if AMR) `reconstructParMesh` - combine mesh regions
- `reconstructPar` - combine fields

### Workflow
- setup case for a `interMixingFoam` simulation (F1 immiscible and F2,F3 miscible)
- set `alpha.F3` as one of the fluids and either `alpha.F1` or `alpha.F2` as "blank"
- in `dynamicMeshDict` - set field to `alpha.F3`
- to toggle miscibility
  - rename `alpha.F1` and `alpha.F2`
  - update `setField` and `setExprField`

## Adaptive Mesh Refinement
- precision error - check `writePrecision` in `controlDict`
- for 2D - needs `symmetryPlane`
