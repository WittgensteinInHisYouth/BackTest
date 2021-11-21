# Backtest Engine
> [_Heritage Capital Management_](https://hcm.com.sg/)'s internal backtest engine.
<!-- buttons -->
<p align="left">
    <a href="https://www.python.org/">
        <img src="https://img.shields.io/badge/python-v3-brightgreen.svg"
            alt="python"></a> &nbsp;
</p>

## Table of Contents
* [General Info](#general-information)
* [Requirements](#requirements)
* [Features](#features)
* [Documentation](#documentation)
* [Contact](#contact)
<!-- * [License](#license) -->


## General Information
This repository provides a Python toolkit for backtesting, outputing several metrics that quant may concern. 
Furthermore, the functionality of converting gross return to net return is particularly useful in hedge fund.

## Requirements
- Python 3.x
- Pandas Library
- A csv/Excel file consist of two columns, i.e, date & return



## Features
In this section, I detail some of the available functionalites. 

- Backtest Metrics
```python
data = pd.read_excel("Daily Return.xlsx", index_col=0, parse_dates=True)
data = data.asfreq('B') # specify the frequency of data, either "B" for business day frequency or "M" for monthly frequency
engine = BackTest(data.squeeze())
engine.compute_stat()
```

```plaintext
Start                                2016-10-03 00:00:00
End                                  2021-09-30 00:00:00
Duration                              1823 days 00:00:00
Return (Ann.) [%]                              21.186223
Volatility (Ann.) [%]                          27.020285
Information Ratio                               0.784086
Final AUM [unitless]                            3.714083
AUM Peak [$]                                    3.714083
Final Return [%]                              272.629228
Max. Drawdown [%]                             -36.867565
Max. Drawdown Duration                 515 days 00:00:00
Avg. Drawdown Duration       186 days 17:08:34.285714286
Max. Underwater Duration               555 days 00:00:00
Total Underwater Duration             1287 days 00:00:00
dtype: object
```
<img width="650" src="https://github.com/waitaminutewhoareyou/BackTest/blob/main/myplot.png">

- Conversion from gross return(before mgn. fee, perf. fee and commission fee) to net reutrn

```Python
data = pd.read_excel("Monthly Return.xlsx", index_col=0, parse_dates=True)
data = data.asfreq('M')
convertor = Gross2Net(data.squeeze())
convertor.main()
```

```plaintext
| Date       |    Raw Ret |   Value after fee |   High water mark |   Accrued performance fee |      NAV |     Net ret |
|:-----------|-----------:|------------------:|------------------:|--------------------------:|---------:|------------:|
| 1972-02-29 |  0         |          0.99875  |           1       |               0           | 0.99875  | -0.00125    |
| 1972-03-31 |  0         |          0.997502 |           1       |               0           | 0.997502 | -0.00249844 |
| 1972-04-30 |  0         |          0.996255 |           1       |               0           | 0.996255 | -0.00374531 |
| 1972-05-31 | -0.0027062 |          0.992313 |           1       |               0           | 0.992313 | -0.0076867  |
| 1972-06-30 |  0         |          0.991073 |           1       |               0           | 0.991073 | -0.00892709 |
| 1972-07-31 |  0         |          0.989834 |           1       |               0           | 0.989834 | -0.0101659  |
| 1972-08-31 |  0         |          0.988597 |           1       |               0           | 0.988597 | -0.0114032  |
| 1972-09-30 |  0.015319  |          1.00251  |           1       |               0.000501069 | 1.002    |  0.00200428 |
| 1972-10-31 |  0.0070103 |          1.00828  |           1       |               0.00165602  | 1.00662  |  0.00662406 |
| 1972-11-30 |  0.11433   |          1.1223   |           1       |               0.0244593   | 1.09784  |  0.0978371  |
| 1972-12-31 |  0.14142   |          1.27961  |           1       |               0.0559217   | 1.22369  |  0.223687   |
| 1973-01-31 |  0.09928   |          1.34364  |           1.22369 |               0.0239916   | 1.31965  |  0.319653   |
```
## Documentation
This section explains the exact calculations happening behind each metrics. I would complete this section after figuring out how to typeset latex in Github.
<img src="https://render.githubusercontent.com/render/math?math=e^{i \pi} = -1">
<!-- Optional -->
<!-- ## License -->
<!-- This project is open source and available under the [... License](). -->

<!-- You don't have to include all sections - just the one's relevant to your project -->
