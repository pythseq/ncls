# Nested containment list

[![Build Status](https://travis-ci.org/hunt-genes/ncls.svg?branch=master)](https://travis-ci.org/hunt-genes/ncls) [![PyPI version](https://badge.fury.io/py/ncls.svg)](https://badge.fury.io/py/ncls)

Much faster (i.e. many times) than even the fastest intervaltrees for most purposes.

Paper: https://academic.oup.com/bioinformatics/article/23/11/1386/199545

## Install

```
pip install ncls
```

## Changelog

```
# 2018.01.06 (0.0.23)
- NCLS started segfaulting in travis build for pyranges. Probably due to bad string definition files in travis.

# 2018.05.09 (0.0.16-18)
- add Cython/C helper code for pyranges

# 2018.05.09 (0.0.15)
- add faster method has_overlap that returns True/False

# 2018.05.09 (0.0.11)
- empty NCLS returns [] instead of raising IndexError
```

## Usage

```python
# see the examples/ folder for more examples
from ncls import NCLS

import pandas as pd

starts = pd.Series(range(0, 5))
ends = starts + 100
ids = starts

ncls = NCLS(starts.values, ends.values, ids.values)

it = ncls.find_overlap(0, 2)
for i in it:
    print(i)
# (0, 100, 0)
# (1, 101, 1)
```

## Timings

Better timings coming.

## Citation

> Alexander V. Alekseyenko, Christopher J. Lee; Nested Containment List (NCList): a new algorithm for accelerating interval query of genome alignment and interval databases, Bioinformatics, Volume 23, Issue 11, 1 June 2007, Pages 1386–1393, https://doi.org/10.1093/bioinformatics/btl647
