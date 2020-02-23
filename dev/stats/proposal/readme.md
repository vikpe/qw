Property | Type | | Example | Description
--- | --- | --- | --- | ---
`schema_version` | `(string)` | | `1.0.0` | Version of stats schema.
|||
**`match`** | `(object)` | | |
&nbsp;&nbsp; `id` | `(int)` | | `3BCADE2038A9F726EF` | Unique ID of match
&nbsp;&nbsp; `started` | `(int)` | | `2020-01-01 20:00:00 UTC` | Timestamp when match started
&nbsp;&nbsp; `ended` | `(int)` | | `2020-01-01 20:20:00 UTC` | Timestamp when match ended
&nbsp;&nbsp; `duration` | `(int)` | | `20` | Match duration in minutes
|||
**`settings`** | `(object)` | | |
&nbsp;&nbsp; `mode` | `(string)` | | `team` | Mode (`duel/team`)
&nbsp;&nbsp; `deathmatch` | `(int)` | | `2` | Deathmatch
&nbsp;&nbsp; `fraglimit` | `(int)` | | `50` | Fraglimit
&nbsp;&nbsp; `teamplay` | `(int)` | | `2` | Teamplay
&nbsp;&nbsp; `timelimit` | `(int)` | | `20` | Timelimit
|||
**`teams`** | `(array)` | | |
&nbsp;&nbsp; `[n].name` | `(string)` | | `fOm` | Name (normalized)
&nbsp;&nbsp; `[n].name_raw` | `(string)` | | `f^Om` | Name (raw)
&nbsp;&nbsp; `[n].players` | `(array)` | | `[XantoM, mushi]` | Normalized player names
&nbsp;&nbsp; `[n].stats` | `(object)` | | | Team stats
&nbsp;&nbsp;&nbsp;&nbsp; `[n].frags` | `(int)` | | `252` | Frags
&nbsp;&nbsp;&nbsp;&nbsp; `[n].kills` | `(int)` | | `256` | Kills
&nbsp;&nbsp;&nbsp;&nbsp; `[n].deaths` | `(int)` | | `198` | Deaths
&nbsp;&nbsp;&nbsp;&nbsp; `[n].teamkills` | `(int)` | | `4` | Teamkills
&nbsp;&nbsp;&nbsp;&nbsp; `[n].quad_taken` | `(int)` | optional | `5` | Quads taken
&nbsp;&nbsp;&nbsp;&nbsp; `[n].quad_time` | `(int)` | optional | `122` | Quad time
&nbsp;&nbsp;&nbsp;&nbsp; `[n].[more stats..]` | `(any)` | optional | | Additional stats
|||
**`players`** | `(array)` | | |
&nbsp;&nbsp; `[n].name` | `(string)` | | `silverfish` | Name (normalized)
&nbsp;&nbsp; `[n].name_raw` | `(string)` | | `silver^f^i^s^h` | Name (raw)
&nbsp;&nbsp; `[n].bottomcolor` | `(string)` | | `4` | Bottom color
&nbsp;&nbsp; `[n].topcolor` | `(string)` | | `2` | Top color
&nbsp;&nbsp; `[n].disconnected` | `(bool)` | | `false` | Player disconnected
&nbsp;&nbsp; `[n].team` | `(string)` | | `fOm` | Team name (normalized)
&nbsp;&nbsp; `[n].stats` | `(object)` | | | Player stats
&nbsp;&nbsp;&nbsp;&nbsp; `frags` | `(int)` | | `252` | Frags
&nbsp;&nbsp;&nbsp;&nbsp; `kills` | `(int)` | | `256` | Kills
&nbsp;&nbsp;&nbsp;&nbsp; `deaths` | `(int)` | | `198` | Deaths
&nbsp;&nbsp;&nbsp;&nbsp; `teamkills` | `(int)` | | `4` | Teamkills
&nbsp;&nbsp;&nbsp;&nbsp; `quad_taken` | `(int)` | optional | `5` | Quads taken
&nbsp;&nbsp;&nbsp;&nbsp; `quad_time` | `(int)` | optional | `122` | Quad time
&nbsp;&nbsp;&nbsp;&nbsp; `[more stats..]` | `(any)` | optional | | Additional stats
|||
**`server`** | `(object)` | optional | |
&nbsp;&nbsp; `hostname` | `(string)` | | `badplace.eu` | Hostname
&nbsp;&nbsp; `ip` | `(string)` | | `202.151.22.12` | IP
&nbsp;&nbsp; `port` | `(int)` | | `27501` | Port number
|||
**`meta`** | `(object)` | optional | | 
&nbsp;&nbsp; `[key]` | `(any)` | | `EQL 10 Grand Final` | Additional custom info