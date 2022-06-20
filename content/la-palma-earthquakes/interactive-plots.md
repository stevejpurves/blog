---
title: Interactive Plots
description: ""
authors:
  - userId: fI5cWFyZPEZCTpIHdqX5H8OU3Iv1
    name: Steve Purves
    orcid: 0000-0002-0760-5497
    corresponding: false
    roles: []
    affiliations: []
date: 2021-12-14T10:43:51.777Z
name: interactive-plots
oxa: oxa:1Bk7uPlcMuaTyKEshESj/WDq6KWbTREcy77B1KLEO
---

+++ {"oxa":"oxa:1Bk7uPlcMuaTyKEshESj/axI5QtsofVLngsx9rZjg.4"}

In this project, we have prepared a preprint article describing the seismicity recorded during the 2021 eruption on La Palma ([La Palma Seismicity 2021](oxa:1Bk7uPlcMuaTyKEshESj/7lITJLg3LX0T0h3VVmAp "La Palma Seismicity 2021") ) which is available online and in PDF form (EarthArXiv compatible format).

The following interactive figures have been created allowing exploration of the same data used to create the results and figures presented in that paper. The [Notebooks](oxa:1Bk7uPlcMuaTyKEshESj/2ryzUNncnmYvtMiboc2h "Notebooks") used to create these plots are also included here in full and the dataset itself [is available here](https://github.com/stevejpurves/ign-earthquake-data). The shape of the dataset is as shown below:

+++ {"oxa":"oxa:1Bk7uPlcMuaTyKEshESj/LzUwSyPpw6OHFawe4lkV.1"}

~~~{list-table}
:header-rows: 1

* - 

  - Event

  - Date

  - UTC time

  - Local time(\*)

  - Latitude

  - Longitude

  - Depth(km)

  - Magnitude

  - Mag. type

  - Max. int

  - Region

  - More Info

* - 0

  - es2022chvdg

  - 2022-02-02

  - 17:31:41

  - 17:31:41

  - 28.6224

  - -17.9208

  - 0.0

  - 1.7

  - mbLg

  - NaN

  - SE TAZACORTE.ILP

  - NaN

* - 1

  - es2022chfbg

  - 2022-02-02

  - 09:24:25

  - 09:24:25

  - 28.5381

  - -17.8586

  - 34.0

  - 2.2

  - mbLg

  - NaN

  - N FUENCALIENTE DE LA PALMA.ILP

  - NaN

* - 2

  - es2022cffbs

  - 2022-02-01

  - 07:10:21

  - 07:10:21

  - 28.5515

  - -17.8468

  - 11.0

  - 1.6

  - mbLg

  - NaN

  - N FUENCALIENTE DE LA PALMA.ILP

  - NaN

* - 3

  - es2022cfagc

  - 2022-02-01

  - 04:42:34

  - 04:42:34

  - 28.5655

  - -17.8853

  - 9.0

  - 2.2

  - mbLg

  - NaN

  - NW FUENCALIENTE DE LA PALMA.IL

  - NaN

* - 4

  - es2022cewue

  - 2022-02-01

  - 02:57:48

  - 02:57:48

  - 28.5866

  - -17.9535

  - 8.0

  - 1.8

  - mbLg

  - NaN

  - SW TAZACORTE.ILP

  - NaN

~~~

+++ {"oxa":"oxa:1Bk7uPlcMuaTyKEshESj/xD3wrsx0ccarXyCmKImN.1"}

```{mdast} interactive-plots.mdast.json#NwridsdPF3
```

+++ {"oxa":"oxa:1Bk7uPlcMuaTyKEshESj/vNqIQ7okm6T9LoqKOVNu.2"}

## Events Timeline

The following interactive plot shows all event data to date. Make a selection on the lower bar graph in order to filter points on the top plot. To clear the selection, click on an unselected area of the chart.

+++ {"oxa":"oxa:1Bk7uPlcMuaTyKEshESj/8tNtS5WgsfDkzMBVfFZy.6"}

```{mdast} interactive-plots.mdast.json#CLsRiINutM
```

+++ {"oxa":"oxa:1Bk7uPlcMuaTyKEshESj/NCYh399yJygkuFlKdmts.2"}

## Depth and Magnitude Distribution

Upper plot shows Depth vs Magnitude for all data points. Make a selection on the lower bar graph in order to filter points on the top plot to a specific time window. To clear the selection, click on an unselected area of the chart.

+++ {"oxa":"oxa:1Bk7uPlcMuaTyKEshESj/dHZe2kYsT41cTzhNPzTe.4"}

```{mdast} interactive-plots.mdast.json#Mhr9JmtpBv
```

+++ {"oxa":"oxa:1Bk7uPlcMuaTyKEshESj/N0VE2dY7mgF5ENi31AUr.2"}

## Geometric distribution of events

The top two plots show events spatially Depth/Longitude, Depth/Latitude with size indicating magnitude. Coloring is arbitrary based on boundary at 20km depth. Make a selection on the lower bar graph in order to filter points on the top plot to a specific time window. To clear the selection, click on an unselected area of the chart.

+++ {"oxa":"oxa:1Bk7uPlcMuaTyKEshESj/Tp9HP9JVkxfoMO50TUCT.2"}

```{mdast} interactive-plots.mdast.json#Ke7s0SvWiD
```

