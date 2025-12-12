How Economy Influences Democracy
================
by Fantastic Four (RB Raya, Keagan Ryan, Ian Del Rio Viera, Bravo Nie)

## Summary

This project deals with economy and regime. Specifically, we inquire on the relationship between countries’ economy and their regime. We ask how a country’s economy determines its regime measured in democracy and dictatorship continuum. We use regime and economic indicators collected from the Varieties of Democracy (V-Dem) dataset and World Development Indicators (WDI) dataset of the World Bank, respectively. V-Dem provides the five indices of democracies, while WDI provides economic indicator measured in GDP per capita.

(1) What is the relationship between democracy and economy? 
(2) What historically relevant events one notices that affect both the economy and regime?
(3) Can it be that the regime determines the economy?

Definitions of Democracy Indices

(1) Polyarchy, also known as electoral democracy, is the extent to which elections are free, fair, and inclusive, and whether key democratic institutions allow citizens to choose their leaders meaningfully.

(2) Liberal democracy, on the other hand, is the extent to which individual rights, rule of law, and constraints on executive power protect citizens from government abuse. It is also the most common conception of democracy in the West. 

(3) Deliberative democracy measures whether political decisions are made through reasoned, respectful, and common-good–oriented public deliberation rather than elite coercion or narrow interests.

(4) Participatory Democracy measures how much citizens can directly participate in political processes through civil society, local governance, and non-electoral channels.

(5) Lastly, egalitarian democracy measures the extent to which political power and influence are distributed equally across social groups, ensuring equal access to rights and resources.

These measures are the product of a series of questions answered by experts of about five in each country. These questions are then turned into indices using Bayesian aggregation. These measures are important in representing democracy as they capture the different and often debated definitions of democracy.

In the Democracy & Economy Overtime graph, it is clear to see the change in Democracy and GDP per capita over time. We can see that after the Third Wave of Democratization, which shifted from authoritarian regimes to democratic governments, there is an almost instant increase in democratization, shortly followed by a rise in GDP per capita. This data shows that once a country has become more democratic, its economy begins to increase shortly after.

The Evolution of Democracy & Economy maps show the GDP per capita and the World Liberal Democracy of the entire world in 2024. When comparing these maps side by side, we can see that in countries that are more democratic, we also see a better GDP per capita.  When you scan the QR codes, you can also see the change in GDP per Capita and World Liberal Democracy over time (1960 - 2024). In these changing maps, we can also see the same pattern as in 2024.

The Relationship Between Democracy & Economy plots show the bivariate relationship between the percentile of indices of democracy and GDP per capita. We can observe here a strong positive relationship between economy and democracy. Moreover, the concentration in the lower right of each plot shows what scholars call resource course, where because states have high amount of resources, they become less dependent on the people.

In future research methods, it would be very helpful to develop an analysis for causal inference. This would assist researchers in understanding the depth of GDP per capita around the world on specific regimes going beyond correlations and accounting for even more causal activity.

## Handout

Our handout can be found [here](handout/handout.pdf).

## Memo

A link to the code and how we created our graphics in our memo can be found [here](memo/memo.md).

## Data and Methods

In this project, we use Varieties of Democracy (V-Dem) dataset and World Development Indicators (WDI) dataset of the World Bank. Because of the size of V-Dem dataset, we had to merge both the dataset outside Posit. The following shows how we do this. We then rename variables in our main dataset df. 

We answer our research question using basic visualizations of correlations without considering covariates. To do this we use the following variables: `country`, `year`, `countryid`, `polyarchy`, `libdem`, `partipdem`, `delibdem`, `egaldem`, `gdp`, `gdppc`, `population`, `region`, `continent`, and `gini`.

Most of our analyses will include three main variables: `year`, the measures of democracy (`polyarchy`, `libdem`, `partipdem`, `delibdem`, `egaldem`), and measures of economic development (`gdppc`). 

To further illustrate this, we plan to use the following visualizations:

1. Time-series Plot - This will shows how the measures of democracy (`polyarchy`, `libdem`, `partipdem`, `delibdem`, `egaldem`) and measures of economic development (`gdppc` and `gini`) evolved through time. In the same visualization, we will also include lines that describe any particular events that explains the increase or drop of both measures. We can also facet this to show how the relationship differs (if at all) with respect to `region`.

2. Animated Maps - This is another way to show how the measures of democracy (`polyarchy`, `libdem`, `partipdem`, `delibdem`, `egaldem`) and measures of economic development (`gdppc` and `gini`) evolved through time while also considering the `country` in a map. 

3. Scatter Plot and Heatmaps- This plot is the most important of all. This finally shows the bivariate relationship between economic development and democracy. One way to show this is by transforming the x-axis to the percentile of countries' economic development and y-axis to the percentile of countries in terms of a measure of democracy. We will then facet them in terms of the measures of democracy (`polyarchy`, `libdem`, `partipdem`, `delibdem`, `egaldem`). This transformation is necessary, because as you will see below, the distribution of the economic indicator is highly skewed (although we may also use the log function).

Vdem dataset: Coppedge, Michael, John Gerring, Carl Henrik Knutsen, Staffan I. Lindberg, Jan Teorell, David Altman, Fabio Angiolillo, Michael Bernhard, Agnes Cornell, M. Steven Fish, Linnea Fox, Lisa Gastaldi, Haakon Gjerløw, Adam Glynn, Ana Good God, Sandra Grahn, Allen Hicken, Katrin Kinzelbach, Joshua Krusell, Kyle L. Marquardt, Kelly McMann, Valeriya Mechkova, Juraj Medzihorsky, Natalia Natsika, Anja Neundorf, Pamela Paxton, Daniel Pemstein, Johannes von Römer, Brigitte Seim, Rachel Sigman, Svend-Erik Skaaning, Jeffrey Staton, Aksel Sundström, Marcus Tannenberg, Eitan Tzelgov, Yi-ting Wang, Felix Wiebrecht, Tore Wig, Steven Wilson and Daniel Ziblatt. 2025. "V-Dem [Country-Year/Country-Date] Dataset v15" Varieties of Democracy (V-Dem) Project. <https://doi.org/10.23696/vdemds25>

WDI data: <https://databank.worldbank.org/source/world-development-indicators>

## Conclusions and Limitations

In this project, we ask whether economy has effects on democracy. We use two datasets involving robust democracy and economy measures. Our visualization suggests that economy heavily influences democracy. That is, as economy rise, so does democracy in aggregate level. This is a strong visualization in support of fundamental theories in comparative politics, including economic modernization theory. 

Although we find that economy influences democracy, the plots alone do not show the causal mechanism driving this influence. It may also be the case that democracy predicts economy as we show in `Plot 1`. One necessary method to establish such claims is to use econometric models; however, doing so would go beyond the project's scope. 

Nonetheless, this project shows the important role of economy in democratization or democracy in economic growth. 

## References

1. Vdem dataset: Coppedge, Michael, John Gerring, Carl Henrik Knutsen, Staffan I. Lindberg, Jan Teorell, David Altman, Fabio Angiolillo, Michael Bernhard, Agnes Cornell, M. Steven Fish, Linnea Fox, Lisa Gastaldi, Haakon Gjerløw, Adam Glynn, Ana Good God, Sandra Grahn, Allen Hicken, Katrin Kinzelbach, Joshua Krusell, Kyle L. Marquardt, Kelly McMann, Valeriya Mechkova, Juraj Medzihorsky, Natalia Natsika, Anja Neundorf, Pamela Paxton, Daniel Pemstein, Johannes von Römer, Brigitte Seim, Rachel Sigman, Svend-Erik Skaaning, Jeffrey Staton, Aksel Sundström, Marcus Tannenberg, Eitan Tzelgov, Yi-ting Wang, Felix Wiebrecht, Tore Wig, Steven Wilson and Daniel Ziblatt. 2025. "V-Dem [Country-Year/Country-Date] Dataset v15" Varieties of Democracy (V-Dem) Project

2.  World Bank. 2024. World Development Indicators. Washington, DC: World Bank.
