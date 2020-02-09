# Game stats schema
> this is a draft

## Thoughts
* Changes to schema should be documented and versioned ([semantic versioning](https://semver.org/))
* We create a tool to convert between major versions.
* Which properties should be mandatory?
* Which properties should be optional?
* Should it omit properties that are obsolete depending or game mode (or output empty values)?
  * E.g. should a 1on1 output contain `teams: []`?
* Should it contain duplicate/aggregated data to help consumers or keep it minimal?  
  * E.g. `color: 4 2` vs `topcolor: 4, bottomcolor: 2`.
  * See verbose vs minimal examples below.
* Would be nice to include an id/hash that is unique for each game.
* Would be nice with enough info to generate screenshots.
* How to handle:
  * disconnected players?
  * overtime?
  * other irregularities?
  * non-deathmatch game modes, such as race?
* What data can u get from a QWD (compared to MVD)?
* Could/should we use game tags in a systematic way? E.g. `Official / EQL / EQL9 / Div1 Group Game` (similar to [Pip classifiers](https://pypi.org/classifiers/))

### Schema (verbose)
```json
{
  "schema_version": "0.1.0",
  
  "game": {
    "id": "3BCADE2038A9F726EF7BDDF1DA112CACA9EC60D0AF",
    "started": "2020-02-09 20:51 UTC",
    "ended": "2020-02-09 21:11 UTC",
    "duration": "20",
    "mode": "4on4",
    "tag": "EQL20",
    "map": "dm3"
  },
  
  "players": [
    {
      "name": "XantoM",
      "name_raw": "XantoM",
      "team": "fOm",
      "topcolor": "4",
      "bottomcolor": "2",
      "disconnected": false,
      "stats": {
        "frags": "46",
        "kills": "50",
        "deaths": "40",
        "teamkills": "4",
        "quads_taken": "3",
        "[more_stats]": "[...]"
       }
    }
  ],
  
  "teams": [
    {
      "name": "fOm",
      "name_raw": "f^Om",
      "players": [
        "XantoM",
      ],
      "stats": {
        "frags": "46",
        "kills": "50",
        "deaths": "40",
        "teamkills": "4",
        "quads_taken": "3",
        "[more_stats]": "[...]"
      }
    }
  ]
}
```

### Schema (minimal/normalized)
```json
{
  "schema_version": "0.1.0",
  
  "game": {
    "id": "3BCADE2038A9F726EF7BDDF1DA112CACA9EC60D0AF",
    "started": "2020-02-09 20:51 UTC",
    "ended": "2020-02-09 21:11 UTC",
    "mode": "4on4"
  },
  
  "players": [
    {
      "name": "XantoM",
      "team": "f^Om",
      "color": "4 2",
      "disconnected": false,
      "stats": {
        "kills": "50",
        "deaths": "40",
        "teamkills": "4",
        "quads_taken": "3",
        "[more_stats]": "[...]"
       }
    }
  ]
}
```
