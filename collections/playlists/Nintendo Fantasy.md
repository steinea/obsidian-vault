---
title: Nintendo Fantasy
date: 2024-02-26
permalink: 2024/02/26/nintendo-fantasy
---

# Nintendo Fantasy

[[Playlists]]

* [[Xenoblade Chronicles Definitive Edition]], 2010-06-10
* [[Xenoblade Chronicles X]], 2015-04-29
* [[Crypt of the NecroDancer]], 2015-08-23
* [[Persona 5 Royal]], 2016-09-15
* [[Breath of the Wild]], 2017-03-03
* [[Xenoblade Chronicles 2]], 2017-12-01
* [[Dynasty Warriors 9]], 2018-02-08
* [[Persona 5 Dancing in Starlight]], 2018-05-24
* [[Xenoblade Chronicles 2 Torna The Golden Country]], 2018-09-14
* [[Cadence of Hyrule]], 2019-06-13
* [[Fire Emblem Three Houses]], 2019-07-26
* [[Persona 5 Strikers]], 2020-02-20
* [[Hyrule Warriors Age of Calamity]], 2020-11-20
* [[Fire Emblem Warriors Three Hopes]], 2022-06-24
* [[Xenoblade Chronicles 3]], 2022-07-29
* [[Tears of the Kingdom]], 2023-05-12
* [[Persona 5 Tactica]], 2023-11-17


<p><br></p>

#### Flowchart

```mermaid
flowchart TD;

XCDE(["Xenoblade Chronicles Definitive Edition"])
XCX(["Xenoblade Chronicles X"])
XC2(["Xenoblade Chronicles 2"])
XC2TTGC(["Xenoblade Chronicles 2 Torna The Golden Country"])
XC3(["Xenoblade Chronicles 3"])

XCDE --> XCX --> XC2 --> XC2TTGC --> XC3

class XCDE,XCX,XC2,XC2TTGC,XC3 internal-link;

```

<p><br></p>

```mermaid
flowchart TD;

DW9(["Dynasty Warriors 9"])

COTND(["Crypt of the NecroDancer"])
BOTW(["Breath of the Wild"])
COH(["Cadence of Hyrule"])
HWAOC(["Hyrule Warriors Age of Calamity"])
TOTK(["Tears of the Kingdom"])

COTND -.-> COH

BOTW --> COH --> HWAOC --> TOTK

DW9 -.-> HWAOC

class DW9,COTND,BOTW,COH,HWAOC,TOTK internal-link;

```

<p><br></p>

```mermaid
flowchart TD;

DW9(["Dynasty Warriors 9"])

P5R(["Persona 5 Royal"])
P5DIS(["Persona 5 Dancing in Starlight"])
P5S(["Persona 5 Strikers"])
P5T(["Persona 5 Tactica"])


P5R --> P5DIS --> P5S --> P5T

DW9 -.-> P5S

class DW9,P5R,P5DIS,P5S,P5T internal-link;

```

<p><br></p>

```mermaid
flowchart TD;

DW9(["Dynasty Warriors 9"])

FETH(["Fire Emblem Three Houses"])
FEWTH(["Fire Emblem Warriors Three Hopes"])

FETH --> FEWTH

DW9 -.-> FEWTH

class DW9,FETH,FEWTH internal-link;

```
