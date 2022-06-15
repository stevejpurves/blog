---
title: Internal Checkpoint
description: A consise overview of key plots and steps to QC our outputs
date: 2020-12-10T16:22:28.696Z
authors:
  - name: Steve Purves
    userId: fI5cWFyZPEZCTpIHdqX5H8OU3Iv1
    orcid: 0000-0002-0760-5497
    corresponding: null
    email: null
    roles: null
    affiliations: null
name: mpt-ef-internal-checkpoint
oxa: oxa:dvunfvCkr67W5YDXfxGE/0SzCqAXxMjoJgn1i4HUK
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

~~~{list-table}
:header-rows: 1

* - 

  - AAPL

  - AMZN

  - FB

  - GOOGL

* - date

  - 

  - 

  - 

  - 

* - 2016-01-04

  - 101.783763

  - 636.99

  - 102.22

  - 759.44

* - 2016-01-05

  - 99.233131

  - 633.79

  - 102.73

  - 761.53

* - 2016-01-06

  - 97.291172

  - 632.65

  - 102.97

  - 759.33

* - 2016-01-07

  - 93.185040

  - 607.94

  - 97.92

  - 741.00

* - 2016-01-08

  - 93.677776

  - 607.05

  - 97.33

  - 730.91

* - 2016-01-11

  - 95.194629

  - 617.74

  - 97.51

  - 733.07

* - 2016-01-12

  - 96.576222

  - 617.89

  - 99.37

  - 745.34

* - 2016-01-13

  - 94.093220

  - 581.81

  - 95.44

  - 719.57

* - 2016-01-14

  - 96.151117

  - 593.00

  - 98.37

  - 731.39

* - 2016-01-15

  - 93.842021

  - 570.18

  - 94.97

  - 710.49

~~~

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/dByOHFeLjdzgZ4BOzGAV.6"}

```{figure} images/dvunfvCkr67W5YDXfxGE-dByOHFeLjdzgZ4BOzGAV-v6.png
:name: 1611010242565
```

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/R50svVw6ALsRk6BGHEAB.5"}

```{figure} images/dvunfvCkr67W5YDXfxGE-R50svVw6ALsRk6BGHEAB-v5.png
:name: 1611010298019
```

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/y3BswGdszeeU9Ditgdq9.4"}

```{figure} images/dvunfvCkr67W5YDXfxGE-y3BswGdszeeU9Ditgdq9-v4.png
:name: 1611010330278
```

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/9VQixVbn0vkNn6oRBU4i.4"}

```{figure} images/dvunfvCkr67W5YDXfxGE-9VQixVbn0vkNn6oRBU4i-v4.png
:name: 1611010349037
```

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/DGE4GJ6eDeV6C8wUcTtc.1"}

## Check Monte Carlo Spread

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/JoijFHjrHp5GP81mZ0yA.1"}

```{figure} images/dvunfvCkr67W5YDXfxGE-JoijFHjrHp5GP81mZ0yA-v1.png
:name: 1611010380375
```

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/98eDQg3rwNxNrfiBRlGR.2"}

## Check Comparison to Current Position

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/WMCvIGV7lraSxkjWICip.1"}

```{figure} images/dvunfvCkr67W5YDXfxGE-WMCvIGV7lraSxkjWICip-v1.png
:name: 1611010412509
```

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/fmmKpWJYXtyox5yM0Kbd.1"}

### Optimal Portfolio Allocations

~~~{list-table}
:header-rows: 1

* - Description

  - Max Sharpe Ratio

  - Minimum Volatility

* - Annualised Return

  - 0.3

  - 0.22

* - Annualised Volatility

  - 0.18

  - 0.16

* - Allocations

  - 

  - 

* - AAPL

  - 45.47

  - 33.61

* - AMZN

  - 27.03

  - 0.32

* - FB

  - 27.1

  - 6.8

* - GOOGL

  - 0.41

  - 59.27

~~~

+++ {"oxa":"oxa:dvunfvCkr67W5YDXfxGE/CMNMC8tFRj0vck8H3Ffq.4"}



