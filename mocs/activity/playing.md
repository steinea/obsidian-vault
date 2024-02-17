# Playing

[[activity]]

#### Playing

```dataview

TABLE date, platform, duration, trophies
from "constellation/games"
where progress = "playing"
sort file.name ASC

```

<br>

#### To Play

```dataview

TABLE platform, howlongtobeat
from "constellation/games"
where progress = "toplay"
sort platform, file.name ASC

```

<br>

#### Complete

```dataview

TABLE date, platform, duration, trophies
from "constellation/games"
where progress = "complete"
sort date DESC

```

<br>

#### Stopped Playing

```dataview

TABLE date, platform, duration, trophies
from "constellation/games"
where progress = "stopped"
sort file.name ASC

```