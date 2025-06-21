## [[NEX Protocols]] > [Ranking Protocol](Ranking-Protocol) > MK8 (112)

This page describes the methods that are only seen in Mario Kart 8.

| Method ID | Method Name |
| --- | --- |
| 14 | GetCompetitionRankingScore |
| 15 | [UploadCompetitionRankingScore](#15-uploadcompetitionrankingscore) |
| 16 | [GetCompetitionInfo](#16-getcompetitioninfo) |

# (15) UploadCompetitionRankingScore
## Request
| Type | Description |
| --- | --- |
| [CompetitionRankingUploadScoreParam] | Param |

## Response
| Type | Description |
| --- | --- |
| Bool | Result |

# (16) GetCompetitionInfo
## Request
| Type | Description |
| --- | --- |
| [CompetitionRankingInfoGetParam] | Param |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[CompetitionRankingInfo]&gt; | Info |

# Types
## CompetitionRankingInfo ([Structure])
| Type | Description |
| --- | --- |
| Uint32 | Id |
| Uint32 | Number of participants |
| [List]&lt;Uint32&gt; | Team scores |

## CompetitionRankingInfoGetParam ([Structure])
| Type | Description |
| --- | --- |
| Uint8 | Rank order |
| [ResultRange] | Result range |

## CompetitionRankingUploadScoreParam ([Structure])
| Type | Description |
| --- | --- |
| Uint32 | Id |
| Uint32 | Season id |
| Uint32 | Unknown |
| Uint32 | Score |
| Uint8 | Team id |
| Uint32 | Team score |
| Bool | Is first upload |
| [qBuffer] | Metadata |

[Result]: NEX-Common-Types#result
[String]: NEX-Common-Types#string
[Buffer]: NEX-Common-Types#buffer
[qBuffer]: NEX-Common-Types#qbuffer
[List]: NEX-Common-Types#list
[Map]: NEX-Common-Types#map
[DateTime]: NEX-Common-Types#datetime
[Structure]: NEX-Common-Types#structure
[Data]: NEX-Common-Types#anydataholder
[ResultRange]: NEX-Common-Types#resultrange-structure
[PID]: NEX-Common-Types#pid

[CompetitionRankingInfo]: #competitionrankinginfo-structure
[CompetitionRankingInfoGetParam]: #competitionrankinginfogetparam-structure
[CompetitionRankingUploadScoreParam]: #competitionrankinguploadscoreparam-structure