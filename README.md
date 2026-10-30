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

\section{Methods}


\subsection{A Low-Order Chaotic Model: The Gottwald Model}

The Gottwald model couples the well-known Lorenz84 \cite{lorenz1984irregularity} atmospheric model and Stommel 2-box oceanic models \cite{stommel1961thermohaline} to create a fast-slow system where atmospheric and oceanic properties are exchanged in a two-way coupling \cite{gottwald2021model, oh2025noise}. 

The Lorenz-84 model of the atmosphere defines a simplified Hadley circulation with three ordinary differential equations \cite{lorenz1984irregularity}:

\begin{align}
\dot{x} &= -(y^2 + z^2) - a(x - F) \\
\dot{y} &= xy - bxz - (y - G) \\
\dot{z} &= bxy - xz - z
\end{align}

where $x$ represents intensity of westerlies as well as the poleward temperature gradient, and $y$ and $z$ are the cosine and sine phases of large-scale eddies, respectively. The coefficients $a$ and $b$ control displacement and damping of the westerly current compared to the eddies, and $F$ and $G$ are relaxation terms for $x$ and $y$ in an uncoupled model. \cite{lorenz1984irregularity}. 

The conceptual 2-box Stommel oceanic model assumes the ocean is split into two boxes, polar and equatorial, with temperature, $(T_e, T_p)$ and salinity, $(S_e, S_p)$. Gradients represent the strength of the AMOC circulation, defined as $T = T_e - T_p$ and $S = S_e - S_p$. The overturning rate is proportional to the resulting density differences, representing the basic mechanism of NADW formation and allowing for bi-stability \cite{rahmstorf1996freshwater}. The strength of AMOC flow, $\Psi = T - S$, is thermally driven ($\Psi > 0$) in the on state, but transitions to being salinity driven when $\Psi < 0$ \cite{stommel1961thermohaline, mehling2024limits}.

The Stommel two-box model is described by:

\begin{align}
\dot{T} &= \frac{-1}{\epsilon_a}(T-\Theta(t))-T-\mu|S-T|T\\
\dot{S} &= \sigma(t) - S - \mu|S-T|S
\end{align}

where $\mu$ gives the strength of the transport and $\sigma(t)$ represents freshwater flux \cite{gottwald2021model}.  $\epsilon_a$ is the relaxation of the deep ocean temperature to $\Theta(t)$, the ambient temperature. 

The Stommel and Lorenz-84 models are coupled through temperature gradients and freshwater flux. $\Theta(t)$ is driven by the atmosphere's thermal wind balance:

\begin{align}
\Theta(t) &= \Theta_0 + \Theta_1  \frac{(x_n-\bar{x_n})}{(\sqrt{\epsilon_f})}
\end{align}

where  $\epsilon_f$ represents the ratio of timescales of the fast atmosphere and slow ocean. $\sigma(t)$ becomes a function of the atmosphere's sine and cosine phases of large-scale eddies, $\Delta=y^2+z^2$. 

\begin{align}
\sigma(t) &= \sigma_0 + \sigma_1  \frac{(\Delta - \bar{\Delta})}{(\sqrt{\epsilon_f})}
\end{align}

The atmospheric driving terms $\frac{x-\bar{x}}{\sqrt{\epsilon_f}}$ and $\frac{\Delta - \bar{\Delta}}{\sqrt{\epsilon_f}}$ converge to Brownian motion as $\epsilon_f \to 0$ \cite{gottwald2021model}, allowing for the integrated fast chaotic variable to act as noise on the slower timescale of the ocean. The final 5-dimensional coupled model is given by:


\begin{align}
\dot{x} &= \frac{1}{\epsilon_f}(-\Delta - a(x - F_0 - F_1T)) \\
\dot{y} &= \frac{1}{\epsilon_f}(xy - bxz - (y-G_0 + G_1T)) \\
\dot{z} &= \frac{1}{\epsilon_f}(bxy + xz -z)
\end{align}

\begin{align}
\dot{T} &= \frac{-1}{\epsilon_a}(T-\Theta(t))-T-\mu|S-T|T\\
\dot{S} &= \sigma(t) - S - \mu|S-T|S
\end{align}

A two way coupling is achieved, with the atmosphere driving the ocean through $\sigma_0$ and $\Theta$, and the ocean driving the atmosphere through the meridional temperature gradient, $F$. Here the sea ice component from the original Gottwald model has been removed as in \cite{mehling2024limits}.

Table~\ref{table:parameters} gives the values used in our model.

\begin{table}[ht]
\begin{tabularx}{\linewidth}{|c|>{\raggedright\arraybackslash}X|c|}
\hline
Parameter & Description & value \\
\hline
$a$ & displacement of westerly current compared to eddies & $0.25$ \\ \hline
$b$    & damping of westerly current compared to eddies & $4$ \\ \hline
$F$    & relaxation for $x$ in an uncoupled model & $8$ \\ \hline
$G$    & relaxation term for $y$ in an uncoupled model & $1$  \\ \hline
$\mu$    & strength of transport & $7.5$  \\ \hline
$\sigma$    & freshwater flux & varied, $0.9$ to $0.99$  \\ \hline
$\epsilon_a$    & relaxation of deep ocean temperature & $0.34$  \\ \hline
$\epsilon_f$    & ratio of timescales of fast atmosphere and slow ocean & $0.0003$  \\

\hline
\end{tabularx}
\label{table:parameters}
\end{table}

\subsection{Rare Event Algorithm}

Rare event algorithms come out of the theory of importance sampling, which says that some random variables contribute more to the variance of the sample than others. Oversampling these 'important' variables creates a new distribution with a reduced variance \cite{smith1997quick}. In our work, the new distribution of interest is collapse events found at extremes of the distribution.

The rare event algorithm used in \cite{ragone2018computation, cini2024simulating} oversamples trajectories headed towards collapse by assigning a weight to each trajectory in an ensemble at each resampling time, based on its proximity to tipping behaviour. Trajectories with weights close to zero are killed, and trajectories with higher weights are cloned proportional to their weight, resulting in an ensemble of trajectories containing a higher proportion of collapse events. 

The algorithm requires selecting a physically reasonable resampling time and an anomaly to bias towards. The resampling time is the time at which the simulation is stopped and trajectories are killed or cloned. A reasonable value for the resampling time is the point at which the auto-correlation decays to zero, since it is assumed that trajectories become independent of each other at this point. For a time series $X(t)$, the normalized auto-correlation function (ACF) is defined as:

\begin{align}
    R(t) &= \frac{((X(s)-\mu)(X(s+t)-\mu))}{\sigma^2}
\end{align}
where $s$ gives the starting time, $\mu$ is the mean of the time series and $\sigma^2$ is the variance. The auto-correlation of the system is averaged across sliding windows of 50 years to reduce noise.  The memory timescale of the system is quantified with the integral auto-correlation time,

\begin{align}\tau_c &= \int_{0}^{+\infty}R(t)dt\end{align}

where $dt$ is the time step and $\tau_c$ corresponds to the area under the auto-correlation curve. In practice, this integral was approximated numerically using the sum. With our resampling time, $\tau_c=1$ selected, we can now choose the target anomaly.

This anomaly, which the distribution will be biased towards, may be found in the tail of the distribution, $c$ standard deviations below/above the mean. In the Gottwald model, reasonably long simulations do not exhibit collapse events. Hence selecting the anomaly requires some trial and error. After several iterations, we have selected an anomaly, $c=-30, c=30$ for collapses of $\Psi$ and $S$ respectively. The distribution is biased according to the following:

\begin{equation}
k\tau_c\sigma^2 \approx\mathbb{E}_k\left[\frac{1}{T_a}\int_0^{T_a} f(X(t))dt\right]
\end{equation}


where $f(X(t))$ is the observable and $T_a$ gives the total simulation time. Hence the time-averaged observable value, is approximately proportional to $k$. $k$ is then the biasing parameter, and its value is given by $k=\frac{a}{\tau_c\sigma^2}$, where $a$ is the anomaly. After parameters $a$, $k$ and $\tau_c$ have been selected, the simulations are run with the rare event algorithm stopping at each resampling time to assign weights to each trajectory. The weight assigned to each trajectory in an ensemble, $w_j$ at time $t_i$, is given by:

\begin{equation}
w_j(t_i) = \frac{e^{k\int_{t_i-1}^{t_i}f(X_j(t))dt}}{Z_i}
\end{equation}

so that for $k>0$ ($k<0$), larger (smaller) values of $f(X_j(t))$ are selected for cloning. $Z_i$ is the normalisation, given by the mean $w_j(t_i)$:

\begin{equation}Z_i = \frac{1}{N}\sum_{j=1}^{N}w_j(t_i)\end{equation}

Trajectories with weights near zero are killed and those with higher weights are cloned proportionally to their weight (keeping the same number of trajectories overall). A small random perturbation, $r \sim \mathcal{U}(-1,1)$ with a noise amplitude of $\epsilon = 10^{-5}$ is added to each cloned trajectory. After adding the perturbations to the cloned trajectories, the simulation is run again, and the process repeats.

The full experimental design began with a run of $50,000$ years to provide a control for comparison between states. Snapshots of the full system were taken from the $50,000$-year control run at regular intervals, and used as initial conditions for  the ensemble of $10,000$ trajectories. The rare event algorithm was applied at regular sampling intervals, $\tau_c$. Experiments were conducted applying the algorithm to $T$, $S$ and $\Psi$ separately. In practice, this works best in chunks, where $10$ ensembles of $1000$ trajectories are run in parallel, to prevent degeneracy of ancestors. The path was mapped in the phase space of $T$ and $S$ from initial conditions in the on state to the off state. Probabilities of collapse were estimated by assigning a binary value to each collapse event, and re-weighting events by their inverse to find expectation values in an ensemble of $10,000$ trajectories under normal dynamics.

\subsection{The Edge State}

Discovering where the edge state lies in the dynamics of the Gottwald model allows us to run a preliminary check on whether our deterministic collapses are crossing the boundary. Defining the edge state begins with an edge tracking algorithm initially designed for turbulent flow \cite{skufca2006edge}, and applied to climate modelling thereafter \cite{lucarini2017edge,lohmann2025role,borner2026global}. The edge of the Gottwald model has already been described in \cite{mehling2024limits} and the associated Julia package, CriticalTransitions v0.8.0 \cite{borner_climate_2025} allowed us to reproduce these results. 

We begin with two system states, $u_1$, and $u_2$, which belong to different attractors. These are obtained from deterministic simulations where a transition has been achieved. Two simulations of the given model are initiated in parallel, using $u_1$ and $u_2$ as the starting states, until the two states diverge by a specified Euclidean distance tolerance threshold, $\epsilon_1 = 10^{-8}$. The starting states of the next parallel simulations are taken as a bisection along a straight line in this result so that the two new initial starting states diverge by the Euclidean distance tolearance threshold, $\epsilon_2 = 10^{-9}$. This repeats until a convergence to the basin boundary has been achieved \cite{mehling2024limits}. 

In the Gottwald model, the edge state has been mapped only in the phase space of $T$ and $S$, as the chaotic dynamics of the atmosphere do not converge after $100$ iterations, and because we are interested in the collapse path of the oceanic variables. 

Edge tracking in PLASIM-LSG takes the same form as in the Gottwald model. The higher-dimensionality allows for the identification of excursive markers, variables which identify the edge state by their difference from either attractor. These markers have been discussed in more detail in Section 4.6.  

\subsection{The Stochastic Model}

We hypothesised that the collapse path taken in the deterministic model aligns with the instanton, the least energy path between on and off states. To determine the instanton in $T$ and $S$, we must reduce the system to its slow-only dynamics. Exploiting the two-way coupling of the ocean and atmosphere, we can implicitly code the atmosphere into an ocean-only model, allowing for the creation of a stochastic system which can tip without the use of the rare event algorithm, and hence for which the instanton can be calculated. 

One fast atmospheric timestep, $\delta_f$, is related to one slow oceanic timestep, $\delta_s$, according to
\begin{equation}
\gamma = \frac{\delta_s}{\delta_f},
\qquad
\delta_s = \frac{\delta_f}{\epsilon_f},
\end{equation}
where $\gamma$ describes the ratio of fast to slow timesteps and $\epsilon_f$ is the coupling term. We represent these fast-slow dynamics as:

\begin{align}
x = [x,y,z], \dot{x} = \frac{1}{\epsilon_f}g_1(X) + \frac{1}{\epsilon_f}g_2(x) \\
X = [T,S], \dot{X} = a(X) + \frac{1}{\sqrt{\epsilon_f}}b(x)
\end{align}

where $a(X)$ is the oceanic drift term and $b(x)$ represents the noise driven by the atmosphere. Homogenisation theory \cite{engel2021homogenization} states that as $\epsilon_f \to 0$, 

\begin{equation}
d(X) = a(X)dt + \sigma(X)dW
\end{equation}

where $dW$ is a Wiener process, so that in the limit of infinite timescale separation, stochastic dynamics have been made implicit in the slow variables. The coefficient $\sigma(X)$ describes the noise strength, which is given by a covariance matrix, $\sigma(X)\sigma(X)^{T}$:

\begin{align}
Q(T) = \begin{pmatrix} 
        \sigma_{T}^2 & \sigma_{TS} \\
        \sigma_{TS} & \sigma_{S}^2
        \end{pmatrix}
\end{align}

where $\sigma_{T}^2$ and $\sigma_{S}^2$ are the variances of temperature and salinity, respectively, and $\sigma_{TS}$ is the covariance between the two variables. This matrix is found by holding the oceanic properties, $X$, fixed while the atmospheric forcing, $b(x(0))$ is compared to itself at lag, $b(x(t))$, averaging the comparisons across the atmosphere's long-term state and integrating each lag:

\begin{align}
\sigma(X)\sigma(X)^{T}=\int_{0}^{\infty} dt \int d\mu_X(x)\,
(b(x(0)) \otimes b(x(t))+b(x(t)) \otimes b(x(0))
\end{align}

where $\otimes$ is a tensor product and $\mu_X(x)$ is the invariant measure of the fast system. Noise can then be given as independent random Guassian draws which are related by the correlation of $S$ and $T$, and where the correlation depends on $T$.

Because the atmosphere depends on $T$, the covariance matrix must be defined as a function of $T$ for all $T$. In practice, a family of diffusion matrices was calculated for $100$ values of $T$, and a cubic fit was applied to the returned data to give an estimate of the covariance matrix. The final stochastic model capable of spontaneous noise-induced transitions is below:

\begin{align}
\dot{T} = dt(\frac{-1}{\epsilon_a}(T-\Theta_0) - T - \mu|S-T|T) + x_1\sqrt{dt}\\
\dot{S} = dt(\sigma_0-S-\mu|S-T|S) + x_2\sqrt{dt}
\end{align}

where $(x1, x2)$ are the two independent random normals related by the correlation of $S$ and $T$, and where $T$ is state-dependent. This approximates the correlated additive and multiplicative noise used in the original Gottwald deterministic model.

\subsection{The Instanton}

In general terms, the instanton is the minimum energy and maximum likelihood path between two states \cite{vanden2008geometric}. The mathematical foundation behind the calculation of instantons is based largely on Freidlin-Wentzell large deviation theory, out of which comes the idea of the associated Freidlin-Wentzell action \cite{freidlin1998random}. The action of the path measures the deviation of a path's velocity, $\phi$ from its deterministic drift, $a(\phi)$:

\begin{align}
\phi(t) = (T(t), S(t)) \\
S_{Ta}(\phi) = \frac{1}{2}\int_{0}^{T_a} <\dot{\phi} - a(\phi),x^{-1}(\dot{\phi}-a(\phi))>dt
\end{align}

where $\phi(0) \in A$ (AMOC on) and $\phi(T_{a}) \in B$ (AMOC off). The minimum action path is found by comparing all actions of all possible paths. Of the many instanton methods, we have selected the geometric minimum action method (gMAM) \cite{vanden2008geometric, grafke2015instanton} for our purposes, which can be applied to systems with state-dependent noise. 

The gMAM method has been implemented using the Julia package CriticalTransitions v0.9.0 \cite{borner2025climate}. The stochastic model defined in Equations 24 and 25 is split into drift and diffusion terms, which are passed as separate arguments in the CoupledSDEs method to allow for multiplicative noise. Starting and ending states are defined as $t_i=(0.57,0.43)$ and $t_F = (0.73,0.76)$ respectively. The instanton is found by iterating over all possible paths, and comparing each path, $x$, to a control, $u$, to minimise the Freidlin-Wentzell action.

We then compare our instanton calculation to our deterministic collapse paths, and observe variations in instantons as $\sigma_0$ is varied. As an added benefit of the calculation, we are able to determine the path from the off state back to the on state, and thus complete a hysteresis diagram for the Gottwald model. 
 

\subsection{PLASIM-LSG: A Higher-Order Model}

A model intercomparison was conducted to demonstrate the application of a rare event algorithm for the characterisation of the instanton. PlaSim-LSG is an Earth System Model of Intermediate Complexity (EMIC). It has been based on a simplified general circulation model, the Portable University Model of the Atmosphere (PUMA) \cite{fraedrich2005planet, mehling2023high} which contains a spectral dynamical core based on the moist primitive equations.  This has been coupled with systems of lower complexity including land-surface processes, vegetation, and sea ice \cite{fraedrich2005planet}. PlaSim has then been coupled with the large-scale geostrophic ocean (LSG) \cite{shifterjhardenberg}. The added LSG component better simulates centennial AMOC variability which is influenced by geostrophic changes \cite{mehling2023high}. 

We have used PLASIM-LSG v1 with default settings, which gives an AMOC in present-day conditions \cite{shifterjhardenberg, borner2026global}. Parameters selected for PlaSim-LSG follow those described in \cite{cini2024simulating}, where the resampling time of the rare event algorithm is $1$ year, allowing for the completion of one seasonal cycle, and biasing parameter is $k=-3$. PlaSim-LSG  has been configured with a T21 resolution and with 10 vertical layers. The strength of the overturning of the AMOC is measured in Sverdrups (Sv), with 1 Sverdrup equalling 1 million cubic meters per second, where the average flow in higher latitudes is about 17.0 Sv \cite{weijer2019stability}, and the threshold of collapse in this study is 10.0 Sv. Simulations of PlaSim-LSG are conducted on the high-performance computing service, running 10 trajectories in parallel to improve the speed of the model. 

A control run of 2000 years was initiated, where the first 1000 years were discarded as a transient period. Snapshots of the full system state were selected at evenly spaced intervals in the control run, and used as initial conditions of the 100-member ensemble. Simulations from the stationary on-state were integrated for 150 years, with the rare event algorithm applied to the AMOC index at each resampling time, and the small random perturbation added to the sea level pressure as described in \cite{cini2024simulating}.

PLASIM-LSG's edge state is defined in terms of its excursive markers. Following parallel methodology to the Gottwald research, we have assumed the LSG ocean is split into polar and equatorial boxes. The polar box is defined as $40^\circ\text{--}80^\circ\text{N}$ and equatorial as $0^\circ\text{--}20^\circ\text{N}$. Excursive markers of the edge state in PLASIM-LSG have been described in \cite{borner2026global}. These include:
\begin{enumerate}
    \item the meridional salinity gradient: the difference in average salinity at depths of 100-1000m in polar and equatorial boxes
    \item the vertical salinity gradient: the difference in average salinity at $46^\circ\text{--}66^\circ\text{N}$ between depths of 100-1000m and 1000-3000m
    \item the salinity anomaly: the average salinity anomaly relative to -35kg/g north of $50^\circ\text{N}$ and with a depth below 1000m
\end{enumerate}

For ease of comparison with the Gottwald model, we have added a meridional temperature gradient.  

\section{Results} 

We begin with the deterministic collapse events that were oversampled using the rare event algorithm. Table~\ref{table:exps} shows experiments applied to each observable, $T$, $S$ and $\Psi$, and the anomalies, $a$, that were targeted in terms of standard deviations from the mean. While $k$ has been calculated explicitly for each experiment, $k$ was varied in practice to determine the lowest possible biasing that results in a collapse, with the goal of maximising the number of original ancestors that are cloned and have descendants in the final distribution. We found that the minimum biasing parameter was equally or more effective than a stronger one, with collapses sometimes occurring after fewer model years at lower values of $k$. However, minimising $k$ did not entirely solve the problem of ancestor degeneracy, which was solved through running 10 instances of 1000 trajectories, forcing the very degenerate ensemble to select $x>10$ ancestors for each simulaton.

\begin{table}[H]
\centering
\begin{tabular}{|c| c |c |c |c}
\hline
Observable & $a$ & $k$ & $k$ variations \\
\hline
$\Psi$ & $\mu - 30\sigma$ & $-1744$ & $-500,\,-1000,\,-2000$  \\
$S$    & $\mu + 30\sigma$ & $8282$ & $7000,\,8000,\,9000$  \\
$T$    & $\mu - 30\sigma$ & $-46866$ & $-4000,\,-5000,\,-6000$  \\
\hline
\end{tabular}
\label{table:exps}
\end{table}

Collapse events with the rare event algorithm applied to $\Psi$ and $S$ are shown in Figure~\ref{fig:collapses}. Recall that the biasing parameter, $k$, assigns weights to trajectories based on their proximity to a collapse event. This is a simplified prediction, where we assume a steadily decreasing temperature gradient and AMOC index, and a steadily increasing increasing salinity gradient. No collapse event is observed for the experiments in $T$. This is confirmed by the $T$ timeseries in $S$ collapse events, where an AMOC collapse has an increase in $T$ at first and hence will not allow a negative anomaly to collapse the AMOC. 

\begin{figure}[H]
\centering
\subfloat[]{\includegraphics[width=0.45\textwidth]{figures/ancestors_fixed_amoc_running_average (1).png}}
\subfloat[]{\includegraphics[width=0.45\textwidth]{figures/ancestors_fixed_salinity_running_average.png}}
\caption{A running average of collapses is shown, with the rare event algorithm applied to the AMOC (a), and to salinity (b). Each line represents the mean trajectory of one ancestor.}
\label{fig:collapses}
\end{figure} 

To provide evidence that the rare event algorithm biases trajectories towards the instanton, we first check if our deterministic collapse paths cross the edge state. The edge bisection and tracking algorithm reached convergence after 100 iterations. In Figure~\ref{fig:edge_convergence}, the edge state is compared to the on and off states in all 5 dimensions of the Gottwald model, with the atmosphere represented as $x^2 + y^2 + z^2$. While the chaotic atmosphere does not show clear variation between states, the oceanic components show clear separation in the phase space of $T$ and $S$. 
\begin{figure}[H]
\centering
\subfloat[]{\includegraphics[width=0.45\textwidth]{figures/3D_edge.png}}
\caption{The edge (yellow), on (teal), and off (salmon) states are compared in all 5 dimensions of the Gottwald model.}
\label{fig:edge_convergence}
\end{figure} 

The ensemble of trajectories is shown as a function of $T$, $S$ and time (as a color gradient) against the edge state, shown in slate black in Figure~\ref{fig:path_edge}. The ensemble clusters around the edge state, confirming our deterministic collapse path's passage through it.

\begin{figure}[H]
\centering
\subfloat[]{\includegraphics[width=0.45\textwidth]{figures/edge_instanton_salinity.png}}
\caption{The deterministic collapse path is shown over time in the phase space of temperature and salinity. It is compared to the calculated edge state, shown in black.}
\label{fig:path_edge}
\end{figure} 

We proceed with the calculation of the instanton by first building the stochastic system described in Section IV. We observe similar steady states between deterministic and stochastic models, shown in the probability density functions in Figure~\ref{fig:hists}. 

\begin{figure}[H]
\centering
\subfloat[]{\includegraphics[width=0.45\textwidth]{figures/stoch_det_dens.png}}
\caption{The distribution of AMOC indices is demonstrated in the deterministic model (a) and stochastic model (b).}
\label{fig:hists}
\end{figure} 

The minimum action between the initial state in $T$ and $S$, (0.57,0.43) and end state (0.73,0.76) is shown in Figure~\ref{fig:path_edge_instanton} overlaid on the deterministic transition path, where the instanton has been calculated from the on state to the off state. Very good agreement between the calculated instanton and the deterministic collapse trajectory gives a good argument to say that the rare event algorithm may be automatically selecting the instanton path. 

\begin{figure}[H]
\centering
\subfloat[]{\includegraphics[width=0.45\textwidth]{figures/edge_instanton_amoc_073076 (2).png}}
\caption{The deterministic collapse trajectory in an ensemble has been plotted in the phase space of $T$ and $S$ shown over model years 0-40 (gradient bar). This is compared to the edge state, in black, and the instanton path from on state to off state, in teal.}
\label{fig:path_edge_instanton}
\end{figure} 

Thus far, the research has shown results with a fixed freshwater flux, $\sigma_0 = 0.9$. In figure ~\ref{fig:sigma_det_stoch_edge}a, we vary $\sigma_0$, and compare the collapse paths against the edge state for different freshwater forcing scenarios. As $\sigma_0$ increases, the initial state of the system closes its distance to the edge state. Although the edge state itself does not vary with the control parameter, the starting state moves closer to the edge. Similar results are obtained in the stochastic model in Figure~\ref{fig:sigma_det_stoch_edge}b, confirming that model results are interchangeable. 

\begin{figure}[H]
\centering
\subfloat[]{\includegraphics[width=0.45\textwidth]{figures/sigma_varied_deterministic_edge.png}}
\subfloat[]{\includegraphics[width=0.45\textwidth]{figures/sigma_varied_stochastic_edge.png}}
\caption{Collapse paths from the Gottwald deterministic model (a) and stochastic model (b) are shown in the phase space of temperature and salinity, for 5 freshwater forcing scenarios, $\sigma_0$. The transitions are compared to the edge state in black.}
\label{fig:sigma_det_stoch_edge}
\end{figure} 

We next investigate our second hypothesis that probabilities of tipping increase as the distance to the edge state is closed, or as the system moves towards the bifurcation point. Now N-tipping will be combined with other tipping types, expressed with 10 freshwater forcing scenarios shown in Table~\ref{stats}. 

\begin{table}[ht]
\centering
\begin{tabular}{|c |c|}
\hline
$\sigma_0$ & Expectation \\
\hline
0.9 & 0.0004 \\ \hline
0.95 & 0.0004 \\ \hline
0.96 & 0.0004 \\ \hline
0.97 & 0.0004 \\ \hline
0.98 & 0.0004 \\ \hline
0.99 & 0.0004 \\
\hline
\end{tabular}
\label{table:stats}
\end{table}


To complete the picture, we investigate returns of the system from AMOC off to AMOC on. With each experiment in Table~\ref{table:exps} repeated for the opposite anomaly, no transitions from off to on were observed in the deterministic model. However, the instanton path back to the on state can be easily calculated by reversing the end states and initial states given to the algorithm. In Figure~\ref{fig:hysteresis}a the instanton from the on state to the off state is shown with varied $\sigma_0$, and again from the off to the on state in Figure~\ref{fig:hysteresis}b. The resulting hysteresis diagram in Figure~\ref{fig:hysteresis}c demonstrates that a return to the on state after collapse is not as simple as the initial collapse. 

\begin{figure}[H]
\centering
\subfloat[]{\includegraphics[width=0.45\textwidth]{figures/sigma_instanton_changes_SDE (1).png}}
\subfloat[]{\includegraphics[width=0.45\textwidth]{figures/sigma_instanton_back_changes_SDE (1).png}} \\
\subfloat[]{\includegraphics[width=0.45\textwidth]{figures/instanton_complete.png}}
\caption{Instantons calculated from varied $\sigma_0$ are shown in the phase space of $T$ and $S$, from on to off (a) and off to on (b). The complete hysteresis diagram is shown in c.}
\label{fig:hysteresis}
\end{figure} 

Assuming now that the rare event algorithm does indeed bias trajectories towards the instanton path, we turn to a higher-order model where the instanton cannot be calculated explicitly, PLASIM-LSG. The N-tipping experiment of \cite{cini2024simulating} was reproduced, resulting in a transition from the AMOC on to the off state in a 100-member ensemble integrated for 140 years. A collapse occurs by Year 100, as shown in Figure~\ref{fig:plasim_collapse}.

\begin{figure}[H]
    \centering
    \includegraphics[width=0.8\textwidth]{figures/amoc_collapse_fixed.png}
    \caption{A time series of the AMOC index is shown, with a clear transition around Year 100.}
    \label{fig:plasim_collapse}
\end{figure}

PLASIM-LSG's excursive markers as discussed in \cite{borner2026global}, represent physical characterisations of the edge state, and would serve as EWS that are easier to identify than edge state variables which instead remain near the on or off attractors. Following \cite{borner2026global}, we assume these variability of the edge state compared to on and off attractors to be described largely by three components, namely the meridional salinity gradients, the vertical salinity gradient, and the salinity anomaly, explained in detail in Section IV. We have also included sea surface temperature, to compare transition paths between the Gottwald model and PLASIM-LSG.

Meridional salinity and temperature gradients are calculated as in the Gottwald model, with the polar box subtracted from the equatorial box, shown in Figures~\ref{fig:gradients}a (temperature) and 11b (salinity). A sharp spike is obvious in the meridional salinity gradient when polar and equatorial boxes diverge in the edge state.

\begin{figure}[H]
    \centering
    \subfloat[]{\includegraphics[width=0.45\textwidth]{figures/plasim_s_gradient.png}}
    \subfloat[]{\includegraphics[width=0.45\textwidth]{figures/plasim_sst_gradient.png}}
    \caption{Sea surface salinity (a) and temperature (b) gradients are shown as a function of time, with sea surface salinity exhibiting an excursion during the edge state period around Year 80.}
    \label{fig:gradients}
\end{figure}


The deterministic collapse path in the phase space of $T$, the sea surface temperature gradient in PLASIM-LSG, and $S$, average salinity gradient in the depths 100-1000m, or meridional salinity gradient, is demonstrated in Figure~\ref{fig:plasim_paths}a. The edge state excursive markers meridional salinity gradient, vertical salinity gradient, and salinity anomaly are demonstrated in the 3D plot in Figure~\ref{fig:plasim_paths}b, confirming results of \cite{borner2026global}, and confirming the passing of our collapse path through the edge state. The salinity anomaly difference between off and on states is shown in Figure~\ref{fig:plasim_paths}c, with the anomaly difference decreasing around Greenland.  

\begin{figure}[H]
    \centering
    \subfloat[]{\includegraphics[width=0.45\textwidth]{figures/plasim_plot_3D_salts.png}}
    \subfloat[]{\includegraphics[width=0.45\textwidth]{figures/on.png}}\\
    \subfloat[]{\includegraphics[width=0.45\textwidth]{figures/plasim_deep_map.png}}
    \caption{Sea surface salinity (a) and temperature (b) gradients are shown as a function of time, with sea surface salinity exhibiting an excursion during the edge state period around Year 80. The salinity anomaly (c) difference between off and on states is shown spatially distributed in the map. A decrease in the anomaly is seen around Greenland.}
    \label{fig:plasim_paths}
\end{figure}


\section{Conclusions}

We have begun this paper by discussing noise-induced transitions of the AMOC, which can happen anywhere along the bifurcation branch of the AMOC system due to their stochastic nature. As such, EWS are not robustly developed for this type of tipping, inviting a need for the advancement of EWS research, which is focused on mapping edge states and calculating instantons. Although there has been much progress on the former, instantons are nigh-impossible to calculate in any order of model which reflects climate more accurately. We submit this paper to hypothesise that the rare event algorithm, thus far used as a statistical tool for creating distributions of unlikely events, can also be applied to estimate the instanton, or least-action collapse path of a system. The next logical step following these conclusions is to apply the rare event sampling algorithm to a suite of higher-order models, particularly those in which the edge state can be calculated explicitly, and confirming whether the collapse path passes through the edge state. Another useful direction is defining jump conditions, which mark the phase space of the instanton in a meaningful way.

We also demonstrate that noise-induced transitions increase in likelihood as a tipping point is approached, due to the combination of rate-induced and noise-induced tipping types. We observe that as the bifurcation point is approached, the edge state moves closer to the current state of the system, where eventually the on state is expected to disappear altogether. This complicates the return to on state, as demonstrated in the increasing extremes in $T$ and $S$ on the return path of the calculated instanton. This hysteresis has also been found in other models, again making the case that the prevention of AMOC tipping is of utmost importance \cite{jackson2023understanding,jackson2017ocean}

