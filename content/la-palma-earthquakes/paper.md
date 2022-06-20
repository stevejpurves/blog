---
title: "Article: La Palma Seismicity 2021"
description: ""
date: 2021-11-10T11:21:14.856Z
name: paper
oxa: oxa:1Bk7uPlcMuaTyKEshESj/7lITJLg3LX0T0h3VVmAp
---

+++ {"oxa":"oxa:1Bk7uPlcMuaTyKEshESj/pUjKKutoZngkdiA7AaeU.7"}

In September 2021, a significant jump in seismic activity on the island of La Palma (Canary Islands, Spain) signalled the start of a volcanic crisis that still continues at the time of writing. Earthquake data is continually collected and published by the Instituto Geográphico Nacional (IGN). We have created an accessible dataset from this and completed preliminary data analysis which shows seismicity originating at two distinct depths, consistent with the model of a two reservoir system feeding the currently very active volcano.

+++ {"oxa":"oxa:1Bk7uPlcMuaTyKEshESj/Sb7tLNwIcBizqIilcjdF.5"}

# Introduction

La Palma is one of the west most islands in the Volcanic Archipelago of the Canary Islands, a Spanish territory situated is the Atlantic Ocean where at their closest point are 100km from the African coast {numref}`Figure %s <p4bsXV4LbH>`. The island is one of the youngest, remains active and is still in the island forming stage.

```{figure} images/1Bk7uPlcMuaTyKEshESj-ZRWWy3yER1t7RAAVDLMp-v2.png
:name: p4bsXV4LbH

Map of La Palma in the Canary Islands. Image credit [NordNordWest](https://commons.wikimedia.org/w/index.php?curid=76638603)
```

La Palma has been constructed by various phases of volcanism, the most recent and currently active being the *Cumbre Vieja* volcano, a north-south volcanic ridge that constitutes the southern half of the island.

+++ {"oxa":"oxa:1Bk7uPlcMuaTyKEshESj/8ubOyqcjiW7QaP4CtH7j.7"}

## Eruption History

A number of eruptions were recorded since the colonization of the islands by Europeans in the late 1400s, these are summarised in {numref}`Table %s <BgqPdBiswA>`.

~~~{list-table} Recent historic eruptions on La Palma
:header-rows: 1
:name: BgqPdBiswA

* - Name

  - Year

* - Current

  - 2021

* - Teneguía

  - 1971

* - Nambroque

  - 1949

* - El Charco

  - 1712

* - Volcán San Antonio

  - 1677

* - Volcán San Martin

  - 1646

* - Tajuya near El Paso

  - 1585

* - Montaña Quemada

  - 1492

~~~

This equates to an eruption on average every 79 years up until the 1971 event. Probability of a future eruption can be modelled by a Poisson distribution {eq}`VnOOYNFmti`.

```{math}
:label: VnOOYNFmti

p(x)=\frac{e^{-\lambda} \lambda^{x}}{x !}
```

Where $\lambda$ is the number of eruptions per year, $\lambda=\frac{1}{79}$ in this case. The probability of a future eruption in the next $t$ years can be calculated by:

```{math}
:label: R2evRgFXRg

p_e = 1-\mathrm{e}^{-t \lambda}
```

So following the 1971 eruption the probability of an eruption in the following 50 years — the period ending this year — was 0.469. After the event the number of eruptions per year moves to $\lambda=\frac{1}{75}$ and the probability of a further eruption within the next 50 years (2022-2071) rises to 0.487 and in the next 100 years, this rises again to 0.736.

## Magma Reservoirs

Studies of the magma systems feeding the volcano, such as {cite:p}`article` has proposed that there are two main magma reservoirs feeding the Cumbre Vieja volcano; one in the mantle (30-40km depth) which charges and in turn feeds a shallower crustal reservoir (10-20km depth).

```{figure} images/1Bk7uPlcMuaTyKEshESj-9fbGlQTuCZQEBgYcu9Ds-v1.png
:name: WLhyFr6NCs

Proposed model from Marrero et al
```

In this paper, we look at recent seismicity data to see if we can see evidence of such a system action, see {numref}`Figure %s <WLhyFr6NCs>`.

+++ {"oxa":"oxa:1Bk7uPlcMuaTyKEshESj/JSgPtGAseshXHQfbXxWK.2"}

# Dataset

The earthquake dataset used in our analysis was generated from the [IGN web portal](https://www.ign.es/web/resources/volcanologia/tproximos/canarias.html) this is public data released under a permissive license. A web scraping script was developed to pull data into a machine-readable form for analysis. That code tool [is available on GitHub](https://github.com/stevejpurves/ign-earthquake-data) along with a copy of recently updated data.

+++ {"oxa":"oxa:1Bk7uPlcMuaTyKEshESj/ta1zlBNixWxhtSgV0M2P.2"}

# Results

The dataset was loaded into a Jupyter notebook [visualizaton](oxa:1Bk7uPlcMuaTyKEshESj/Z3pjZzJ7KnN6TVbWndBR "visualizaton") and filtered down to La Palma events only. This results in 5465 data points which we then visualized to understand their distributions spatially, by depth, by magnitude and in time.

+++ {"oxa":"oxa:1Bk7uPlcMuaTyKEshESj/Nxqbd8rzD748hYWbNyxX.23"}

```{figure} images/1Bk7uPlcMuaTyKEshESj-Nxqbd8rzD748hYWbNyxX-v23.png
:name: 1636561434686

A plot of the depth of records seismic events versus time from the start of the seismic crisis on La Palma. Data points are scaled and colored by event magnitude and three distributions can be clearly identified.
```

+++ {"oxa":"oxa:1Bk7uPlcMuaTyKEshESj/S1ETVqEQCAtB7Xi2pn8C.3"}

From our analysis in {numref}`Figure %s <1636561434686>`, we can see 3 different systems in play.

Firstly, the shallow earthquake swarm leading up to the eruption on 19th September, related to significant surface deformation and shallow magma intrusion.

After the eruption, continuous shallow seismicity started at 10-15km corresponding to magma movement in the crustal reservoir.

Subsequently, high magnitude events begin occurring at 30-40km depths corresponding to changes in the mantle reservoir. These are also continuous but occur with a lower frequency than in the crustal reservoir.

+++ {"oxa":"oxa:1Bk7uPlcMuaTyKEshESj/9z2sWXS1SZo01HI6ejYZ.2"}

# Conclusions

From the analysis of the earthquake data collected and published by IGN for the period of 11 September through to 9 November 2021. Visualization of the earthquake events at different depths appears to confirm the presence of both mantle and crustal reservoirs as proposed by {cite:t}`article`.

+++ {"oxa":"oxa:1Bk7uPlcMuaTyKEshESj/nRkvtLfzlTPB9JW8QfJQ.1"}

A web scraping script was developed to pull data into a machine-readable form for analysis. That code tool [is available on GitHub](https://github.com/stevejpurves/ign-earthquake-data) along with a copy of recently updated data.

