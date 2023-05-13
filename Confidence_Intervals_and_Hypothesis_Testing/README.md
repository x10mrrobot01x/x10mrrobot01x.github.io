# Confidence Intervals and Hypothesis Testing

---

```python
import pandas as pd
import numpy as np
import math
import scipy.stats as st

# create 50 randomly chosen values from a Normal distribution. (arbitrarily using mean=2.48 and standard deviation=0.50). 
diameters = np.random.normal(2.4800,0.500,50)

# convert the array into a dataframe with the column name "diameters" using pandas library.
diameters_df = pd.DataFrame(diameters, columns=['diameters'])
diameters_df = diameters_df.round(2)

# print the dataframe (note that the index of dataframe starts at 0).
print("Diameters data frame\n")
print(diameters_df)
```

    Diameters data frame
    
        diameters
    0        2.83
    1        2.64
    2        3.26
    3        3.40
    4        2.14
    5        2.38
    6        3.37
    7        2.60
    8        2.33
    9        2.10
    10       2.56
    11       2.58
    12       1.89
    13       1.83
    14       2.65
    15       3.14
    16       2.79
    17       2.04
    18       2.81
    19       2.30
    20       2.99
    21       2.76
    22       3.17
    23       1.38
    24       2.76
    25       2.01
    26       2.14
    27       2.82
    28       2.76
    29       2.80
    30       1.88
    31       2.43
    32       2.72
    33       3.26
    34       2.91
    35       2.68
    36       2.72
    37       2.70
    38       1.86
    39       1.91
    40       2.55
    41       2.81
    42       2.15
    43       1.91
    44       2.36
    45       2.02
    46       2.56
    47       2.66
    48       2.85
    49       1.80



```python
# Python methods that calculate confidence intervals require the sample mean and the standard error as inputs.

# calculate the sample mean
mean = diameters_df['diameters'].mean()

# input the population standard deviation, which was given in Step 1.
std_deviation = 0.5000

# calculate standard error = standard deviation / sqrt(n)   where n is the sample size.
stderr = std_deviation/math.sqrt(len(diameters_df['diameters']))

# construct a 90% confidence interval.
conf_int_90 = st.norm.interval(0.90, mean, stderr)
print("90% confidence interval (unrounded) =", conf_int_90)
print("90% confidence interval (rounded) = (", round(conf_int_90[0], 2), ",", round(conf_int_90[1], 2), ")")
print("")

# construct a 99% confidence interval.
conf_int_99 = st.norm.interval(0.99, mean, stderr)
print("99% confidence interval (unrounded) =", conf_int_99)
print("99% confidence interval (rounded) = (", round(conf_int_99[0], 2), ",", round(conf_int_99[1], 2), ")")
```

    90% confidence interval (unrounded) = (2.4030912846323322, 2.635708715367667)
    90% confidence interval (rounded) = ( 2.4 , 2.64 )
    
    99% confidence interval (unrounded) = (2.337261363228155, 2.7015386367718444)
    99% confidence interval (rounded) = ( 2.34 , 2.7 )



```python
from statsmodels.stats.weightstats import ztest

# run z-test hypothesis test for population mean. The value under the null hypothesis is 2.30.
test_statistic, p_value = ztest(x1 = diameters_df['diameters'],  value = 2.30)

print("z-test hypothesis test for population mean")
print("test-statistic =", round(test_statistic,2))
print("two tailed p-value =",round(p_value,4))
```

    z-test hypothesis test for population mean
    test-statistic = 3.35
    two tailed p-value = 0.0008



```python

```
[BACK](../README.md)
