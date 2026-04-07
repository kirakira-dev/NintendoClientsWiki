[Pia](Pia-Overview) > [Protocols](Pia-Protocols) > Session Protocol (new)
---

This page describes the session protocol that can be found in Pia version 6.x. It combines the functions of the [[station protocol]] and [[mesh protocol]] into one.

*Up to 6.23:*
| Type | Description |
| --- | --- |
| 0 | [Join request](#join-request) |
| 1 | Join request ack |
| 2 | Join response |
| 3 | Leave request |
| 4 | ? |
| 5 | [Update session](#update-session) |
| 6 | Update session ack |
| 7 | [Left station sync](#left-station-sync) |
| 8 | Left station sync ack |
| 9 | Start host migration |
| 10 | Start host migration ack |

*6.25 - 6.39:*

In addition to the above:

| Type | Description |
| --- | --- |
| 11 | Detect keep alive timeout |
| 12 | Kick request |

*6.40 - 6.42:*

In addition to the above:

| Type | Description |
| --- | --- |
| 13 | ? |
| 14 | ? |
| 15 | ? |
| 16 | ? |
| 17 | ? |

## Join Request
*6.39:*

| Type | Description |
| --- | --- |
| Uint8 | Message type (0) |
| Uint8 | Number of protocols (N) |
| [ProtocolInfo](#protocolinfo) (N) | Protocol info |
| Uint16 | Application communication version |
| Uint32 | Random value |
| Uint64 | Source constant id |
| Uint16 | Source variable id |
| Uint8 | NAT mapping |
| Uint8 | Is private IPv6 |
| Uint8 (32) | Identification token (ascii) |
| Uint64 | Destination constant id |
| Uint16 | Destination variable id |
| Uint8 | Number of players (P) |
| Uint8 | Number of participants |
| [StationAddress](#stationaddress) | Station address (IPv4 or IPv6) |
| [PlayerInfo](#playerinfo) (P) | Player info |

## Update Session
This message may be split into fragments.

*6.42:*

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 3 | Header |
| 0x3 | 1 | Number of fragments |
| 0x4 | 1 | Fragment index |
| 0x5 | 2 | Fragment offset |
| 0x7 | | Fragment data |

## Left Station Sync
This message may be split into fragments.

*6.42:*

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 11 | Header |
| 0xB | 1 | Number of fragments |
| 0xC | 1 | Fragment index |
| 0xD | 2 | Fragment offset |
| 0xF | | Fragment data |

After reassembling the fragments:

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 1 | Message type (7) |
| 0x1 | 8 | Sender constant id |
| 0x9 | 2 | Unknown |
| 0xB | 1 | Number of entries |
| 0xC | 2 | Unknown |
| 0xE | | [LeftStationInfo](#leftstationinfo) entries |

## ProtocolInfo
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 1 | Protocol id |
| 0x1 | 1 | Protocol version |

## StationAddress
This structure is a wrapper around the [InetAddress](Pia-Types#inetaddress) type, but includes information about whether the address is IPv4 or IPv6.

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 1 | 0 = IPv4, 1 = IPv6 |
| 0x1 | 6 or 18 | [InetAddress](Pia-Types#inetaddress), the size depends on whether it is IPv4 or IPv6 |

## PlayerInfo
The player name may consist of up to 20 characters.

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 16 | Player id |
| 0x10 | 4 | Player name size (in bytes) |
| 0x14 | 1 | Player name encoding (1 = UTF-8, 2 = UTF-16) |
| 0x15 | | Player name |

## LeftStationInfo
*6.42:*

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 8 | Constant id |
| 0x8 | 2 | Variable id |
| 0xA | 2 | Join order |
| 0xC | 2 | Left join order |
| 0xE | 1 | Station index |
| 0xF | 1 | Number of players |
| 0x10 | 1 | Number of participants |
| 0x11 | 32 | Identification token |
| 0x31 | | [PlayerInfo](#playerinfo) (one per player) |