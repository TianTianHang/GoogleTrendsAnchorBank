# Google Trends Anchor Bank (G-TAB)

Google Trends is a tool that allows users to analyze the popularity of Google search queries across time and space.
In a single request, users can obtain time series for up to 5 queries on a common scale, normalized to the range from 0 to 100 and rounded to integer precision.
Despite the overall value of Google Trends, rounding causes major problems, to the extent that entirely uninformative, all-zero time series may be returned for unpopular queries when requested together with more popular queries.
We address this issue by proposing
*Google Trends Anchor Bank (G-TAB),*
an efficient solution for the calibration of Google Trends data.
Our method expresses the popularity of an arbitrary number of queries on a common scale without being affected by rounding errors.
The method proceeds in two phases.
In the offline preprocessing phase, an "anchor bank" is constructed, a set of queries spanning the full spectrum of popularity, all calibrated against a common reference query by carefully chaining together multiple Google Trends requests.
In the online deployment phase, any given search query is calibrated by performing an efficient binary search in the anchor bank.
Each search step requires one Google Trends request, but few steps suffice, as we demonstrate in an empirical evaluation.

# Using G-TAB

First you need to setup a Python (written and tested using 3.8.1) virtual environment and installing the packages listed in requirements.txt.

The src/python project structure is as follows:
- config - contains four necessary config files:
- data - contains the input data set as well as the outputs of G-TAB.
- logs - contains logs that are written while constructing new G-TABs.

## Config files 
Each config file needs to contain a single line that is evaluable in Python (i.e. eval()) and contains some parameters: 
### blacklist.config:
Contains a Python set with FreeBase IDs that are disallowed when sampling.
