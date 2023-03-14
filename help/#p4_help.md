#### Part 4: Solve

This section presents the classical frequency model, which can be formulated as an optimization problem as follows:

$$
min\:f(P_s)\\
s.t.\quad \left\{\begin{matrix}0\leq P_s \leq 1, s=1,2,3,...,m\\\sum_{s=1}^{m}{P_s}=1\end{matrix}\right.
$$

Some optional forms of $f(P_s)$:

1. The sum of squared relative errors: $f(P_s)=\sum_{i=1}^{n}(\frac{C_i-\sum_{s=1}^{m}P_sS_{si}}{C_i})^2$ (Walling et al., 1999);
2. The residual sum of squares (RSS): $f(P_s)=\sum_{i=1}^{n}\{C_i-\sum_{s=1}^{m}P_sS_{si}\}^2$ (Gruszowski et al., 2003);
3. The absolute sum of the relative errors: $f(P_s)=\sum_{i=1}^{n}|\frac{C_i-\sum_{s=1}^{m}P_sS_{si}}{C_i}|$ (Walling et al., 1993);
4. The root mean square error (RMSE): $f(P_s)=\sqrt{\frac{\sum_{i=1}^{n}\{C_i-\sum_{s=1}^{m}P_sS_{si}\}^2}{n}}$ (Motha et al., 2004);
5. The Landwehr model: $f(P_s)=\frac{1}{n}\sum_{i=1}^{n}\frac{|C_i-\sum_{s=1}^{m}P_sS_{si}|}{\sqrt{\sum_{s=1}^{m}P_s^2VAR_{si}}}$ (Devereux et al., 2010);
6. The modified Landwehr model: $f(P_s)=\frac{1}{n}\sum_{i=1}^{n}\frac{|C_i-\sum_{s=1}^{m}P_sS_{si}|}{\sqrt{\sum_{s=1}^{m}P_s^2\frac{VAR_{si}}{N_s}}}$  (Gellis et al., 2009);
7. The Collins model: $f(P_s)=\sum_{i=1}^{n}(\frac{C_i-\sum_{s=1}^{m}P_sS_{si}Z_sO_s}{C_i})^2W_i$ (Collins et al., 1997);
8. The modified Collins model: $f(P_s)=\sum_{i=1}^{n}(\frac{C_i-\sum_{s=1}^{m}P_sS_{si}Z_sO_sSV_{si}}{C_i})^2W_i$ (Collins et al., 2010).

Their parameters mean: 

+ $P_s$: the percentage contribution from source group $s$;
+ $C_i$: the merged concentration of fingerprint property $i$ in sediment sample;
+ $S_{si}$: the merged concentration of tracer property $i$ in source group $s$;
+ $m$: the number of sediment sources;
+ $n$: the number of fingerprints;
+ $VAR_{si}$: the variance of a specific tracer concentration $i$ in the source group $s$;
+ $N_s$: the total number of samples in the source group $s$;
+ $Z_s$: the particle size correction factor for source group $s$; 
+ $O_s$: the organic matter content correction factor for source group $s$;
+ $W_i$: the discriminatory weight of tracer $i$;
+ $SV_{si}$: weighting representing the within-source variability of tracer property $i$ in source group $s$.  

SCUS offers two algorithms, **Genetic Algorithms** and **Simulated Annealing**, to solve this optimization problem. You can either utilize the findings of past statistical tests or select your own sources, targets, and tracers. However, experiments have revealed that standardizing data using z-transformation can alter the distribution of optimal solutions in the feasible region. Therefore, it is not advisable to use data standardization, particularly for models 1, 3, 7, or 8. In certain synthetic data sets, the relative error calculation method used by these models may lead to infinite errors when standardized data is applied.

##### Brief description of parameters:

+ Precision: refers to the level of computational accuracy achieved when finding the optimal solution, which is measured by the number of digits after the decimal point in the calculated function value;
+ Population size: how many individuals are in the population. A larger population can help find the best solution more easily;
+ Maximum generation: how many times the population can evolve;
+ Generation gap: how different the new population is from the old one. A smaller gap keeps more good individuals, while a larger gap creates more new individuals;
+  Crossover probability and Mutation probability: how likely it is that two individuals will combine or change their traits. A higher probability can speed up the search for the best solution, but also make it less stable;
+ Temperature attenuation coefficient: how much the temperature decreases after each cycle;
+ Initial temperature: the starting temperature of the algorithm;
+ Maximum external iterations: how many cycles of temperature decrease are allowed. The algorithm stops when the temperature is too low or the limit is reached;
+ Maximum internal iterations: how many times the algorithm can run at a fixed temperature. The algorithm stops when the limit is reached. The total number of times the algorithm runs is equal to the number of external iterations times the number of internal iterations.

##### Brief description of results:

+ Algorithm performance of plot 1:  keep track of the best solutions in each iteration. If the best solution does not change after many iterations, you can trust the result;
+ Algorithm performance of plot 2: show the error lines or grids in the feasible region when the model has two or three sources. Mark where the solutions are and see if they make sense. Be careful with model 4 and model 5, because the errors can become infinite when the contributions and variance are very small in the denominator. This can happen when the data has low variance. In this case, plot 2 is not useful.
+ GOF: goodness of fit (for the first one, also know as the mean absolute fit, MAF)
  + absolute: $GOFa=1-\frac{1}{n}\sum_{i=1}^{n}|\frac{C_i-\sum_{s=1}^{m}P_sS_{si}}{C_i}|$ (Laceby and Olley, 2015),
  + squared: $GOFs=1-\frac{1}{n}\sum_{i=1}^{n}(\frac{C_i-\sum_{s=1}^{m}P_sS_{si}}{C_i})^2$ (Collins et al., 2012);
+ AIC: Akaike information criterion, $AIC=ln(\frac{RSS}{n})+\frac{2(m+1)}{n}$, where RSS is the sum of squared of residuals (i.e. the second type of $f(P_s)$);
+ SC: Schwarz criterion, $SC=ln(\frac{RSS}{n})+\frac{m}{n}ln(n)$;
+ Proportion: shows how much each source contributes to the total in decimals and pie charts.

##### Reference

+ Walling, D. E., Owens, P. N., & Leeks, G. J. (1999). Fingerprinting suspended sediment sources in the catchment of the River Ouse, Yorkshire, UK. *Hydrological processes*, *13*(7), 955-975.

+ Gruszowski, K. E., Foster, I. D., Lees, J. A., & Charlesworth, S. M. (2003). Sediment sources and transport pathways in a rural catchment, Herefordshire, UK. *Hydrological Processes*, *17*(13), 2665-2681.

+ Walling, D. W., Woodward, J. C., & Nicholas, A. P. (1993). A multi-parameter approach to fingerprinting suspended-sediment sources. In *Tracers in hydrology. Proc. international symposium, Yokohama, 1993|* (pp. 329-338). International Association of Hydrological Sciences.
+ Motha, J. A., Wallbrink, P. J., Hairsine, P. B., & Grayson, R. B. (2004). Unsealed roads as suspended sediment sources in an agricultural catchment in south-eastern Australia. *Journal of Hydrology*, *286*(1-4), 1-18.
+ Devereux, O. H., Prestegaard, K. L., Needelman, B. A., & Gellis, A. C. (2010). Suspended‐sediment sources in an urban watershed, Northeast Branch Anacostia River, Maryland. *Hydrological Processes: An International Journal*, *24*(11), 1391-1403.
+ Gellis, A. C., Hupp, C. R., Pavich, M. J., Landwehr, J. M., Banks, W. S., Hubbard, B. E., ... & Reuter, J. M. (2009). Sources, Transport, and Storage of Sediment in the Chesapeake Bay Watershed: US Geological Survey Scientific Investigations Report 2008–5186. 2009. 95p.
+ Collins, A. L., Walling, D. E., & Leeks, G. J. (1997). Fingerprinting the origin of fluvial suspended sediment in larger river basins: combining assessment of spatial provenance and source type. *Geografiska Annaler: Series A, Physical Geography*, *79*(4), 239-254.
+ Collins, A. L., Walling, D. E., Webb, L., & King, P. (2010). Apportioning catchment scale sediment sources using a modified composite fingerprinting technique incorporating property weightings and prior information. *Geoderma*, *155*(3-4), 249-261.
+ Laceby, J. Patrick, and Jon Olley (2015). An examination of geochemical modelling approaches to tracing sediment sources incorporating distribution mixing and elemental correlations. *Hydrological processes,* 29.6 (2015): 1669-1685.
+ Collins, A. L., Zhang, Y., Walling, D. E., Grenfell, S. E., Smith, P., Grischeff, J., ... & Brogden, D. (2012). Quantifying fine‐grained sediment sources in the River Axe catchment, southwest England: application of a Monte Carlo numerical modelling framework incorporating local and genetic algorithm optimisation. Hydrological Processes, 26(13), 1962-1983.
