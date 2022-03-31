## Game Detail
This feed contains the full boxscore for an archived game. The archived game response will restart every 3 hours, starting at 12:00AM CDT, and will conclude in a post game state at the end of the 3 hour session. To force a particular game state response, simply provide a query parameter to your request with a valid `state` value, as illustsrated below in the Query Parameters.

If no valid state parameter is provided, the response will contain the archived game response for that time, relative to the 3 hour window. For example, a request without a query parameter present, sent to the endpoint below at 1:15PM CDT will respond with a live game state in the 2nd quarter.

**URL** : `/api/archived-game/0022101142`

**Method** : `GET`

**Auth required** : NO

**Query Parameters**

| Parameter | Type | Required? | Default Value | Accepted Values | Notes |
| -------------- | ----------------------------------- | :-------: | :-----------: | ---------------------------------------------------------------------------------------- |
| `state` | `string` | False | none | _pregame_, _live_, _halftime_, _postgame_| Force a specific game state response |

## Success Response

**Code** : `200 OK`

**Example Content**

```json
{
    "g": {
      "mid": 1646340841581,
      "gid": 0022101142,
      "gdte": "2022-03-30",
      //...
    }
}
```

## Game Object Detail

**Game Response Schema**

| Key | Value Type | Notes |
| -------------- | ----------------------------------- | ---------------------------------------------------------------------------------------- |
| `mid` | `number` | Message ID |
| `gid` | `string` | Game ID |
| `gdte` | `string` | Game Date Eastern |
| `htm` | `string` | Game Time for Home Team |
| `vtm` | `string` | Game Time for Away Team |
| `etm` | `string` | Game Time Eastern |
| `gdtutc` | `string` | Game Time UTC |
| `utctm` | `string` | Game Time UTC in "hh:mm" 24 hour format |
| `ac` | `string` | Arena City |
| `as` | `string` | Arena State |
| `gcode` | `string` | Game Code |
| `next` | `string` | Next file requested |
| `ar` | `number` | 0 or 1, "is video archive available". Not used. |
| `p` | `number` | Period |
| `st` | `number` | Game Status (1=pregame, 2=in progress, 3=complete) |
| `stt` | `string` | Game Status Text |
| `cl` | `string` | Clock |
| `lpla` | `object` | Last event/play that occurred. ([lpla object detail](#lpla))|
| `vls` | `object` | Visitor Line Score Object ([team line score object detail](#tls)) |
| `hls` | `object` | Home Line Score Object ([team line score object detail](#tls)) |
| `offs` | `object` | Officials Object ([offs object detail](#offs)) |
| `an` | `string` | Arena Name |
| `at` | `number` | Attendance |
| `gsts` | `object` | Game Stats Object ([gsts object detail](#gsts)) |
| `dur` | `string` | Game Duration |


## Last Play (lpla) Object Detail {#lpla}

**Response Schema**

| Key | Value Type | Notes |
| -------------- | ----------------------------------- | ---------------------------------------------------------------------------------------- |
| `evt` | `number` | Event |
| `cl` | `string` | Clock |
| `de` | `string` | Description |
| `locX` | `number` | Court location X |
| `locY` | `number` | Court location Y |
| `opt1` | `number` | Option – Event Type 1 |
| `opt2` | `number` | Option – Event Type 2 |
| `mtype` | `number` | Message Type |
| `etype` | `number` | Event Type |
| `opid` | `string` | Opposing player ID (e.g. for fouls) |
| `tid` | `number` | Player ID |
| `pid` | `number` | Team ID (of player id) |
| `hs` | `number` | Home Team Score |
| `vs` | `number` | Visitor Team Score |
| `epid` | `string` | Extra Person ID |
| `oftid` | `number` | The offensive team’s id |


## Team Line Score (vls or hls) Object Detail {#tls}
This object represents either the Visitor Line Score (visiting team), or the Home Line Score (home team).
**Response Schema**

| Key | Value Type | Notes |
| -------------- | ----------------------------------- | ---------------------------------------------------------------------------------------- |
| `s` | `number` | Score |
| `ftout` | `number` | Full timeouts remaining |
| `stout` | `number` | Short timeouts remaining |
| `ta` | `string` | Team Abbreviation (ex. HOU) |
| `tstsg` | `object` | Team Stats (game) Object ([tstsg object detail](#tstsg)) |
| `pstsg` | `array` | Array of Player Stats (game) Object ([pstsg object detail](#pstsg)) |
| `tn` | `string` | Team Name |
| `tc` | `string` | Team City |
| `tid` | `number` | Team ID |
| `q1` | `number` | Quarter 1 Points (if game of two halves, this is First Half Points) |
| `q2` | `number` | Quarter 2 Points (if game of two halves, this is Second Half Points) |
| `q3` | `number` | Quarter 3 Points (if game of two halves, this is always zero) |
| `q4` | `number` | Quarter 4 Points (if game of two halves, this is always zero) |
| `ot1` | `number` | Overtime 1 Points |
| `ot2` | `number` | Overtime 2 Points |
| `ot3` | `number` | Overtime 3 Points |
| `ot4` | `number` | Overtime 4 Points |
| `ot5` | `number` | Overtime 5 Points |
| `ot6` | `number` | Overtime 6 Points |
| `ot7` | `number` | Overtime 7 Points |
| `ot8` | `number` | Overtime 8 Points |
| `ot9` | `number` | Overtime 9 Points |
| `ot10` | `number` | Overtime 10 Points |


## Team Stats Game (tstsg) Object Detail {#tstsg}

**Response Schema**

| Key | Value Type | Notes |
| -------------- | ----------------------------------- | ---------------------------------------------------------------------------------------- |
| `fga` | `number` | Field Goals Attempted |
| `fgm` | `number` | Field Goals Made |
| `tpa` | `number` | Three Pointers Attempted |
| `tpm` | `number` | Three Pointers Made |
| `fta` | `number` | Free Throws Attempted |
| `ftm` | `number` | Free Throws Made |
| `oreb` | `number` | Offensive Rebounds |
| `dreb` | `number` | Defensive Rebounds |
| `reb` | `number` | Rebounds |
| `ast` | `number` | Assists |
| `stl` | `number` | Steals |
| `blk` | `number` | Blocks |
| `pf` | `number` | Fouls |
| `tov` | `number` | Turnovers |
| `fbpts` | `number` | Fastbreak Points |
| `fbptsa` | `number` | Fastbreak Points Attempted |
| `fbptsm` | `number` | Fastbreak Points Made |
| `pip` | `number` | Points In the Paint |
| `pipa` | `number` | Points in the Paint Attempted |
| `pipm` | `number` | Points in the Paint Made |
| `ble` | `number` | Biggest Lead |
| `bpts` | `number` | Bench points |
| `tf` | `number` | Team Technical Fouls |
| `scp` | `number` | Team Second Chance Points |
| `tmreb` | `number` | Team rebounds (not cumulative) |
| `tmtov` | `number` | Team turnovers (not cumulative) |
| `potov` | `number` | Points off turnovers |


## Player Stats Game (pstsg) Object Detail {#pstsg}

**Response Schema**

| Key | Value Type | Notes |
| -------------- | ----------------------------------- | ---------------------------------------------------------------------------------------- |
| `fn` | `string` | First Name |
| `ln` | `string` | Last Name |
| `num` | `string` | Jersey Number |
| `pos` | `string` | Position |
| `min` | `number` | Minutes Played |
| `sec` | `number` | Seconds Played (beyond Minutes Played) |
| `totsec` | `number` | Total Seconds Played (Minutes Played * 60 + Seconds Played) |
| `fga` | `number` | Field Goal Attempted |
| `fgm` | `number` | Field Goals Made |
| `tpa` | `number` | Three Pointers Attempted |
| `tpm` | `number` | Three Pointers Made |
| `fta` | `number` | Free Throws Attempted |
| `ftm` | `number` | Free Throws Made |
| `oreb` | `number` | Offensive Rebounds |
| `dreb` | `number` | Defensive Rebounds |
| `reb` | `number` | Rebounds |
| `ast` | `number` | Assists |
| `stl` | `number` | Steals |
| `blk` | `number` | Blocks |
| `pf` | `number` | Fouls |
| `pts` | `number` | Points |
| `tov` | `number` | Turnovers |
| `fbpts` | `number` | Fastbreak Points |
| `fbptsa` | `number` | Fastbreak Points Attempted |
| `fbptsm` | `number` | Fastbreak Points Made |
| `pip` | `number` | Points In Paint |
| `pipa` | `number` | Points in the Paint Attempted |
| `pipm` | `number` | Points in the Paint Made |
| `court` | `number` | 1 or 0, on or off court |
| `pid` | `number` | Player ID |
| `pm` | `number` | Plus/Minus |
| `blka` | `number` | Blocks Against |
| `tf` | `number` | Technical Fouls |
| `status` | `string` | Player Status for game: A/I (A is active and eligible to play. I is inactive) |
| `memo` | `string` | Additional notes |


## Officials (offs) Object Detail {#offs}

**Response Schema**

| Key | Value Type | Notes |
| -------------- | ----------------------------------- | ---------------------------------------------------------------------------------------- |
| `fn` | `string` | First Name |
| `ln` | `string` | Last Name |
| `num` | `string` | Jersey Number |


## Game Stats (gsts) Object Detail {#gsts}

**Response Schema**

| Key | Value Type | Notes |
| -------------- | ----------------------------------- | ---------------------------------------------------------------------------------------- |
| `lc` | `number` | Times Tied |
| `tt` | `number` | Lead Changes |

