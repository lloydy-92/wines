# Is there a causal link between a wine's numeric and categorical variables?"
### Goal: Peform ANOVA and Tukey's Test, and Causal Inference techniques to determine if two variables differ significantly from one another. The variables in question are geographical location where the wine was made, it's type (red, white, etc.), and its price ($) and WineEnthusiast rating (x/100).
<br/>

## Visualising correlation between numeric and categorical variables.
<img width="695" height="470" alt="image" src="https://github.com/user-attachments/assets/ef275f77-625b-4145-ba05-7590677bf16b" />

<img width="700" height="470" alt="image" src="https://github.com/user-attachments/assets/05258e67-503f-4187-a0ee-0fedcca8e114" />

<img width="686" height="470" alt="image" src="https://github.com/user-attachments/assets/073609eb-6c22-4430-b36a-966af9f66517" />

<img width="700" height="470" alt="image" src="https://github.com/user-attachments/assets/c10e7d7c-2258-46fb-a866-d0d14d522fc5" />
<br/>

## Statistically testing for correlation between numeric and categorical variables
--- price by type ---<br/>
Test used: Kruskal-Wallis, p-value = 0<br/>
Applied log-transform due to skewness = 11.82<br/>
There is a statistically significant difference in a wine's price across its type (p=0).<br/>

--- points by type ---<br/>
Test used: Kruskal-Wallis, p-value = 1.15e-293<br/>
No transformation applied<br/>
There is a statistically significant difference in a wine's points across its type (p=1.15e-293).<br/>

--- price by continent ---<br/>
Test used: Kruskal-Wallis, p-value = 0<br/>
Applied log-transform due to skewness = 11.82<br/>
There is a statistically significant difference in a wine's price across its continent (p=0).<br/>

--- points by continent ---<br/>
Test used: Kruskal-Wallis, p-value = 0<br/>
No transformation applied<br/>
There is a statistically significant difference in a wine's points across its continent (p=0).<br/>
<br/>

## Statistically testing for causality between numeric and categorical variables

**Summary of Estimated Causal Effects:**
| Categorical Var | Numeric Var |	Confounders Used | OLS Effect |	OLS p-value |	PSM ATT |
|-----------------|-------------|------------------|------------|-------------|---------|
| type | price | continent, points | 7.919863 |	0.000000e+00 | 8.109014 |
| type | points | continent, price | 0.183497 |	1.178687e-29 | -1.550203 |
| continent |	price |	type, points | 0.240251 |	1.696970e-01 | 9.635554 |
| continent |	points | type, price | 0.001863 |	9.052154e-01 | -1.657526 |
<br/><br/>


### Does wine type cause differences in price?
It is clear to see that, even after controlling for region and WineEnthusiast rating, wine type has a causal impact on price. The summary table aboves shows that certain types are, on average, $8 more expensive, as evidenced by both OLS and PSM scores being around this value (7.92 and 8.11 respectively). The low p-value of 0 also indicates that this effect is highly statistically significant.

### Does wine type cause differences in WineEnthusiast ratings (points)?
Ordinary Least Squares regression analysis suggests that there is a small positive causual relationship between wine type and rating, with certain types being rated about 0.18 points higher on average. These findings are backed by the small OLS p-value of 1.18x10^-29, suggesting that this efect is an extremely statistically significant and robust. However, the PSM score of -1.55 contradicts this; wines of the first type actually score about 1.55 points lower than matched wines of other types. This points towards the causal relationship being confounded, where the apparent effect of type on rating maybe due to price differences instead.

### Does a wine's continent of origin affect its price?
According to the regression analysis, the continent does not effect price to a great degree, with wines from certain regions only being around 24 cents more expensive on average. However, the large p-value of 0.17 means that these findings are not statistically significant. On the other hand, PSM shows that matching wines from certain continents may cause those wines to be around $9.64 more expensive on average when compared to similar wines of the same type and rating. The results are inconclusive, as regression illutrates there is no significant effect, but Propensity Score Matching suggests there might be one.

### Does a wine's continent of origin affect its WineEnthusiast rating?
Referring the summary table, OLS analysis shows a weak and insignifcant causal effect relationship between a wine's geographical origin and rating, as shown by the OLS effect and p-value of 0.002 and 0.905 respectively. Matching similar wines from certain continents also suggests that there is no meaningful effect when compared to that of wines in similar type and price; the PSM ATT value of -1.66 suggests that wines from one continent might score slightly lower, but this discrepancy is insignificant. It would appear that WineEnthusiast reviewers are more inclined to rate wines on its intrinsic qualities, rather than where they came from.

## Overall Conclusion
The findings generated from causal analysis techniques to assess how a wine's characteristics influence its price and ratings were somewhat mixed.
Controlling for external influencing variables, a wine's type was found to have a strong and statistically significant effect on its price, with certain types costing around $8 more on average.
On the other hand, a causal link between a wine's rating and type was less obvious, as the regression and matching results appeared to contradict each other, implying possible confounding.
A wine's continent of origin was shown to be an equally or less significant of an effect on its price and rating, indicating that a wine's geographical region of its own does not causally affect its perceived quality or price after account for its type and rating.


