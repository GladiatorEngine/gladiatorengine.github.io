---
sort: 2
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
