---
sort: 3
---

# Models

## VerticesJSON
VerticesJSON is a simple JSON-based format to declare model's vertices with ease.

### Example of a cube
This is a cube with edge of 1 and centered in point (0; 0):
```json
[
	[-0.5, 0.5, 0.5, 1],
	[-0.5, -0.5, 0.5, 1],
	[0.5, -0.5, 0.5, 1],
	[0.5, 0.5, 0.5, 1],
	[-0.5, 0.5,-0.5, 1],
	[-0.5, -0.5, -0.5, 1],
	[0.5, -0.5, -0.5, 1],
	[0.5, 0.5, -0.5, 1]
]
```

## GEA model binary format

GEA model file contains information about model in this scheme (excluding 0xBB - first byte and SHA512 hash in the end):

```
08000000 00000000 805075D1 5BDC4DB6 | first 8 bytes - amount of vertices in the binary file
BBB1C94E B96B7410 000000BF 0000003F | 16 bytes - UUID of vertex
0000003F 5E226966 A2E44FB7 AFCA74D3 | 4 bytes for each x/y/z coordinate (total - 12 bytes)
5DDA61DE 000000BF 000000BF 0000003F | * next vertex *
...
```

### The same cube as in VerticesJSON example
Binary formatted model (in HEX):
```
08000000 00000000 805075D1 5BDC4DB6
BBB1C94E B96B7410 000000BF 0000003F
0000003F 5E226966 A2E44FB7 AFCA74D3
5DDA61DE 000000BF 000000BF 0000003F
B1CFE579 FDCF47F9 9B334F3B 6589F241
0000003F 000000BF 0000003F C946FE6E
3D1740C0 B8336C6A 87D2E6BC 0000003F
0000003F 0000003F 7B06D4FD 461A4841
B3C7D605 2E157E7F 000000BF 0000003F
000000BF B213A761 007F4D07 B766B213
F81560B3 000000BF 000000BF 000000BF
A8D065B2 C29842CB AC6EECF9 E1646DAD
0000003F 000000BF 000000BF D78B863E
EA9B4450 9ED595F3 205ED598 0000003F
0000003F 000000BF
```

## Creating model out of VerticesJSON

To create a model asset out of VerticesJSON you can use:
```shell
gladiator-tools asset-builder model build --vertices cube.json --output-path cube.gea
```

## Extracting VerticesJSON out of GEA model asset

To extract VerticesJSON out of GEA model asset you can use:
```shell
gladiator-tools asset-builder model to-vertices-json cube.gea --output-path cube_extracted.json
```

