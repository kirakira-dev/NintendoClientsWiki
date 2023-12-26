## [[NEX Protocols]] > [Data Store](Data-Store-Protocol) > Miitopia 3DS (115)

This page describes the methods that are only seen in Miitopia 3DS.

| Method ID | Method Name |
| --- | --- |
| 47 | [SearchMii](#47-searchmii) |

# (47) SearchMii
## Request
| Type | Name |
| --- | --- |
| [MiiTubeSearchParam](#miitubesearchparam-structure) | param |

## Response
| Type | Name |
| --- | --- |
| [MiiTubeSearchResult](#miitubesearchresult-structure) | pSearchResult |

# Types
## MiiTubeSearchParam ([Structure])
| Type | Name |
| --- | --- |
| [String] | name |
| Uint32 | page |
| Uint8 | category |
| Uint8 | gender |
| Uint8 | country |
| Uint8 | searchType |
| Uint8 | resultOption |

## MiiTubeMiiInfo ([Structure])
| Type | Name |
| --- | --- |
| [DataStoreMetaInfo](Data-Store-Protocol#datastoremetainfo-structure) | metaInfo |
| Uint8 | category |
| Uint8 | rankingType |

## MiiTubeSearchResult ([Structure])
| Type | Name |
| --- | --- |
| [List]&lt;[MiiTubeMiiInfo](#miitubemiiinfo-structure)&gt; | result |
| Uint32 | count |
| Uint32 | page |
| Bool | hasNext |

[String]: NEX-Common-Types#string
[List]: NEX-Common-Types#list
[Structure]: NEX-Common-Types#structure