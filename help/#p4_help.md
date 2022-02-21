Page 4: solve (solution of the question)

In this section, the classical frequency model is established and expressed as the following optimization problem:

$$
min\:f(P_s)\\
s.t.\quad \left\{\begin{matrix}0\leq P_s \leq 1, s=1,2,3,...,m\\\sum_{s=1}^{m}{P_s}=1\end{matrix}\right.\\\tag{1}
$$

and there are four optional forms for $f(P_s)$:

1. the sum of squared of relative residuals: $f(P_s)=\sum_{i=1}^{n}(\frac{C_i-\sum_{s=1}^{m}P_sS_{si}}{C_i})^2$;

2. the sum of squared of residuals: $f(P_s)=\sum_{i=1}^{n}\{C_i-\sum_{s=1}^{m}P_sS_{si}\}^2$;

3. the sum of absolute of relative residuals: $f(P_s)=\sum_{i=1}^{n}|\frac{C_i-\sum_{s=1}^{m}P_sS_{si}}{C_i}|$;

4. the sum of absolute residuals: $f(P_s)=\sum_{i=1}^{n}|C_i-\sum_{s=1}^{m}P_sS_{si}|$;

where, 

+ $P_s$: the percentage contribution from source category $s$;
+ $C_i$: the mean concentration of fingerprint property $i$ in sediment sample;
+ $S_{si}$: the mean concentration of tracer property $i$ in source group $s$;
+ $m$: the number of sediment sources;
+ $n$: the number of fingerprints.

For the optimization problem (1), this software provides two algorithms (Genetic Algorithms and Simulated Annealing). You can use the results of the previous statistical tests, or you can choose sources, targets, and tracers by yourself. Due to the characteristics of the two algorithms,  it is recommended to check the checkbox for data standardization (z-transformation) when the values of different tracers in the data are quite different. 

Brief description of algorithm parameters:

+ Accuracy: the computational accuracy when finding the optimal solution (i.e. the number of decimal places);
+ Population size:  individual number of population, the larger the population, the easier it is to find the global optimal solution;
+ Maximum generation: maximum iterations;
+ Generation gap: the difference between the new generation and the previous generation. The smaller the difference, the more excellent individuals will be retained, and the larger the difference, the more new individuals will appear;
+ Crossover probability and Mutation probability: The greater the probability of crossover and mutation, the faster the search speed of the optimal solution, but the instability will also increase;
+ Temperature attenuation coefficient: Multiplier of temperature after each external iteration;
+ Initial temperature: The temperature at the beginning of the algorithm;
+ Maximum external iterations: External iteration means the decrease of temperature. When the temperature drops below the accuracy or reaches the maximum value, the iteration stops;
+ Maximum internal iterations: Internal iteration refers to the number of iterations at a certain temperature and stops when the limit is reached. The total number of iterations of the algorithm is equal to the number of external iterations multiplied by the number of internal iterations.

Brief description of the results:

+ Algorithm performance: record the values of the optimal solution of each iteration. When the optimal solution is stable at the end of the iteration, it can be considered that the result is reliable;

+ GOF: goodness of fit, $GOF=1-\frac{1}{n}\sum_{i=1}^{n}|\frac{C_i-\sum_{s=1}^{m}P_sS_{si}}{C_i}|$;
+ AIC: Akaike information criterion, $AIC=ln(\frac{SSR}{n})+\frac{2(m+1)}{n}$, where SSR is the sum of squared of residuals (i.e. the second type of $f(P_s)$);
+ SC: Schwarz criterion, $SC=ln(\frac{SSR}{n})+\frac{m}{n}ln(n)$;
+ Proportion: the contribution ratio of each source is shown in decimal form, i.e. the final solution of problem (1).
