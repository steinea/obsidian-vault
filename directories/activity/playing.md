# Playing

[[activity]]

#### In Progress

```dataview

TABLE date, platform, duration, trophies
from "constellation/games"
where progress = "incomplete"
sort file.name ASC

```

<br>

#### To Play

```dataview

TABLE date, platform, duration, trophies
from "constellation/games"
where progress = "priority"
sort file.name ASC

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

#### Abandoned

```dataview

TABLE date, platform, duration, trophies
from "constellation/games"
where progress = "abandoned"
sort file.name ASC

```