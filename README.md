# Draft config/locs

## Locs
1. create a backup of your current `dm2.loc`, `dm3.loc` and `e1m2.loc`.
2. copy locs from repo to `qw/locs/`

## Config
**Setup/save config**
1. copy `tvs_alias.cfg` and `tvs_tp.cfg` to `id1/`
1. edit player settings and binds in `tvs_tp.cfg`
1. start ezquake
1. load your current config
1. `/exec tvs_tp.cfg`
1. `/cfg_save xx`

Draft config is now saved at `ezquake/configs/xx.cfg`.

**Load config**

```
/cfg_load xx
```

### MM3
* **armor**: `red`, `yellow`, `green`
* **rocket**: `rock`,  e.g. "rock at tunnel"
* **item times** - declare `the time it next spawns` (if you take low on :12 then declare "low on 42")
* **enemy powerups** - `"enemy quad at <location>"` or `"enemy quad going to <location>"`
  * really helps to know e.g. is enemy taking quad to yellow, or to ring etc
