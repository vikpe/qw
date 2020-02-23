# Stats schema proposal
> this is a draft

## Thoughts
* **Which properties should be mandatory?**
* **Which properties should be optional?**
* **How to calculate match ID? (sha256 of match.started.concat([player_names])?)**
* **Nested levels or flattened key?**
  * `player.[n].stats.weapons.sg.acc.attacks` or 
  * `player.[n].stats.weapons_sg_acc_attacks`
* Should we provide a dictionary for terms used?
  * E.g: `health_15` - Small healthpack  
* We create a tool to convert between
  * major versions.
  * existing schemas
* Would be nice with enough info to generate screenshots.
* How to handle:
  * overtime?
  * other irregularities?
  * non-deathmatch game modes, such as race?
* What data can u get from a QWD (compared to MVD)?

## Schema
Property | Type | | Example | Description
--- | --- | --- | --- | ---
`schema_version` | `(string)` | | `1.0.0` | Version of stats schema.
|||
**`match`** | `(object)` | | |
&nbsp;&nbsp; `id` | `(int)` | | `3BCADE2038A9F726EF` | Unique ID of match
&nbsp;&nbsp; `started` | `(int)` | | `2020-01-01 20:00:00 UTC` | Timestamp when match started
&nbsp;&nbsp; `ended` | `(int)` | | `2020-01-01 20:20:00 UTC` | Timestamp when match ended
&nbsp;&nbsp; `duration` | `(int)` | | `20` | Match duration in minutes
&nbsp;&nbsp; `[more info...]` | `(any)` | optional | | More info
|||
**`settings`** | `(object)` | | |
&nbsp;&nbsp; `mode` | `(string)` | | `team` | Mode (`duel/team`)
&nbsp;&nbsp; `deathmatch` | `(int)` | | `2` | Deathmatch
&nbsp;&nbsp; `fraglimit` | `(int)` | | `50` | Fraglimit
&nbsp;&nbsp; `teamplay` | `(int)` | | `2` | Teamplay
&nbsp;&nbsp; `timelimit` | `(int)` | | `20` | Timelimit
&nbsp;&nbsp; `[more settings...]` | `(any)` | optional | | More settings
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
&nbsp;&nbsp;&nbsp;&nbsp; `[n].[more stats..]` | `(any)` | optional | | More stats
|||
**`players`** | `(array)` | | |
&nbsp;&nbsp; `[n].name` | `(string)` | | `silverfish` | Name (normalized)
&nbsp;&nbsp; `[n].name_raw` | `(string)` | | `silver^f^i^s^h` | Name (raw)
&nbsp;&nbsp; `[n].team` | `(string)` | | `fOm` | Team name (normalized)
&nbsp;&nbsp; `[n].bottomcolor` | `(string)` | | `4` | Bottom color
&nbsp;&nbsp; `[n].topcolor` | `(string)` | | `2` | Top color
&nbsp;&nbsp; `[n].ping` | `(int)` | (optional) | `25` | Ping
&nbsp;&nbsp; `[n].disconnected` | `(bool)` | (optional) | `false` | Player disconnected
&nbsp;&nbsp; `[n].stats` | `(object)` | | | Player stats
&nbsp;&nbsp;&nbsp;&nbsp; `frags` | `(int)` | | `252` | Frags
&nbsp;&nbsp;&nbsp;&nbsp; `kills` | `(int)` | | `256` | Kills
&nbsp;&nbsp;&nbsp;&nbsp; `deaths` | `(int)` | | `198` | Deaths
&nbsp;&nbsp;&nbsp;&nbsp; `teamkills` | `(int)` | | `4` | Teamkills
&nbsp;&nbsp;&nbsp;&nbsp; `[more stats..]` | `(any)` | optional | | More stats
|||
**`source`** | `(object)` | optional | |
&nbsp;&nbsp; `type` | `(string)` | | `demo` | Type (`demo`/`stats_file`)
&nbsp;&nbsp; `filename` | `(string)` | | `2on2_red_vs_blue[dm2]170722-1131.mvd` | Filename
|||
**`server`** | `(object)` | optional | |
&nbsp;&nbsp; `hostname` | `(string)` | | `badplace.eu` | Hostname
&nbsp;&nbsp; `ip` | `(string)` | | `202.151.22.12` | IP
&nbsp;&nbsp; `port` | `(int)` | | `27501` | Port number
|||
**`custom`** | `(object)` | optional | | 
&nbsp;&nbsp; `[key]` | `(any)` | | `EQL 10 Grand Final` | Custom info
