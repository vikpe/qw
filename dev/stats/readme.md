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
