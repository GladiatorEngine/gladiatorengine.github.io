---
sort: 1
---

# Asset Binary format

All assets are stored in GladiatorEngine Asset Binary format. It's a pretty simple format to understand.

## AssetType
GEA uses the first byte in file to determine what does the the file contain:

| Byte | Description |
| ---- | ----------- |
| 0xAA | Texture     |
| 0xBB | Model       |
| 0xCC | Animation   |
| 0xDD | Intelligence (NPC/player's movements, dialogs and so on) |
| 0xEE | AssetPack   |

## Single asset files

If GEA file contains one asset (texture, model, sound and etc.) it follows the following scheme:
```
AA89504E 470D0A1A 0A000000 0D494844 | AA - first byte (in this case: texture), next - asset data
...
18F995DC CEB24D1A 34A1DF46 A30C20C3 |
FDA86E55 0B999665 F3A8407F 6AB9AB9C | SHA512 hash of asset data
EFE5D488 EA8C4EA8 31CACB45 DABCF06A | (last 64 bytes)
87A7F0A6 09A85546 8A07428E EA41255E |
```

## Multiple asset files (AssetPacks)

If GEA file contains multiple assets in it's first byte should be 0xEE (AssetPack) and should not have SHA512 hash of asset data.
So, it's scheme looks like this:
```
EE561103 00000000 00AA8950 4E470D0A | first byte - 0xEE (AssetPack),
                                    | 8 bytes of contained asset's length (dec: 201046),
                                    | 1 byte - contained asset's type (0xAA - texture)
                                    | *length* (in this case 201046) bytes of asset data
... (continue at byte 201056 - asset data just ended)
56110300 00000000 AA89504E 470D0A1A | there is another asset, same as before
                                    | 8 bytes of contained asset's length (dec: 201046),
                                    | 1 byte - contained asset's type (0xAA - texture)
                                    | *length* (in this case 201046) bytes of asset data
... (and so on until EOF)
```
