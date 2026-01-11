[[Server List]] > BCAT (News)
---

### bcat-list
| URL |
| --- |
| `/api/nx/v1/list/<name>` |

### bcat-topics
| Method | URL |
| --- | --- |
| GET | [`/api/nx/v1/titles/<id>/topics`](#get-apinxv1titlesidtopics) |
| ? | `/api/nx/v1/topics/catalog` |
| ? | `/api/nx/v1/topics/<name>/detail` |
| ? | `/api/nx/v1/topics/<name>/icon` |
| ? | `/api/nx/v2/latest_news/<name>` |
| ? | `/api/nx/v2/topics/<name>/online_archives` |

## GET /api/nx/v1/titles/&lt;id&gt;/topics
| Param | Description |
| --- | --- |
| l | Language (e.g. `en-GB`) |
| c[] | Countries (e.g. `GB`) |

On success, a bcat content container containing the topics for the given title id is returned.