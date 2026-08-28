Narrative:
2. We start by modelling the collapse of the AMOC. This is achieved in a simple model through the use of a rare event algorithm.
3. We illustrate the path to collapse in the deterministic model. Keep in mind that this is a deterministic model with added white noise, so the path modelled may not necessarily be the instanton.
4. We homogenize the system, incorporating the noise as a covariance matrix, which allows more accurate simulation of noisy dynamics, by? understand this part better, then calculate the instantonic trajectory with the stochastic model. This shows good agreement with our research so far.
5. We analyse the probabilities of collapse by re-weighting the trajectories, giving ?
6. In practice, the system may be at different points on the on arm of the bifurcation, so it may be anywhere near the bifurcation point. We vary the freshwater flux to illustrate how the deterministic instanton, stochastic instanton, determinstic paths, and probabilities change as the control parameter is adjusted.
7. Given that the calculated instanton path shows good agreement with the deterministic one, this provides a good case to say that the RE algorithm is selecting the instanton path. We compare our findings to a higher-order model, where the instanton cannot be calculated explicitly.


## Introduction
The Atlantic Meridional Overturning Circulation (AMOC) is a large current in the Atlantic ocean's whose northward heat transport maintains a relatively mild climate compared to countries at similar latitudes. This climate sub-system also affects other systems, which provides motivation for research into mechanisms of its collapse.
Said collapse can be achieved by an influx of freshwater, reaching a tipping point through either rate-induced (R-tipping) or bifurcation-induced (B-tipping. Alternatively, the AMOC can collapse through random inputs such as wind stress, stochastic precipitation changes, atmospheric variability, or other system variability. This random input of variables is known as noise-induced (N-tipping), and, due to limits to its predictability, is an important topic of further research. N-tipping experiments are achieved through timescale separations between interacting climate sub-systems (such as the ocean and the atmosphere) where the slower system is forced to tip based on stochastic variability in the faster system. One can imagine that, as an example, the atmosphere's timesteps are at a ratio of 1000:1 of the oceanic timescale. This means that as the atmosphere conducts cycles, the integrated effect of the atmosphere looks like a random variable in the ocean. In the case of the research on the Gottwald model, the faster atmosphere evolves on a timescale which approaches infinity. In practice, this chaotic variability has often been represented instead as additive white noise, $\frac{dT/dt} = f(T) + a(dW)$, where $dW$ is a Wiener process and $a$ is the amplitude of the additive noise. In the low-noise limit where $a < 1$, random processes each have very low probabilities of occurring, so that the probability of stochastic processes occurring in sequence in the same direction decreases exponentially with number of events. For this reason, the probability of each path to collapse is an order of magnitude different from the next least unlikely path. It follows, therefore, that there is one path which is the least unlikely, and therefore the most likely to be approached in a noise-induced collapse. This path is known as the $instanton$, and as the system approaches the phase space of the instanton, it can be assumed that the system is headed towards collapse. 

Common early warning signals (EWS) of B-tipping and R-tipping such as the phenomenon known as $critical slowing down$, fail to predict noise-induced transitions, and currently the investigation of the instantonic trajectory is the only reliable method of developing EWS of these collapses. The instantonic trajectory has been shown to occur at the intersection of the unstable manifold in the base state and the stable manifold of the threshold state, meaning that it crosses the the unstable boundary between states known as the \textit{edge state}. Hence, both calculation of the instantonic trajectory and characterisation of the edge state are integral to research into EWS for noise-induced transitions. 

### Edge State
The edge state governs the geometry of two basin boundaries. In my research on the AMOC, this is the boundary between the AMOC $on$ state and its $off$ state. The edge state is reached through its stable manifold before being left through its unstable manifold towards either attractor. The characteristics of the edge state, in this case including the strength of the AMOC and its state variable values, can be an indication of tipping given that noise-induced transitions typically happen after approaching the edge state. The long-term aim of this research is to provide a threshold for tipping using the characterisation of the edge state and the calculation of the instantonic trajectory (below). 

### Rare Event Algorithms

### The Stochastic Gottwald Model

#### Instanton

Following my research below, 

<p align="left">
  <a href="https://github.com/amethystaurora-robo/Rare_event_algorithms" target="_blank">
    <img src="https://img.shields.io/badge/%20Transitions-2b6750?style=for-the-badge&logo=github&logoColor=white"/>
  </a>
</p>
 I am now validating the authenticity of my simulated instantonic trajectories by 1) confirming the path passes through the edge state by the use of an edge tracking algorithm fitted to the Gottwald model and 2) calculate the theoretical instanton of the Gottwald model.

Instead, the stochastic Gottwald model derives more accurate noise amplitudes and noise correlation based on $x, y$ and $z$'s dependence on $T$. (add equations). The timescale separation of atmospheric and oceanic conditions allows the integrated chaotic atmosphere to act as noise as it approaches infinity (add this as an equation). The correlations for each $T$ are defined by I(add correlation equation) and the slope of the line is approximated with a linear fit to ensure a solutions for an value of $T$. A covariance matrix is then created through tensor flow products (add this equation), where the system's state is affected by correlated additive and multiplicative noise. The computation of the instanton through the GMAM method (cite) can then be computed. 
## Methods
### Edge State
The dynamical system, in this case the Gottwald model, is initialized with two initial states, $u1$ and $u2$ that lie in different basins (on and off). The forward trajectories are computed for each attractor to create attractor representations and their means. States are classified by basin membership. A bisection method is used to bisect the straight line in phase space between $u1$ and $u2$ until two states on opposite sides of the basin boundary are found within a tolerance threshold of $1e-9$. The midpoint is taken as the initial edge state. This is done in interations until their separation falls below the tolerance threshold.
### Stochastic Transitions
The previous work used a killing and cloning rare event algorithm to bias trajectories towards collapse. Noise was introduced to separate trajectories after cloning, which allowed for noise-induced transitions from the AMOC $on$ state to its $off$ state. This was Guassian white noise, which was added to the differential equations of either $T$ or $S$ at each resampling period, to allow differentiation of trajectories after cloning. 
In the Gottwald model, the chaotic atmosphere is meant to instead act as noise on the slow ocean, which is achieved through a separation of timescales between the ocean and atmosphere. The atmosphere consists of state variables $x$, $y$, and $z$, which (add what they mean) in the real system would be correlated with each other. Therefore, correlated additive and multiplicative (CAM) noise has been introduced in the stochastic model as below:

Add equations here

a ̃ = a(X) , σ(X)σ(X)T =  ∫∞  0  dt  ∫  dμX(x) (b(x) ⊗ b(x(t)) + b(x(t)) ⊗ b(x)) , (B.3)

where a covariance matrix was computed to represent the nosiy atmosphere's effect on the ocean. The stochastic model was then computed from this matrix, and the transitions from this model was used to calculate the instanton, as below:

Add the dynamics.jl equations here.


## Conclusion

Below the collapses in the deterministic model are shown, where the rare event algorithm has been applied to the AMOC and to salinity respectively. Applying it to temperature did not result in any collapse.

<p>
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/ancestors_fixed_amoc.png" width="400">
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/ancestors_fixed_salinity.png" width="400">
</p>

After re-weighting the trajectories to determine their probability under normal dynamics, the expectation for the ensemble is 0.04%, where 4/10,000 trajectories are expected to collapse.

Next, I will run the stochastic model with 100,000 trajectories to confirm if this is the case.

Below the bisection method of determining the edge state results in a convergence in the phase space of state variables $T$ and $S$. The values of the state variables are as below:
T_mean ± std = 0.682514 ± 0.00041549123
S_mean ± std = 0.6146085 ± 0.00011937455
T_median = 0.6824541, S_median = 0.6145892

The trajectory of the bisection method is shown below, where $T$ and $S$ converge quickly to the basin boundary.
<p>
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/edge_state_TS.png" width="400">
</p>

Values of $T$ and $S$ in the edge state are cut after convergence, the threshold $0.5$, and overlaid on the determinstic paths to collapse.
<p>
  <img src="https://github.com/amethystaurora-robo/EWS_GOTTwald/blob/main/figures/edge_instanton_amoc_200-2000.png" width="400">
  <img src="https://github.com/amethystaurora-robo/EWS_GOTTwald/blob/main/figures/edge_instanton_salinity_2007000.png" width="400">
</p>

The determinstic instanton was plotted with T vs S, and then after homogenization, the stochastic model was used to calculate and confirm the path of the true instanton, where Freidlin-Wentzell action is minimized.

The same has been done for trajectories simulated with the rare event algorithm applied to the AMOC, with results as below. The instanton path which has been calculated through the geometric minimum action method (gMAM), shows very good compatibility with the deterministic trajectory found using the rare event algorithm. This gives a promising indicator that the rare event algorithm may be finding the instantonic trajectory, and can be used to estimate the instanton in higher-order models where it cannot be calculated directly.

<p>
  <img src="https://github.com/amethystaurora-robo/EWS_GOTTwald/blob/main/figures/instanton_path.png" width="400">
</p>

For a given starting temperature (t0), runs a transient until the fast variables reach their attractor, then uses separation of 
time-scales to allow fast, chaotic atmosphere to run while the slow ocean is essentially stationary. The integral of the fast
atmosphere is used to act like noise on the slower system. We observe the variance of T and S due to noise, and confirm that
it can be approximated with white noise given that the approximately random forcing from the atmosphere leads to, on average
a continuous spread of trajectories over time, shown in the plots as an approximately straight line from 0 to 1.  

I have checked that the instantonic trajectory also passes through the edge state in the phase space of x, y, and z.

<p>
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/3D_edge.png" width="400">
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/3D_edge_inst_det.png" width="400">
</p>

In the real climate system, noise is not separate from other types of system collapse, especially R-tipping, which is controlled by freshwater flux. Hence, below I have adjusted the freshwater flux parameter for values closer to the tipping point, resulting in changes in the deterministic transition paths, the shape of both determinstic and stochastic instanton paths.

<p>
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/sigma_varied_timeseries_amoc.png" width="400">
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/sigma_varied_timeseries_salinity.png" width="400">
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/paths_sigma_back_stochastic.png" width="400">
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/paths_sigma_towards_stochastic.png" width="400">
</p>

The results are promising, demonstrating how the rare event algorithm may select the optimal transition path. This is particularly useful in higher order climate models, where the instanton is not feasible to compute. 

Below, I again run deterministic trajectories in the model of intermediate complexity PlaSim-LSG, where three variables have been selected for direct comparison with the Gottwald model. These are:

• The meridional salinity gradient (SG) in the Atlantic, measured as the mean salinity difference between 0-20 N
and 40-80 N in the top 1000 m (omitting the top 100 m),
• The vertical SG in the North Atlantic, defined as the mean salinity difference between the depths 100-1000 m
and 1000-3000 m at 46-66◦N,
• The deep North Atlantic salinity anomaly, defined as the mean salinity anomaly relative to 35 g kg−1
in the
Atlantic basin north of 50◦N and below 1000 m depth.






