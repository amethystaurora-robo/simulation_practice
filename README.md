# MultiStability in Gottwald Model

This code is for the Gottwald Model, which combines assumptions of a Lorenz-84 chaotic atmosphere and a Stommel ocean '2-box' model.

The Lorenz-84 atmosphere involves the variables: 
- x, the east-west strength of westerlies
- y and z, north-south circulation of eddies (y^2 + z^2 = total eddy energy, delta)

The Stommel model is a simplified ocean model without ice, and 2 main variables: 
- T: average temperature
- S: average salinity

The Stommel model assumes the ocean is 2 boxes, at northern and southern latitudes, with (T1, S1) and (T2, S2). Density differences give circulation strength of the Atlantic Meridional Overturning Circulation (AMOC):
- 𝛹=𝑇−𝑆

Oceanic boundary conditions (the ocean's temperature and salinity in an equilibrium state) are defined using θ and 𝜎 as average surface temperature and salinity, which they evolve towards exponentially. 

<p>
  <img src="https://github.com/amethystaurora-robo/simulation_practice/blob/main/images/proxy-image.png" width="700">
</p>

The Gottwald model reproduced in this code couples the Stommel and Lorenz-84 models to give a fast, chaotic atmosphere interacting with a slow ocean. Temperature changes in the atmosphere continuously perturb the ocean, while fluxes in the ocean slowly shift the mean state of the atmosphere. The variable epsilon_f controls the time dynamics of the atmosphere coupled with the ocean. As epsilon_f approaches infinity, time dynamics of the atmosphere approach infinity, and the effect on the ocean becomes infinitesimally small, essentially representing noise.

<p>
  <img src="https://github.com/amethystaurora-robo/simulation_practice/blob/main/images/gottwald.jpg">
</p>
(Mehling, et al, 2024)
<p></p>

This project varies the coupling term epsilon_f, to attempt to observe transitions and multi-stability in the Gottwald model. 

Below is the analysis of 5 1000-year runs, with epsilon_f changed to approach zero, creating a stronger coupling with the atmosphere and ocean. The runs include parameters of epsilon f 0.03, 0.003, 0.0003, 3e-5, and 3e-6, respectively.

<p>
  <img src="https://github.com/amethystaurora-robo/simulation_practice/blob/main/images/Simulation_1.png" width="700">
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/simulation_practice/blob/main/images/Simulation_2.png" width="700">
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/simulation_practice/blob/main/images/Simulation_3.png" width="700">
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/simulation_practice/blob/main/images/Simulation_4.png" width="700">
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/simulation_practice/blob/main/images/Simulation_5.png" width="700">
</p>

These results show no qualitative changes in behavior of the system. In Simulation 2 a long transient can be observed before settlement in the true attractor. A new approach may be needed to observe transitions in the Gottwald model.


References:

Mehling, O., Börner, R. and Lucarini, V., 2024. Limits to predictability of the asymptotic state of the Atlantic Meridional Overturning Circulation in a conceptual climate model. Physica D: Nonlinear Phenomena, 459, p.134043.

