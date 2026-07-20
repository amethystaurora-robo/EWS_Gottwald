TODO:
add button to rare event algorithms
define better the stochastic model
add equations of stochastic model
add plots when they're finished (lineplots and instantons)
do the instanton and add equations
add instanton plots of stochastic model
fix ancestor degeneracy and add deterministic system transitions (only really need 2 I think), can also change the instantons to only 2
Could add a trajectory of the instanton on the 3D plot
Run spiking problem by Francesco
Transitions with different bifurcation parameters, and one more plot

## Introduction
The Atlantic Meridional Overturning Circulation (AMOC) is a large current in the Atlantic ocean's whose northward heat transport maintains a relatively mild climate compared to countries at similar latitudes. This climate sub-system also affects other systems, which provides motivation for research into mechanisms of its collapse.
Said collapse can be achieved by an influx of freshwater, reaching a tipping point through either rate-induced (R-tipping) or bifurcation-induced (B-tipping. Alternatively, the AMOC can collapse through random inputs such as wind stress, stochastic precipitation changes, atmospheric variability, or other system variability \cite{weijer2019stability, cini2024simulating}. This random input of variables is known as noise-induced (N-tipping), and, due to limits to its predictability \cite{mehling2024limits}, is an important topic of further research. N-tipping experiments are achieved through timescale separations between interacting climate sub-systems (such as the ocean and the atmosphere) where the slower system is forced to tip based on stochastic variability in the faster system \cite{lohmann2024melancholia}. One can imagine that, as an example, the atmosphere's timesteps are at a ratio of 1000:1 of the oceanic timescale. This means that as the atmosphere conducts cycles, the integrated effect of the atmosphere looks like a random variable in the ocean. In the case of the research on the Gottwald model, the faster atmosphere evolves on a timescale which approaches infinity. In practice, this chaotic variability has often been represented instead as additive white noise, $\frac{dT/dt} = f(T) + a(dW)$, where $dW$ is a Wiener process and $a$ is the amplitude of the additive noise. In the low-noise limit where $a < 1$ (check on this), random processes each have very low probabilities of occurring, so that the probability of stochastic processes occurring in sequence in the same direction decreases exponentially with number of events. For this reason, the probability of each path to collapse is an order of magnitude different from the next least unlikely path. It follows, therefore, that there is one path which is the least unlikely, and therefore the most likely to be approached in a noise-induced collapse. This path is known as the $instanton$, and as the system approaches the phase space of the instanton, it can be assumed that the system is headed towards collapse. 

Common early warning signals (EWS) of B-tipping and R-tipping such as the phenomenon known as $critical slowing down$, fail to predict noise-induced transitions, and currently the investigation of the instantonic trajectory is the only reliable method of developing EWS of these collapses. The instantonic trajectory has been shown to occur at the intersection of the unstable manifold in the base state and the stable manifold of the threshold state \cite{slyman2023rate}, meaning that it crosses the the unstable boundary between states known as the \textit{edge state}. Hence, both calculation of the instantonic trajectory and characterisation of the edge state are integral to research into EWS for noise-induced transitions. 

### Edge State
The edge state governs the geometry of two basin boundaries. In my research on the Atlantic Meridional Overturning Circulation (AMOC), this is the boundary between the AMOC $on$ state and its $off$ state. The edge state is reached through its stable manifold before being left through its unstable manifold towards either attractor. The characteristics of the edge state, in this case including the strength of the AMOC and its state variable values, can be an indication of tipping given that noise-induced transitions typically happen after approaching the edge state. The long-term aim of this research is to provide a threshold for tipping using the characterisation of the edge state and the calculation of the instantonic trajectory (below). 
### The Stochastic Gottwald Model
### Instanton
Following my previous work in (add a button for rare event algorithms), I am now validating the authenticity of my simulated instantonic trajectories by 1) confirming the path passes through the edge state by the use of an edge tracking algorithm fitted to the Gottwald model and 2) calculate the theoretical instanton of the Gottwald model.

Instead, the stochastic Gottwald model derives more accurate noise amplitudes and noise correlation based on $x, y$ and $z$'s dependence on $T$. (add equations). The correlations for each $T$ are defined by I(add correlation equation) and the slope of the line is approximated with a linear fit to ensure a solutions for an value of $T$. A covariance matrix is then created through tensor flow products (add this equation), where the system's state is affected by correlated additive and multiplicative noise. The computation of the instanton through the GMAM method (cite) can then be computed. 
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

For one last touch, I can look at the instanton and transitions with different values of the bifurcation parameter.

Now I also need to ensure that the spikes in the noise amplitude are ok. Those plots will also be here.



