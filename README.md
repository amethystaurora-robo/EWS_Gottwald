## Introduction
### Edge State
The edge state governs the geometry of two basin boundaries. In my research on the Atlantic Meridional Overturning Circulation (AMOC), this is the boundary between the AMOC $on$ state and its $off$ state. The edge state is reached through its stable manifold before being left through its unstable manifold towards either attractor. The characteristics of the edge state, in this case including the strength of the AMOC and its state variable values, can be an indication of tipping given that noise-induced transitions typically happen after approaching the edge state. The long-term aim of this research is to provide a threshold for tipping using the characterisation of the edge state and the calculation of the instantonic trajectory (below). 
### The Stochastic Gottwald Model
### Instanton
Following my previous work in (add a button for rare event algorithms), I am now validating the authenticity of my simulated instantonic trajectories by 1) confirming the path passes through the edge state by the use of an edge tracking algorithm fitted to the Gottwald model and 2) calculate the theoretical instanton of the Gottwald model.
## Methods
### Edge State
The dynamical system, in this case the Gottwald model, is initialized with two initial states, $u1$ and $u2$ that lie in different basins (on and off). The forward trajectories are computed for each attractor to create attractor representations and their means. States are classified by basin membership. A bisection method is used to bisect the straight line in phase space between $u1$ and $u2$ until two states on opposite sides of the basin boundary are found within a tolerance threshold of $1e-9$. The midpoint is taken as the initial edge state. This is done in interations until their separation falls below the tolerance threshold.
### Stochastic Transitions
The previous work used a killing and cloning rare event algorithm to bias trajectories towards collapse. Noise was introduced to separate trajectories after cloning, which allowed for noise-induced transitions from the AMOC $on$ state to its $off$ state. This was Guassian white noise, which was added to the differential equations of either $T$ or $S$ at each resampling period, to allow differentiation of trajectories after cloning. 
In the Gottwald model, the chaotic atmosphere is meant to instead act as noise on the slow ocean, which is achieved through a separation of timescales between the ocean and atmosphere. The atmosphere consists of state variables $x$, $y$, and $z$, which (add what they mean) in the real system would be correlated with each other. Therefore, correlated additive and multiplicative (CAM) noise has been introduced in the stochastic model as below:

Add equations here

where a covariance matrix was computed to represent the nosiy atmosphere's effect on the ocean. The stochastic model was then computed from this matrix, and the transitions from this model was used to calculate the instanton, as below:

Add the dynamics.jl equations here.


## Conclusion

Below the bisection method of determining the edge state results in a convergence in the phase space of state variables $T$ and $S$. The values of the state variables are as below:
T_mean ± std = 0.682514 ± 0.00041549123
S_mean ± std = 0.6146085 ± 0.00011937455
T_median = 0.6824541, S_median = 0.6145892

The trajectory of the bisection method is shown below, where $T$ and $S$ converge quickly to the basin boundary.
<p>
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/edge_state_TS.png" width="400">
</p>

Values of $T$ and $S$ in the edge state are cut after convergence, the threshold $0.5$, and overlaid on the simulated instantonic trajectories found in (add button here). For each transition shown below, the instantonic trajectory is mapped. The point of transition is shown as a blue line, passing through the edge state, a slate black plot overlaid on the instanton. 

<p>
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/edge_instanton_salinity_2007000.png" width="400">
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/edge_instanton_salinity_2008000.png" width="400">
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/edge_instanton_salinity_2009000.png" width="400">
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/edge_instanton_salinity_10007000.png" width="400">
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/edge_instanton_salinity_10008000.png" width="400">
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/edge_instanton_salinity_10009000.png" width="400">
</p>

The same has been done for trajectories simulated with the rare event algorithm applied to the AMOC, with results as below.
<p>
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/edge_instanton_amoc_200-500.png" width="400">
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/edge_instanton_amoc_200-1000.png" width="400">
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/edge_instanton_amoc_200-2000.png" width="400">
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/edge_instanton_amoc_1000-500.png" width="400">
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/edge_instanton_amoc_1000-1000.png" width="400">
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/edge_instanton_amoc_1000-2000.png" width="400">
</p>

For a given starting temperature (t0), runs a transient until the fast variables reach their attractor, then uses separation of 
time-scales to allow fast, chaotic atmosphere to run while the slow ocean is essentially stationary. The integral of the fast
atmosphere is used to act like noise on the slower system. We observe the variance of T and S due to noise, and confirm that
it can be approximated with white noise given that the approximately random forcing from the atmosphere leads to, on average
a continuous spread of trajectories over time, shown in the plots as an approximately straight line from 0 to 1.  

I have checked that the instantonic trajectory also passes through the edge state in the phase space of x, y, and z.

<p>
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/3D_edge.png" width="400">
</p>

I have also figured out a solution for ancestor degeneracy in rare event algorithms, so that will be another big step. Finally, this repo will contain new code with the system using the atmosphere as added correlated noise, rather than the white noise we have been using (and compare the statistics to the actual output), in order to apply the stochastic system to compute the instanton, with comparisons between the calculated instanton and the empirical instanton. For one last touch, I can look at the instanton and transitions with different values of the bifurcation parameter.

Now I also need to ensure that the spikes in the noise amplitude are ok. Those plots will also be here.



