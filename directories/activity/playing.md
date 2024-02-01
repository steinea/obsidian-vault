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

#### Complete

```dataview

TABLE date, platform, duration, trophies
from "constellation/games"
where progress = "complete"
sort date DESC

```
