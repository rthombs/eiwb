# `eiwb`
A Stata command to generate a variable for the ecological intensity of well-being.

# Description 
`eiwb` generates a variable for the ecological intensity of well-being (EIWB) based on the work of Dietz et al. ([2009](https://www.jstor.org/stable/24707742?casa_token=PjbQRnaCzQYAAAAA%3A-o3_44JvD8TZlZawMEHZX4kL-rjtKk0egXsfrXhfXc4MuHKuOt_D3_HDEbh19ELPyDw6CDDZJs4kP7tZImPQ0sR03qAvs2zKZm85Yj3r_Ie3w3o3Kxo&seq=1#metadata_info_tab_contents), [2012](https://www.sciencedirect.com/science/article/pii/S014362281000144X?casa_token=RPDaJATGXmwAAAAA:wRtGCgZ1XgDlGkfxeq61PLXZNJl9_iI4KTQ500kS5ES4D77wONXC1S3OmtAO3z3-9TLzHj0tOg)). The EIWB measures 
how much stress is placed on the environment per unit of human well-being **(environmental stress/human well-being)**. To prevent the numerator or 
denominator from dominating the ratio, the coefficient of variation of the two variables must be constrained to be equal (see New Economics Foundation [2009](https://neweconomics.org/uploads/files/08f0708bcd8da25563_0n8m6j8bw.pdf); Dietz et al. [2012](https://www.sciencedirect.com/science/article/pii/S014362281000144X?casa_token=RPDaJATGXmwAAAAA:wRtGCgZ1XgDlGkfxeq61PLXZNJl9_iI4KTQ500kS5ES4D77wONXC1S3OmtAO3z3-9TLzHj0tOg)). 
This is done by adding a constant (referred to as the correction factor) to the variable with the larger coefficient of variation, which shifts the mean without changing the variance. 
The ratio is then multiplied by 100 to scale it. Following the generation of the variable, the coefficients of variation and the calculated correction factor are displayed on screen.

# Syntax

    eiwb varlist(min=2 max=2) [, vname(string) ln]

where the environmental variable **must be specified first** in the variable list. 

## Options

`vname(string)` specifies the name of the variable to be generated; default variable name is `eiwb`. 

`ln` creates a variable consisting of the natural logarithms of the eiwb values. The variable includes a `_ln` suffix. 

 # Example 

 As an example, say our environmental indicator is CO<sub>2</sub> emissions per capita (co2pc) and our indicator of human well-being is health-adjusted life expectancy (hale).

 **Then we can generate the eiwb by (make sure to specify the environmental variable first):**

    eiwb co2pc hale

 **Because out environmental variable is CO<sub>2</sub> emissions per capita, we can more aptly name it the ciwb (Jorgenson [2014](https://www.nature.com/articles/nclimate2110); Kelly [2020](https://academic.oup.com/sf/article-abstract/99/1/178/5714786)):**

    eiwb co2pc hale, vname(ciwb)

 **We can also generate an additional variable that consists of the natural logarithms of the eiwb:**

    eiwb co2pc hale, vname(ciwb) ln

# Install 

`eiwb` can be installed by typing the following in Stata:

    net install eiwb, from("https://raw.githubusercontent.com/rthombs/eiwb/main")

# Author

[**Ryan P. Thombs**](ryanthombs.com)  
**(Boston College)**  
**Contact Me: [thombs@bc.edu](mailto:thombs@bc.edu)**


