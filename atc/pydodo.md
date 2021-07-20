# PyDodo Commands

This page contains a list of ATCO instructions and their nearest pydodo commands, it is neither complete nor exhaustive. More pydodo commands can be found at the [pydodo specification](https://github.com/alan-turing-institute/dodo/blob/master/Specification.md). The original ATCO instructions were taken from [ground control](https://github.com/project-bluebird/ground-control/blob/main/other/ATC-instructions.md).

| ATC action | Modifier | pydodo Command | Example | Notes
| :--| :--: | :--: | :-- | :-- |
| Change flight level | None | `pydodo.change_altitude ("BAW123",flight_level=100)` | BAW123 descend FL100 | Use `flight_level` argument, not the `altitude` argument |
| Change flight level | Level by (descent only) | N/A | "BAW123 descend FL100 level by OCK" | ATC document suggests to use unmodified commands in first instance |
| Change flight level | When ready (descent only) | N/A |  | |
| Change flight level | Be above/Be below | N/A | "BAW123 descend FL100, be FL120 or below at OCK" | |
| Change flight level | Rate of climb/descent| `pydodo.change_altitude ("BAW123",flight_level=100, vertical_speed=1500)`  | "BAW123 descend FL100, rate of descent 1500 feet per minute or greater" |Optional `vertical_speed` argument is documented but has not been demonstrated to work. Cannot confirm units are in feet/minute - cannot specify "or greater"|
| Change flight level | Expedite | N/A |  | |
| *** | *** | *** | *** | *** |
| Routing instruction | None | `pydodo.direct_to_waypoint ('BAW123','DVR')` | "BAW123 route direct to DVR" | Waypoint must be specified in the aircraft's `list_route`. Unsure if this is currently functional as `list_route` does not update to reflect specified waypoint as next waypoint |
| Heading instruction | None | `pydodo.change_heading ('BAW123',heading=125)` | "BAW123 fly heading 125°"| Point the aircraft in a specified direction. |
| Heading instruction | None | N/A | "BAW123 turn left/right 10°"| Heading instruction given as relative heading to aircraft once it's on a straight portion of the route |
| Heading instruction | None | N/A | "BAW123 continue present heading" |  |
| *** | *** | *** | *** | *** |
| Change speed - Mach instruction | None | N/A |  | Used for flight levels typically > 250 |
| Change speed - Knots instruction | None | `pydodo.change_speed ('BAW123',speed=220)` | "BAW123, fly speed 220 knots" | Used for flight levels typically < 250 |
| Change speed - Knots instruction | Set speed or greater | N/A | "BAW123, fly speed 250 knots or greater" |  |
