# zfxy-spec: ZFXY specifications

# Definition
Three-dimentional spatial identifier candidate ZFXY of a point with longitude _lng_ [decimal degrees], latitude _lat_ [decimal degrees], and elevation from sea level _h_ [m] shall be encoded `{z}/{f}/{x}/{y}` when a zoom level _z_ is given as an integer and _f_, _x_, _y_ are given in the following formulae: 
- `f = floor(n * h / H) + (2 ^ (z - 1))`
- `x = floor(n * ((lng + 180) / 360))`
- `y = floor(n * (1 - log(tan(lat) + (1 / cos(lat))) / PI) / 2)`
where `n = 2 ^ z` and `H = 2 ^ 25 [m]`.

Definitions of _z_, _x_, _y_ are the same as ones in the industrial standard [Slippy Map Tilenames](https://wiki.openstreetmap.org/wiki/Slippy_map_tilenames).

# Characteristics
- Height of a voxel represented by a ZFXY with z=25 is 1 [m].
- At z=25, the lower bound of the voxel represented by f=0 is `-2 ^ 24` meters under sea level, and that of f=`2 ^ 25` is `2 ^ 24` meters above sea level.

# Future considerations
- More compact encodings of ZFXY may be considered in future. 
