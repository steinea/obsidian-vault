# Building

[[activity]]

```dataview

TABLE series, item, pieces, age, status
from "constellation/lego"
where status = "built" OR status = "unbuilt" OR status = "wishlist"
sort status ASC, file.name ASC

```