## Abstract
The Atlantic Meridional Overturning Circulation (AMOC) is the Atlantic ocean's largest current. Its northward heat transport allows for a relatively mild climate in Europe. Categorised as a tipping element, there is currently growing concern that an AMOC collapse could alter the climate state in the Northern Hemisphere by increasing sea ice and reducing average temperatures. This can affect other climate sub-systems, the global economy and food production. Of particular concern is the possibility of a stochastic collapse, or noise-induced transition, where a sudden regime shift could occur without the typical markers of a slowing of the system. Investigations of stochastic collapses use advanced mathematical models to simulate AMOC flow. However, due to the very low probability of a spontaneous noise-induced collapse, simulations are run with an algorithm used to increase the sample size of collapse events. The structure of the algorithm is such that it may be automatically selecting the most likely path to collapse. We can use this information to find an indication that collapse is about to occur, or an early warning signal. We hereby submit evidence of our hypothesis through a demonstration of transition state dynamics where the path flows through particular points in phase space on its journey compared to a calculation of the lowest energy path in the same phasse space. We compare our findings to a higher-order model with similarly convincing results. We further demonstrate the difficulty of returning to a pre-collapse state once a transition has occurred, through a demonstration of steady state dynamics as freshwater in the Atlantic basin is varied. The extremes in temperature and salinity that we demonstrate as required for a return to normalcy provide a compelling reason to develop early warnings of collapse befor the collapse has occurred. 

## Introduction
### The AMOC as a Tipping Element
The Atlantic Meridional Overturning Circulation (AMOC) is the Atlantic's largest ocean current. It transports heat, salt, and nutrients northward in contrast to the Pacific and Indian ocean's southward transport, keeping the European climate mild compared to land masses at equal latitudes \cite{frajka2019atlantic, weijer2019stability, rahmstorf1996freshwater, hu2012pacific}. The circulation is begun in the North Atlantic, where salty water from the tropics cools, increases in density and sinks to form North Atlantic Deep Water (NADW). This anomalously dense water seeks equilibrium through southward flow, until westerly winds, ekman transport, and evaporation bring it to the surface to start the process again \cite{gordon2001interocean}. Disruptions to the AMOC's delicate cirulation therefore take the form of changes in temperature, salinity, wind, and freshwater influx. Extreme disruptions collapse the circulation: a $tipping point$ \cite{weijer2019stability,mecking2017effect,jackson2017ocean,buizert2015southern}. 

It is helpful to envision tipping by assuming the AMOC is a theoretical system with two variables: freshwater flux, $\sigma_0$, and AMOC strength, $\Psi$. In the \textit{bifurcation} diagram in Figure~\ref{bifurcation_diagram}, the two states of the bi-stable AMOC are demonstrated. As the control parameter is varied, the system moves along the bifurcation branch until collapsing from its AMOC on state, passing through the unstable edge state, and falling into the AMOC off state. This method of tipping is known as \textit{bifurcation-induced (B-tipping)}, but the AMOC can also tip suddenly through internal system variability, known as \textit{noise-induced (N-tipping).}

### Early Warning Signals
While our research requires models to cross tipping thresholds, a major goal of tipping point science is naturally the prevention of these negative outcomes. The first step to preventative measures is developing reliable \textit{Early Warning Signals (EWS)} of collapse. Much of the research into EWS thus far has focused on 'hosing' experiments, which collapse the AMOC through enormous influxes of freshwater in B-tipping scenarios \cite{jackson2023understanding,ma2024revisiting,mecking2016stable}. Relatively robust EWS, particularly the phenomenon known as \textit{critical slowing down} \cite{lenton2012early,} have emerged as a result of these studies, which change the stability landscape pictured in Figure~\ref{bifurcation_diagram}. Much of the recent body of research now focuses on B-tipping events in concert with noise \cite{garain2022stochastic,morr2024detection}. However, these experiments don't account for tipping driven purely by noise, which can occur anywhere along the bifurcation branch, does not change the potential landscape of the system, and may not exhibit critical slowing down \cite{liu2015identifying, ma2019predicting}. Fortunately, there are many promising avenues of exploration for EWS of N-tipping.

We first look at the investigation of the dynamics of the edge state: the unstable basin boundary between on and off attractors, the 'gateway' of transitions \cite{borner2026global}. As an unstable state, it is very sensitive to external perturbations and systems therein can either cross the critical threshold or fall back into the stable on state \cite{liu2015identifying}. While this conjures a notion of a short-lived and chaotic period of system instability, the slow timescale of the ocean provides for a long-lived transient within the edge boundary \cite{borner2026global}, allowing indications of the edge state and distance thereto to serve as EWS. 

The edge state is explicitly calculated in one lower-order and one higher-order model using a bisection and tracking method described in Section II. On this boundary, variables have been identified which reflect dynamics of neither the on or off state, termed \textit{excursive markers} \cite{moinat2026climate,borner2026global,lohmann2024melancholia,lohmann2026predicting,liu2015identifying}. Here, we use the dynamic properties of the edge state to confirm our hypothesis that the path selected by the rare event algorithm may be correctly leading to the edge state. 

Along the same lines, an even earlier EWS predicts the path leading to the edge state, the \textit{instanton}. In a similar way to excursive markers, quantification of the instanton can lead to the description of \textit{jump conditions}, markers of the approach to instanton phase space \cite{giorgini2020precursors}. Edge state dynamics tie into instanton dynamics, because the instanton evolves towards the edge state \cite{lohmann2025role}, reaching an intersection between stable and unstable manifolds \cite{slyman2023rate}. Identifying properties of the edge state and instanton are the first step in building climate networks \cite{moinat2026climate,moinat2026spatial}, detecting system instability \cite{moinat2026climate,ma2019predicting}, defining distances using spatial signatures \cite{moinat2026spatial}, and calculating escape probabilities \cite{ma2022early,chapman2025quantifying} for a full early warning system.

This paper is organised as follows: Section 4 begins with a simple low-order chaotic model. We collapse the AMOC within the system by using our biasing rare event algorithm. We then calculate the edge state for the system, and compare our deterministic collapse trajectory to the edge state phase space. Next, we take our deterministic model and homogenize the chaotic atmosphere component to become a fully stochastic system capable of spontaneous collapse. We use the stochastic system to calculate the instanton, and compare that with our deterministic collapse paths. We then compare the collapse paths against the edge state for varied freshwater forcing scenarios, and find the probability of each. Then we map the path from the off state back to the off state for the same scenarios. Finally, we compare our findings to a higher-order model, looking at edge state dynamics and hypothesising the instanton path for the higher order model.

### Rare Event Algorithms
The first step in our research is obtaining a model which is bi-stable, and capable
of crossing tipping thresholds through internal system variability. Noise-induced
transitions are achieved through timescale separations between interacting cli-
mate sub-systems where the slower system reaches a critical threshold based on
stochastic variability in the faster system [33]. For the AMOC, this takes the
form of a coupled system with a slow ocean and a fast, chaotic atmosphere. Be-
cause the input from the atmosphere is random, the probability of it exerting the
right amount of forcing to be a tipping pressure is very low. Extensive time and
computational power would be required to observe even one of these stochas-
tic transitions. A faster and less computationally intense method of observing
these collapses is a rare event algorithm. The algorithm iteratively clones tra-
jectories headed towards collapse and kills the others, succeeding in creating a
distribution of trajectories which are dominated by tipping behaviour.
Although cloning and killing rare event algorithms and their theory have
existed at least since the early 2000s, they were not applied to climate modelling
until 2021 in studying extreme heatwaves [40]. Since then, rare event algorithms
have been adapted for other climate sub-systems [41–43]. In [43], use of the rare
event algorithm was successful in causing an internally driven AMOC collapse
in the intermediate-complexity model PLASIM-LSG.
Due to collapse events in the AMOC being very rare in models, a need arises for an algorithm which oversamples tails of the distribution of state variables in the AMOC under normal dynamics, to provide an ensemble of collapsed trajectories. This is achieved through a rare event algorithm, which assigns weights to each trajectory in an ensemble at regular resampling intervals, cloning those with higher weights proportional to their weight and killing trajectories with weights near zero. An illustration of the rare event algorithm is shown below, where the ensemble can be seen moving from its normal dynamics to the rare event of interest.

<p>
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/rareevent.jpg" width="400">
</p>

After the rare event algorithm is applied, the peak of the distribution of trajectories shifts from normally distributed dynamics to a peak in the tail, making rare events common. The trajectories can then be re-weighted to determine their probability of collapse under normal dynamics.

<p>
  <img src="https://github.com/amethystaurora-robo/EWS_Gottwald/blob/main/figures/importance_sampling.png" width="400">
</p>

### The Stochastic Gottwald Model

Noise-induced transitions are simulated using models that may be either deterministic or stochastic. The first part of this paper looks at the deterministic collapse of the AMOC, using the rare event algorithm to force the system towards collapse, and adding white noise at each resampling period. In a more realistic system, the noise should be spatially correlated, where the atmospheric variables co-vary according to atmospheric dynamics. The integrated effect of these variables can be integrated into the oceanic system, allowing for spontaneous noise-induced transitions in an ocean-only stochastic model. 

The advantage of this model is that its correlated multiplicative noise can be used to calculate the instantonic trajectory, and compare the calculated instanton with the deterministic path to collapse. 

#### Instanton

Following my research below, 

<p align="left">
  <a href="https://github.com/amethystaurora-robo/Rare_event_algorithms" target="_blank">
    <img src="https://img.shields.io/badge/%20Transitions-2b6750?style=for-the-badge&logo=github&logoColor=white"/>
  </a>
</p>
 I am now validating the authenticity of my simulated instantonic trajectories by 
 $\begin{enumerate}
 \item confirming the path passes through the edge state by the use of an edge tracking algorithm fitted to the Gottwald model 
 \item calculating the theoretical instanton of the Gottwald model.
 \end{enumerate}$

Instead, the stochastic Gottwald model derives more accurate noise amplitudes and noise correlation based on $x, y$ and $z$'s dependence on $T$, as shown in the equations below.

$

The timescale separation of atmospheric and oceanic conditions allows the integrated chaotic atmosphere to act as noise as it approaches infinity (add this as an equation). The correlations for each $T$ are defined by I(add correlation equation) and the slope of the line is approximated with a linear fit to ensure a solutions for an value of $T$. A covariance matrix is then created through tensor flow products (add this equation), where the system's state is affected by correlated additive and multiplicative noise. The computation of the instanton through the GMAM method (cite) can then be computed. 
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






