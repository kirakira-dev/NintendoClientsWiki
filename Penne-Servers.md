[Switch](#switch) > Push Notifications (Penne)
---

Penne is the replacement for [NPNS](NPNS-Servers). It was introduced in system version 18.0.0.

Penne uses HTTP/2. The request and response are JSON-encoded.

### god
| Method | Path |
| --- | --- |
| DELETE | [`/v1/accounts/<id>`](#delete-v1accountsid) |
| POST | [`/v1/accounts/<id>/links`](#post-v1accountsidlinks) |
| DELETE | [`/v1/accounts/<id>/links`](#delete-v1accountsidlinks) |
| POST | [`/v1/accounts/<id>/notification_tokens`](#post-v1accountsidnotification_tokens) |
| ? | `/v1/immigrate` |
| ? | `/v1/penne_ids` |

### val
| Method | Path |
| --- | --- |
| GET | [`/v1/frontlines`](#get-v1frontlines) |
| POST | [`/v1/login_tickets`](#post-v1login_tickets) |

## DELETE /v1/account/&lt;id>
| Field | Description |
| --- | --- |
| penne_id | Penne id |

Response on success:

| Field | Description |
| --- | --- |
| result | `ok` |

## POST /v1/accounts/&lt;id>/links
| Field | Description |
| --- | --- |
| penne_id | Penne id |
| password | Password |
| nsa_id_token | [BaaS](BAAS-Server) id token |

Response on success:

| Field | Description |
| --- | --- |
| nsa_id | BaaS user id |

## DELETE /v1/accounts/&lt;id>/links
| Field | Description |
| --- | --- |
| penne_id | Penne id |
| password | Password |

Response on success:

| Field | Description |
| --- | --- |
| nsa_id | BaaS user id |

## POST /v1/accounts/&lt;id>/notification_tokens
| Field | Description |
| --- | --- |
| id | Penne id |
| application_id | Hex number (e.g. `0x010000000000003e`) |

Response on success:

| Field | Description |
| --- | --- |
| notification_token | Notification token (36 hex digits) |

## GET /v1/frontlines
Response on success:

| Field | Description |
| --- | --- |
| current_time | Current timestamp |
| frontline_fqdn | Frontline server URL (e.g. `fro-4.hac.lp1.penne.srv.nintendo.net`) |
| persistent_connection_params_simple | [Persistent connection params](#persistent-connection-params) |

## POST /v1/login_tickets
| Field | Description |
| --- | --- |
| id | Penne id |
| password | Penne password |

Response on success:

| Field | Description |
| --- | --- |
| expires_at | Expiration timestamp. A ticket is valid for 4 days. |
| frontline_fqdn | Frontline server URL (e.g. `fro-4.hac.lp1.penne.srv.nintendo.net`) |
| issued_at | Issued at timestamp |
| persistent_connection_params_simple | [Persistent connection parameters](#persistent-connection-params) |
| ticket | Penne ticket |

## Persistent Connection Params
The persistent_connection_params_simple object contains the following fields:

| Field | Description |
| --- | --- |
| awake | Awake parameters (see below) |
| ignore_rst | Boolean (true) |
| retry_count | Integer (2) |
| sleep | Sleep parameters (see below) |
| wait_sec | Integer (3600) |

The awake and sleep objects contain the following fields:

| Field | Description |
| --- | --- |
| count | Integer (2 in awake, 1440 in sleep) |
| idle | Integer (60) |
| interval | Integer (10) |