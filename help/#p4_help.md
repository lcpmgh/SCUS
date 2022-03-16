#### Page 4: solve (solution of the question)

In this section, the classical frequency model is established and expressed as the following optimization problem:

$$
min\:f(P_s)\\
s.t.\quad \left\{\begin{matrix}0\leq P_s \leq 1, s=1,2,3,...,m\\\sum_{s=1}^{m}{P_s}=1\end{matrix}\right.\\\tag{1}
$$

and there are some optional forms of $f(P_s)$:

1. The sum of squares of the relative errors: $f(P_s)=\sum_{i=1}^{n}(\frac{C_i-\sum_{s=1}^{m}P_sS_{si}}{C_i})^2$ (Walling et al., 1999);
2. The residual sum of squares (RSS): $f(P_s)=\sum_{i=1}^{n}\{C_i-\sum_{s=1}^{m}P_sS_{si}\}^2$ (Gruszowski et al., 2003);
3. The sum of absolute of the relative errors: $f(P_s)=\sum_{i=1}^{n}|\frac{C_i-\sum_{s=1}^{m}P_sS_{si}}{C_i}|$ (Walling et al., 1993);
4. The root mean square error (RMSE): $f(P_s)=\sqrt{\frac{\sum_{i=1}^{n}\{C_i-\sum_{s=1}^{m}P_sS_{si}\}^2}{n}}$ (Motha et al., 2004);
5. The Landwehr model: $f(P_s)=\frac{1}{n}\sum_{i=1}^{n}\frac{|C_i-\sum_{s=1}^{m}P_sS_{si}|}{\sqrt{\sum_{s=1}^{m}P_s^2VAR_{si}}}$ (Devereux et al., 2010);
6. The modified Landwehr model: $f(P_s)=\frac{1}{n}\sum_{i=1}^{n}\frac{|C_i-\sum_{s=1}^{m}P_sS_{si}|}{\sqrt{\sum_{s=1}^{m}P_s^2\frac{VAR_{si}}{N_s}}}$  (Gellis et al., 2009);
7. The Collins model: $f(P_s)=\sum_{i=1}^{n}(\frac{C_i-\sum_{s=1}^{m}P_sS_{si}Z_sO_s}{C_i})^2W_i$ (Collins et al., 1997);
8. The modified Collins model: $f(P_s)=\sum_{i=1}^{n}(\frac{C_i-\sum_{s=1}^{m}P_sS_{si}Z_sO_sSV_{si}}{C_i})^2W_i$ (Collins et al., 2010).

where, 

+ $P_s$: the percentage contribution from source group $s$;
+ $C_i$: the mean concentration of fingerprint property $i$ in sediment sample;
+ $S_{si}$: the mean concentration of tracer property $i$ in source group $s$;
+ $m$: the number of sediment sources;
+ $n$: the number of fingerprints
+ $VAR_{si}$: the variance of a specific tracer concentration $i$ in the source group $s$;
+ $N_s$: the total number of samples in the source group $s$;
+ $Z_s$: the particle size correction factor for source group $s$; 
+ $O_s$: the organic matter content correction factor for source group $s$;
+ $W_i$: the discriminatory weight of tracer $i$;
+ $SV_{si}$: weighting representing the within-source variability of tracer property $i$ in source group $s$.  

For the optimization problem (1), this software provides two algorithms (Genetic Algorithms and Simulated Annealing). You can use the results of the previous statistical tests, or you can choose sources, targets, and tracers by yourself. Experiments show that standardizing data will change the distribution of optimal solutions in the feasible region, so it is not recommended to check the checkbox for data standardization (z-transformation).  Especially for models 1, 3, 7, or 8, for some synthetic data sets, due to the relative error calculation method adopted by these models, the error calculated with standardized data is likely to be infinite. 

##### Brief description of algorithm parameters:

+ Accuracy: the computational accuracy when finding the optimal solution (i.e. the number of decimal places);
+ Population size:  individual number of population, the larger the population, the easier it is to find the global optimal solution;
+ Maximum generation: maximum iterations;
+ Generation gap: the difference between the new generation and the previous generation. The smaller the difference, the more excellent individuals will be retained, and the larger the difference, the more new individuals will appear;
+ Crossover probability and Mutation probability: The greater the probability of crossover and mutation, the faster the search speed of the optimal solution, but the instability will also increase;
+ Temperature attenuation coefficient: Multiplier of temperature after each external iteration;
+ Initial temperature: The temperature at the beginning of the algorithm;
+ Maximum external iterations: External iteration means the decrease of temperature. When the temperature drops below the accuracy or reaches the maximum value, the iteration stops;
+ Maximum internal iterations: Internal iteration refers to the number of iterations at a certain temperature and stops when the limit is reached. The total number of iterations of the algorithm is equal to the number of external iterations multiplied by the number of internal iterations.

##### Brief description of results:

+ Algorithm performance 1: record the values of the optimal solution of each iteration. When the optimal solution is stable at the end of the iteration, it can be considered that the result is reliable;
+ Algorithm performance 2: when the model contains two or three sources, the line or raster of errors in the feasible region will be displayed, and the location of solutions will be marked to check whether the results are credible. In particular, it should be noted that for model 4 and model 5, since the contributions and variance are in the denominator, it means that the error result is easy to be infinite, especially when the variance of data is generally small. At this time,  performance 2 will become unrecognizable.
+ GOF: goodness of fit, $GOF=1-\frac{1}{n}\sum_{i=1}^{n}|\frac{C_i-\sum_{s=1}^{m}P_sS_{si}}{C_i}|$;
+ AIC: Akaike information criterion, $AIC=ln(\frac{RSS}{n})+\frac{2(m+1)}{n}$, where RSS is the sum of squared of residuals (i.e. the second type of $f(P_s)$);
+ SC: Schwarz criterion, $SC=ln(\frac{RSS}{n})+\frac{m}{n}ln(n)$;
+ Proportion: the contribution ratio of each source is shown in decimal form, i.e. the final solution of problem (1).

##### Reference

+ Walling, D. E., Owens, P. N., & Leeks, G. J. (1999). Fingerprinting suspended sediment sources in the catchment of the River Ouse, Yorkshire, UK. *Hydrological processes*, *13*(7), 955-975.

+ Gruszowski, K. E., Foster, I. D., Lees, J. A., & Charlesworth, S. M. (2003). Sediment sources and transport pathways in a rural catchment, Herefordshire, UK. *Hydrological Processes*, *17*(13), 2665-2681.

+ Walling, D. W., Woodward, J. C., & Nicholas, A. P. (1993). A multi-parameter approach to fingerprinting suspended-sediment sources. In *Tracers in hydrology. Proc. international symposium, Yokohama, 1993|* (pp. 329-338). International Association of Hydrological Sciences.
+ Motha, J. A., Wallbrink, P. J., Hairsine, P. B., & Grayson, R. B. (2004). Unsealed roads as suspended sediment sources in an agricultural catchment in south-eastern Australia. *Journal of Hydrology*, *286*(1-4), 1-18.
+ Devereux, O. H., Prestegaard, K. L., Needelman, B. A., & Gellis, A. C. (2010). Suspended‐sediment sources in an urban watershed, Northeast Branch Anacostia River, Maryland. *Hydrological Processes: An International Journal*, *24*(11), 1391-1403.
+ Gellis, A. C., Hupp, C. R., Pavich, M. J., Landwehr, J. M., Banks, W. S., Hubbard, B. E., ... & Reuter, J. M. (2009). Sources, Transport, and Storage of Sediment in the Chesapeake Bay Watershed: US Geological Survey Scientific Investigations Report 2008–5186. 2009. 95p.
+ Collins, A. L., Walling, D. E., & Leeks, G. J. (1997). Fingerprinting the origin of fluvial suspended sediment in larger river basins: combining assessment of spatial provenance and source type. *Geografiska Annaler: Series A, Physical Geography*, *79*(4), 239-254.
+ Collins, A. L., Walling, D. E., Webb, L., & King, P. (2010). Apportioning catchment scale sediment sources using a modified composite fingerprinting technique incorporating property weightings and prior information. *Geoderma*, *155*(3-4), 249-261.
