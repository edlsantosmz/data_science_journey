# Data Cleaning

## Reshaping your data
* Each variable as a separate column
* Each row as a separate observation


We would want to reshape a table like:

Account	Checking	Savings
“12456543”	8500	8900
“12283942”	6410	8020
“12839485”	78000	92000

Into a table that looks more like:

Account	Account Type	Amount
“12456543”	“Checking”	8500
“12456543”	“Savings”	8900
“12283942”	“Checking”	6410
“12283942”	“Savings”	8020
“12839485”	“Checking”	78000
“12839485”	“Savings”	920000

We can use tidyr’s gather() function to do this transformation. gather() takes a data frame and the columns to unpack:
```
df %>%
  gather('Checking','Savings',key='Account Type',value='Amount')
```
