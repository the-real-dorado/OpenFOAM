# OpenFOAM
- (in base directory) `touch (filename).OpenFOAM` - generate file for ParaView  
- keep copy of _0_ folder as _init_
## interFoam
(working off standard file directorys structure)  
- `blockMesh` - generate mesh - _blockMeshDict_
- `setFields` / `setExprFields` - intialize _alpha.water_ - _setFields_ / _setExprFields_
- `decomposePar` - split regions over processors - _decomposeParDict_
- `mpirun -np (processors) interFoam -parallel` / `interFoam` - run simulation
- `reconstructPar` - combine regions
