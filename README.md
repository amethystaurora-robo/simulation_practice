# Simulation of Coupled Atmosphere and Ocean based on Gottwald Model

This code is for the Gottwald Model, a simplified climate model, combining a Lorenz-84 chaotic atmosphere and a Stommel simplified ocean 'box' model.

The Lorenz-84 atmosphere involves the variables: 
- x, the east-west strength of westerlies
- y and z, north-south circulation of eddies (y^2 + z^2 = total eddy energy, delta)

The Stommel model is a simplified ocean model without ice, and 2 main variables: 
- T: average temperature
- S: average salinity

This model divides the ocean into 2 boxes, a northern latitude and a southern latitude, finally giving 4 variables-the 2 main variables of each box: (T1, S1) and (T2, S2). The idea with the Stommel model is to produce a circulation strength by finding the density difference between the two boxes, resulting in a variable for AMOC strength:
- 𝛹=𝑇−𝑆

Oceanic boundary conditions (the ocean's temperature and salinity in an equilibrium state) are defined using θ and 𝜎 as average surface temperature and salinity, which they evolve towards exponentially. 

<p>
  <img src="https://github.com/amethystaurora-robo/simulation_practice/blob/main/proxy-image.png" width="700">
</p>

The Gottwald model reproduced in this code couples the Stommel and Lorenz-84 models to give a fast, chaotic atmosphere interacting with a slow ocean. Temperature changes in the atmosphere continuously perturb the ocean, while fluxes in the ocean slowly shift the mean state of the atmosphere. The variable epsilon_f controls the time dynamics of the atmosphere coupled with the ocean. As epsilon_f approaches infinity, time dynamics of the atmosphere approach infinity, and the effect on the ocean becomes infinitesimally small, essentially representing noise.

<p>
  <img src="https://github.com/amethystaurora-robo/simulation_practice/blob/main/gottwald.jpg">
</p>
(Mehling, et al, 2024)
<p></p>
This code has three options for running the model:

1. Regular model (as described above)
2. Scaled model (for use in edge tracking)
3. Seasonal model (for looking at seasonal changes)

Below is the output of the first example run, showing trajectories of each group of variables: t vs s, x vs y, and y vs z.

<p>
  <img src="https://github.com/amethystaurora-robo/simulation_practice/blob/main/gottwald_noice.png">
</p>

The idea of this research project is to vary the time dynamics coupling term, epsilon_f, to find a combination of parameters for which the system has spontaneous transitions between states, by changing epsilon-may find that 2 attractors merge.

References:

Mehling, O., Börner, R. and Lucarini, V., 2024. Limits to predictability of the asymptotic state of the Atlantic Meridional Overturning Circulation in a conceptual climate model. Physica D: Nonlinear Phenomena, 459, p.134043.

