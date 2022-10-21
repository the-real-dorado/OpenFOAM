# OpenFOAM
- keep copy of _0_ folder as _init_  
- `touch (filename).OpenFOAM` - generate file for __ParaView__  
- `foamToVTK` - generate VTK folder for __VisIt__
## interFoam
(working off standard file directory structure)  
- `blockMesh` - generate mesh - _blockMeshDict_
- `setFields` / `setExprFields` - intialize _alpha.water_ - _setFields_ / _setExprFields_
- `decomposePar` - split regions over processors - _decomposeParDict_
- `mpirun -np (processors) interFoam -parallel` / `interFoam` - run simulation
- `reconstructPar` - combine regions
