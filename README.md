# `purging` for mediation effects

### Simple method for addressing mediation effects among independent variables

Though there are some great packages for mediation analysis out there, the simple intuition of its need is often ambiguous, especially for younger graduate students. Thus, this is set of files provides a quick, intuitive overview of mediation and the need and a simple method for "purging" variables for use in multivariate analysis.

Let's say we had a model where womens' level of labor force participation determines their level of contraceptive use, and that the effect of female labor force participation on fertility is indirect, essentially filtered through its impact on contraceptive use. Once we control for contraceptive use, the direct effect of labor force participation (seen in the simple bivariate model, _lm1_, in the example code, `purging.R`) goes away. In other words, the effect of labor force participation on fertility is likely indirect, and filtered through contraceptive use. 

This is a simple way of thinking about mediation effects (i.e., a Mediation model:  Labor Force (_indirect_) -> Contraception (_direct_) -> Fertility). If we run into this problem, a simple solution is "purging". First, regress the direct variable (in this case, "contraceptive use") on the indirect variable (in this case, "labor force participation"). Then, store those residuals, which is the effect of direct effect of contraception after accounting for the indirect effect of labor force participation. Then, we add the stored residuals as their own "purged variable" in the updated specification. Essentially, this purging process allows for a new contraception variable that is _uncorrelated_ with female work force participation. When we do this, we will see that each variable is explaining difference variable in the DV of interest (you can double check this several ways, such as comparing correlation coefficients or by comparing R^2). See the attached code file, `purging.R` for the example using real data from the United Nations Human Development Programme. Many thanks to Scott Basinger and Patrick Shea (University of Houston) for the base of the example and UN data from their stats labs.

The `UN.csv` file is a small dataset based on the 2005 United Nations Human Development Programme report, with all data from 2003. Variables include: Human Development Index (HDI: combining female life expectancy at birth (Life), educational attainment, and income per capita); fertility rate (Fert: births per adult female); percentage of women using contraception (Cont); tech adoption as share of the population using cell phones (Cell: subscribers per 1000 people) and the share of the population using the internet (Inter: subscribers per 1000 people); per capita gross domestic product (GDP) in US dollars; carbon dioxide emissions per capita (CO2) measured in metric tons; female adult literacy rate (Liter); and finally adult women in the labor force per 100 men (FemEc).

Feel free to [reach out](http://www.philipdwaggoner.com/) if anything is unclear or if you want to chat more about mediation models/analysis, causal inference, etc. Once the intuition is mastered, check out some great work on mediation from many folks, including Kosuke Imai (Princeton), Luke Keele (Georgetown), and several others. See Imai's mediation site as a sound starting place with [code, papers, and more](https://imai.princeton.edu/projects/mechanisms.html). 
