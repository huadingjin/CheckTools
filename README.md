# CheckTools

Mesh and uv check commands for Maya.

## MeshChecker
mesh checker for my own

### checkMesh command
Plugin command to find general topology errors.

#### Check numbers
0. Triangles
1. Ngons
2. Non-manifold edges
3. lamina faces
4. bi-valent faces
5. zero area faces
6. mesh border edges
7. crease edges
8. zero length edges
9. unfronze vertices (vertices with non-zero pnts attribute)

#### Flags
| Longname | Shortname | Argument types | Default | Properties |
|:---------|----------:|:--------------:|:-------:|:----------:|
|check|c|int||C|
|maxFaceaArea|mfa|float|0.00001|C|
|minEdgeLength|mel|float|0.000001|C|

#### Example
```python
from maya import cmds
e = cmds.checkMesh("|pSphere1", c=0)
print e
[u'|pSphere1.f[360]', u'|pSphere1.f[361]', u'|pSphere1.f[362]', u'|pSphere1.f[363]', u'|pSphere1.f[364]', u'|pSphere1.f[365]', u'|pSphere1.f[366]', u'|pSphere1.f[367]', u'|pSphere1.f[368]', u'|pSphere1.f[369]', u'|pSphere1.f[370]', u'|pSphere1.f[371]', u'|pSphere1.f[372]', u'|pSphere1.f[373]', u'|pSphere1.f[374]', u'|pSphere1.f[375]', u'|pSphere1.f[376]', u'|pSphere1.f[377]', u'|pSphere1.f[378]', u'|pSphere1.f[379]', u'|pSphere1.f[380]', u'|pSphere1.f[381]', u'|pSphere1.f[382]', u'|pSphere1.f[383]', u'|pSphere1.f[384]', u'|pSphere1.f[385]', u'|pSphere1.f[386]', u'|pSphere1.f[387]', u'|pSphere1.f[388]', u'|pSphere1.f[389]', u'|pSphere1.f[390]', u'|pSphere1.f[391]', u'|pSphere1.f[392]', u'|pSphere1.f[393]', u'|pSphere1.f[394]', u'|pSphere1.f[395]', u'|pSphere1.f[396]', u'|pSphere1.f[397]', u'|pSphere1.f[398]', u'|pSphere1.f[399]']
```

## UVChecker
### checkUV command
Plugin command to find general uv errors.

#### Check numbers
0. Udim border intersections
1. Non-mapped UV faces
2. Zero-area Uv faces

#### Flags
| Longname | Shortname | Argument types | Default | Properties |
|:---------|----------:|:--------------:|:-------:|:----------:|
|check|c|integer||C|
|uvArea|uva|double|0.000001|C|
|verbose|v|bool|False|C|

#### Example
```python
from maya import cmds
```

### findUvOverlaps command
Plugin command to find overlapped UVs with other shells or itself.

#### Flags
| Longname | Shortname | Argument types | Default | Properties |
|:---------|----------:|:--------------:|:-------:|:----------:|
|uvSet|set|string||C|
|verbose|v|bool|False|C|
|multithread|mt|bool|False|C|
* Multithread flag makes the command faster only when checking multiple UV shells
properties

#### Example
```python
from maya import cmds
r = cmds.findUvOverlaps("|pSphere1")
print r
[u'|pPlane1|pPlaneShape1.map[38]', u'|pPlane1|pPlaneShape1.map[39]', ....]
```

* Single object selected or object path specified as command argment

    <img src="https://www.dropbox.com/s/fkbew67qy4dymza/uvOverlaps_single.gif?dl=1" alt="Drawing" style="width: 300px;"/>

* Multiple object selected

    <img src="https://www.dropbox.com/s/ktomitkqsfs6eb3/uvOverlaps_multiple.gif?dl=1" alt="Drawing" style="width: 300px;"/>
