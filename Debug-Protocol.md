[[NEX Protocols]] > Debug (116)
---

This protocol seems to log your RMC requests.

| Method ID | Method Name |
| --- | --- |
| 1 | [EnableApiRecorder](#1-enableapirecorder) |
| 2 | [DisableApiRecorder](#2-disableapirecorder) |
| 3 | [IsApiRecorderEnabled](#3-isapirecorderenabled) |
| 4 | [GetApiCalls](#4-getapicalls) |
| 5 | SetExcludeJoinedMatchmakeSession |
| 6 | GetExcludeJoinedMatchmakeSession |
| 7 | [GetApiCallSummary](#7-getapicallsummary) |

# (1) EnableApiRecorder
This method does not take any parameters and does not return anything.

# (2) DisableApiRecorder
This method does not take any parameters and does not return anything.

# (3) IsApiRecorderEnabled
## Request
This method does not take any parameters.

## Response
| Type | Description |
| --- | --- |
| Bool | True if the api recorder is enabled |

# (4) GetApiCalls
This method returns `RendezVous::InvalidConfiguration` if the api recorder is disabled.

## Request
| Type | Description |
| --- | --- |
| [List]&lt;[PID]&gt; | Pids |
| [DateTime] | Start time |
| [DateTime] | End time |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[ApiCall](#apicall-structure)&gt; | Api calls |

### ApiCall ([Structure])
| Type | Description |
| --- | --- |
| [String] | Method name |
| [DateTime] | Call time |
| [PID] | User id |

# (7) GetApiCallSummary
This method returns `RendezVous::InvalidConfiguration` if the api recorder is disabled.

## Request
| Type | Description |
| --- | --- |
| [PID] | Target user to request summaries for |
| [DateTime] | Start time |
| [DateTime] | End time |
| Bool | Only includes summaries where the rate limit has been exceeded |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[ApiCallSummary](#apicallsummary-structure)&gt; | Api call summary |

### ApiCallSummary ([Structure])
| Type | Description |
| --- | --- |
| [String] | Method name |
| Uint32 | Rate limit exceeded (0 or 1) |
| Uint32 | Rate limit duration |
| Uint32 | Rate limit max calls |
| [DateTime] | Start time |
| Uint32 | Number of calls above rate limit |
| Uint32 | Total number of calls |

[Result]: NEX-Common-Types#result
[String]: NEX-Common-Types#string
[Buffer]: NEX-Common-Types#buffer
[qBuffer]: NEX-Common-Types#qbuffer
[List]: NEX-Common-Types#list
[Map]: NEX-Common-Types#map
[DateTime]: NEX-Common-Types#datetime
[Structure]: NEX-Common-Types#structure
[Data]: NEX-Common-Types#anydataholder
[PID]: NEX-Common-Types#pid
[ResultRange]: NEX-Common-Types#resultrange-structure