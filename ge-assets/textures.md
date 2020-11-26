---
sort: 1
---

# Textures

## Creating texture out of PNG

To create a texture asset out of PNG you can use GladiatorEngine Toolset's AssetBuilder:
```shell
gladiator-tools asset-builder texture build --png texture01.png --output-path texture01.gea
```

## Extracting PNG from GEA texture asset

To extract PNG texture out of GEA texture asset you can use:
```shell
gladiator-tools asset-builder texture to-png texture01.gea --output-path texture01_extracted.png
```

