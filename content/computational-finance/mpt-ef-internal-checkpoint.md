---
title: Internal Checkpoint
description: A consise overview of key plots and steps to QC our outputs
authors:
  - userId: fI5cWFyZPEZCTpIHdqX5H8OU3Iv1
    name: Steve Purves
    orcid: 0000-0002-0760-5497
    corresponding: false
    roles: []
    affiliations: []
date: '2020-12-10T16:22:28.696Z'
name: mpt-ef-internal-checkpoint
oxa: oxa:dvunfvCkr67W5YDXfxGE/0SzCqAXxMjoJgn1i4HUK
tags: []
thumbnail: thumbnails/mpt-ef-internal-checkpoint.png
---

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/ZwE3SLjdrvrTBNPe8hyd.1"}

## Check Data Ingestion

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/BmTqzjmqOORNCwGkCCBt.2"}

```python
quandl.ApiConfig.api_key = 'zCYyKsBbzk94ye5yRjvs'
stocks = ['AAPL','AMZN','GOOGL','FB']
data = quandl.get_table('WIKI/PRICES', ticker = stocks,
                        qopts = { 'columns': ['date', 'ticker', 'adj_close'] },
                        date = { 'gte': '2016-1-1', 'lte': '2017-12-31' }, paginate=True)
data.head()
```

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/sKfcy4WZwUTXaJwgLN2y.2"}

```{mdast} mpt-ef-internal-checkpoint.mdast.json#MMtMOsvSiA
```

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/dByOHFeLjdzgZ4BOzGAV.6"}

```{mdast} mpt-ef-internal-checkpoint.mdast.json#Thvo2A8C1H
```

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/R50svVw6ALsRk6BGHEAB.5"}

```{mdast} mpt-ef-internal-checkpoint.mdast.json#IB7Nc3xmYe
```

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/y3BswGdszeeU9Ditgdq9.4"}

```{mdast} mpt-ef-internal-checkpoint.mdast.json#q2kAv9yg9U
```

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/9VQixVbn0vkNn6oRBU4i.4"}

```{mdast} mpt-ef-internal-checkpoint.mdast.json#lBoOXIYdKr
```

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/DGE4GJ6eDeV6C8wUcTtc.1"}

## Check Monte Carlo Spread

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/JoijFHjrHp5GP81mZ0yA.1"}

```{mdast} mpt-ef-internal-checkpoint.mdast.json#IaJjJDMHQm
```

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/98eDQg3rwNxNrfiBRlGR.2"}

## Check Comparison to Current Position

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/WMCvIGV7lraSxkjWICip.1"}

```{mdast} mpt-ef-internal-checkpoint.mdast.json#ipPKCvfrdK
```

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/fmmKpWJYXtyox5yM0Kbd.1"}

```{mdast} mpt-ef-internal-checkpoint.mdast.json#tkRihwXqRd
```

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/CMNMC8tFRj0vck8H3Ffq.4"}

```{mdast} mpt-ef-internal-checkpoint.mdast.json#TdhyHhzv8A
```

