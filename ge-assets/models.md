---
sort: 3
---

# Models

## VerticesJSON
VerticesJSON is a simple JSON-based format to declare model's vertices with ease.

### Example of cube
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
08000000 00000000 000000BF 0000003F | first 8 bytes - amount of vertices in the binary file
0000003F 0000803F 000000BF 000000BF | until end 4 bytes with float value (one vertex contains
0000003F 0000803F 0000003F 000000BF | 4 floats, so 16 bytes per vertex)
...
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

