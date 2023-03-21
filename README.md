# zfxy-spec: ZFXY specifications

# Definition
Three-dimentional spatial identifier candidate ZFXY of a point with longitude _lng_ [decimal degrees], latitude _lat_ [decimal degrees] (_lat_rad_ in radians), and elevation _h_ [m] shall be encoded `{z}/{f}/{x}/{y}` when a zoom level _z_ is given as an integer and _f_, _x_, _y_ are given in the following formulae: 
- `f = floor(n * h / H)`
- `x = floor(n * ((lng + 180) / 360))`
- `y = floor(n * (1 - log(tan(lat_rad) + (1 / cos(lat_rad))) / PI) / 2)`
where `n = 2 ^ z`, `Z = 25` and `H = 2 ^ Z [m]`.

Definitions of _z_, _x_, _y_ are the same as ones in the industry standard [Slippy Map Tilenames](https://wiki.openstreetmap.org/wiki/Slippy_map_tilenames).

# Characteristics
- Height of a voxel represented by a ZFXY with z=Z is 1 [m].

# Implementation considerations
- `log(tan( lat ) + (1 /cos( lat )))` can be more effectively calculated as `log(tan( lat / 2 + 45 ))`.
- `(lng + 180) / 360` can be more effectively calculated as `lng / 360 + 0.5`.
- We appreciate Mr. KAWASE Kazushige from Geospatial Informataion Authority of Japan for the proposals above. 

# Future considerations
- More compact encodings of ZFXY may be considered in future. 
- The value of `Z` is still subject to change.
