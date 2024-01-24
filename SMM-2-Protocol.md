SMM 2 uses [ENL](ENL-Protocol). After a client has joined the mesh, it sends the following packet to the master station through the [reliable protocol](Reliable-Protocol).

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 4 | Packet type (1) |
| 0x4 | 4 | Padding |
| 0x8 | 8 | NSA ID |
| 0x10 | 8 | Unknown |
| 0x18 | 8 | Unknown |
| 0x20 | 11 x 2 | Name |
| 0x36 | 2 | Padding |
| 0x38 | 88 | [Mii](Mii-Data-(Switch)) |