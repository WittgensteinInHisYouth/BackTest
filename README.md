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
* [Control Flow](#control-flow)
* [Features](#features)
* [Screenshots](#screenshots)
* [Setup](#setup)
* [Usage](#usage)
* [Project Status](#project-status)
* [Task List](#task-list)
* [Project Principles and Design Decisions](#project-principles-and-design-decisions)
* [Acknowledgements](#acknowledgements)
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

- Trading Portal
- Follow-up monitor and Feedback Control



## Screenshots
![Example screenshot](./img/screenshot.png)
<!-- If you have screenshots you'd like to share, include them here. -->


## Setup
What are the project requirements/dependencies? Where are they listed? A requirements.txt or a Pipfile.lock file perhaps? Where is it located?

Proceed to describe how to install / setup one's local environment / get started with the project.

```bash
git clone https://github.com/HCMPTELTD/Source-Code.git
```

## Usage
For a detailed practice of the workflow, please consult the [tutorial](examples.com) written by [Yuze Gao](https://github.com/Gxxzx).

`write-your-code-here`


## Project Status
This project is _mostly_ _complete_ . Occasional patches would be added per manager's need. See next section for potential contributions.


## Task List 
- [ ] Automate the process of including new asset.
- [ ] Reset administrative right of SQL 
## Project Principles and Design Decisions

-   Usability is everything: it is better to be self-explanatory than consistent.
-   Everything that has been implemented should be tested.
-   Inline documentation is good; Dedicated (separate) documentation is better.
    The two are not mutually exclusive.
-   Note that many helper functions are written to support major functionality, as such in case of a breakdown or a debug process during trading, error message can propagate through a lengthy chain of low-level helper functions.  <br />
    However, the best practice is to debug from the top-level functions, understanding which major component generates the error message and then track the errors down to lower-level functions.


## Acknowledgements
- This project was originated from Jeff and mostly developed by Zhishe.
- Many thanks to [Yuze Gao](https://github.com/Gxxzx) and [Wenyan Zhang](https://github.com/pikajiu7) for improving code quality.


## Contact
This docs is created and actively maintained by [@Yihong Ji](https://github.com/WittgensteinInHisYouth) - feel free to contact me.



<!-- Optional -->
<!-- ## License -->
<!-- This project is open source and available under the [... License](). -->

<!-- You don't have to include all sections - just the one's relevant to your project -->
