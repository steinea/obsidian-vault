#### Chart

```mermaid
flowchart TD;

BMSW(["(5) Barbara Maria Stella Ward"])
HW(["(10) Herbert Ward"])
WW(["(20) Willie Ward"])
PW(["(40) Peter Ward"])

PW --> WW --> HW --> BMSW

class BMSW,HW,WW,PW internal-link;

```