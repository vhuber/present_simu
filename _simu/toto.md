---
title: "noTitle"
date: 2015_8_21-153359_noTitle.md
categories: simu
--- 

#Physique
## Model 
 - Name **precAFP3D**
 - shortName **precAFP3D**
 - description ****
 - model **linear**

### Parameteros

|Name|Value|Min|Max|
|---|---|---|---|
|**mu_0**|1|1|1|

### Materials
|Material Physical Region Name|Rho|mu|Cp|Cv|k11|k12|k13|k22|k23|k33|Tref|beta|C|YoungModulus|nu|Sigma|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|firstMat|firstMat|1|1|1|1|0|0|1|0|0|1|0|1|1|1|1|

### Boundary Conditions
|Name|Type|Expressions|
|---|---|---|
|**phi**|Dirichlet|<ul><li>**Border**</li><li>0</li><li>0</li><li></li></ul>|
|**u**|Dirichlet|<ul><li>**Border**</li><li>{0,0,0}:x:y:z</li><li>{0,0,0}:x:y:z</li><li></li></ul>|

### PostProcess
|Kind | data |
|---|---|
##Physique spÃÂÃÂ©cifique
| Variable | value | 
|---|---|
| mu | 1.:x:y| 
| Rhs | {-2*(z*z+y*y-2) -2*x*(1-y*y)*(1-z*z),-2*(x*x+z*z-2)-2*y*(1-x*x)*(1-z*z),-2*(y*y+x*x-2)-2*z*(1-x*x)*(1-y*y)}:x:y:z|
| Exact | {(1-y*y)*(1-z*z),(1-x*x)*(1-z*z),(1-x*x)*(1-y*y)}:x:y:z|
#Numerics
##Mesh
| Shape              |1024|
|---|---|
| DIM              |3|
| Order              |1|
| hMin              |0.141421|
| hMax              |0.173205|
| hAverage              |0.224535|
| nPoints              |2347|
| nEdges              |13290|
| nFaces              |21024|
| nVertices              |2347|

##Spaces
|qDim|4|1|1|
|---|---|---|---|
|BasisName|nedelec_lagrange|nedelec|lagrange|
|nDof|68921|59660|9261|
|nLocaldof|12191|10459|1732|
|nPerComponent|17230|19886|9261|
##Solvers
| x | ms | blocksms.11 | blockms.22 |
|---|---|---|---| 
|**ksp-type** |  minres| cg| cg|
|**pc-type**  |  blockms| ams| boomeramg|
|**on-type**  |  elimination| elimination_symmetric| elimination_symmetric|
|**Matrix**  |  323681| 10459| 1732|
|**nb Iter**  |  5| <ul><li>12 -- 4.01514e-08 -- 1</li><li>10 -- 1.51398e-08 -- 1</li><li>12 -- 7.28764e-09 -- 1</li><li>12 -- 5.58366e-09 -- 1</li><li>12 -- 3.06027e-09 -- 1</li><li>12 -- 1.87121e-09 -- 1</li></ul>| <ul><li>0 -- 0 -- 1</li><li>2 -- 2.04155e-08 -- 1</li><li>2 -- 2.12826e-08 -- 1</li><li>2 -- 2.83567e-08 -- 1</li><li>2 -- 7.06841e-09 -- 1</li><li>3 -- 2.95333e-10 -- 1</li></ul>|
##Timers
|Timer                                                  |Count   |Total(s)     |Max(s)     |Min(s)    |Mean(s) |StdDev(s)|
|---|---|---|---|---|---|---|
|                                                     Backend::newMatrix:: build stencil |       5 |    4.24e-01 |    2.89e-01 |    2.51e-06 |    8.47e-02 |    1.08e-01|
|                                                     Backend::newMatrix:: initialize matrix |       5 |    5.19e-02 |    3.41e-02 |    1.19e-03 |    1.04e-02 |    1.25e-02|
|                                                     Backend::newMatrix:: zero out matrix + set split |       5 |    1.55e-03 |    9.95e-04 |    4.84e-05 |    3.10e-04 |    3.65e-04|
|                                                     Inverse |       1 |    2.07e+00 |    2.07e+00 |    2.07e+00 |    2.07e+00 |    0.00e+00|
|                                                     Mesh::UpdateForUse Compute adjacency graph |       1 |    5.32e-02 |    5.32e-02 |    5.32e-02 |    5.32e-02 |    0.00e+00|
|                                                     Mesh::updateForUse check |       5 |    1.18e-05 |    5.96e-06 |    1.02e-06 |    2.35e-06 |    1.92e-06|
|                                                     Mesh::updateForUse update entities of codimension 1 |       1 |    2.91e-01 |    2.91e-01 |    2.91e-01 |    2.91e-01 |    0.00e+00|
|                                                     Mesh::updateForUse update geomap |       1 |    2.84e-03 |    2.84e-03 |    2.84e-03 |    2.84e-03 |    0.00e+00|
|                                                     Mesh::updateForUse update on boundary |       1 |    1.24e-02 |    1.24e-02 |    1.24e-02 |    1.24e-02 |    0.00e+00|
|                                                     OperatorMatrix::applyInverse blockms.11 |       6 |    1.80e+00 |    4.79e-01 |    2.29e-01 |    3.01e-01 |    8.15e-02|
|                                                     OperatorMatrix::applyInverse blockms.22 |       6 |    2.19e-01 |    7.99e-02 |    2.60e-02 |    3.66e-02 |    1.95e-02|
|                                                     PartitionIO writing elements |       1 |    1.02e-02 |    1.02e-02 |    1.02e-02 |    1.02e-02 |    0.00e+00|
|                                                     PartitionIO writing faces |       1 |    9.03e-03 |    9.03e-03 |    9.03e-03 |    9.03e-03 |    0.00e+00|
|                                                     PartitionIO writing hdf5 file |       1 |    4.99e-02 |    4.99e-02 |    4.99e-02 |    4.99e-02 |    0.00e+00|
|                                                     PartitionIO writing points |       1 |    1.92e-03 |    1.92e-03 |    1.92e-03 |    1.92e-03 |    0.00e+00|
|                                                     PartitionIO writing stats |       1 |    9.45e-04 |    9.45e-04 |    9.45e-04 |    9.45e-04 |    0.00e+00|
|                                                     [PreconditionerBlockMS] applyInverse update solution |       6 |    2.04e+00 |    5.63e-01 |    2.62e-01 |    3.40e-01 |    1.01e-01|
|                                                     [PreconditionerBlockMS] setup done  |       1 |    7.42e-01 |    7.42e-01 |    7.42e-01 |    7.42e-01 |    0.00e+00|
|                                                     [PreconditionerBlockMS] update |       1 |    2.71e+00 |    2.71e+00 |    2.71e+00 |    2.71e+00 |    0.00e+00|
|                                                     read msh from file |       1 |    2.65e-01 |    2.65e-01 |    2.65e-01 |    2.65e-01 |    0.00e+00|
