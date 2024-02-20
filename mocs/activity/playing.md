# Playing


#### Now

```dataview

TABLE date, platform, duration, trophies
from "constellation/games"
where progress = "now"
sort file.name ASC

```

<br>

#### Next

```dataview

TABLE platform, howlongtobeat
from "constellation/games"
where progress = "next"
sort platform, file.name ASC

```

<br>

#### Completed

```dataview

TABLE date, platform, duration, trophies
from "constellation/games"
where progress = "complete"
sort date DESC

```

<br>

#### Stopped

```dataview

TABLE date, platform, duration, trophies
from "constellation/games"
where progress = "stopped"
sort file.name ASC

```