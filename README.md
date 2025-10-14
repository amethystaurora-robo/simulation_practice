This code is for the Gottwald Model, a simplified climate model, combining a Lorenz-84 chaotic atmosphere and a Stommel simplified ocean 'box' model.

The Lorenz-84 atmosphere involves the variables: 
- x, the east-west strength of westerlies
- y and z, north-south circulation of eddies (y^2 + z^2 = total eddy energy)

The Stommel model is a simplified ocean model without ice, and 2 main variables: 
- T: average temperature
- S: average salinity

This model divides the ocean into 2 boxes, a northern latitude and a southern latitude, finally giving 4 variables-the 2 main variables of each box: (T1, S1) and (T2, S2). The idea with the Stommel model is to produce a circulation strength by finding the density difference between the two boxes, resulting in a coupled variable for AMOC strength:
- 𝛹=𝑇−𝑆

<p>
  <img src="https://github.com/amethystaurora-robo/simulation_practice/blob/main/proxy-image.png">
</p>

The Gottwald model reproduced in this code couples the Stommel and Lorenz-84 models to give a fast, chaotic atmosphere interacting with a slow ocean. The atmosphere is affected by the ocean through the meridional temperature gradient (F) and zonal temperature gradient (G). Oceanic boundary conditions are defined using θ and 𝜎 as average surface temperature and salinity, which they evolve towards exponentially. 𝜃1 and 𝜎1 are coupling strengths defining ocean sensitivity to atmospheric changes. Temperature changes in the atmosphere continuously perturb the ocean, while fluxes in the ocean slowly shift the mean state of the atmosphere. The ocean relaxes towards Tsurf and Ssurf, which are dynamically changing due to atmospheric fluxes.

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

The plan for this model is to work on edge tracking, so we would use the scaled version. This introduces another term, s, which is used to reduce amplitude of the fast atmosphere.

References:

Mehling, O., Börner, R. and Lucarini, V., 2024. Limits to predictability of the asymptotic state of the Atlantic Meridional Overturning Circulation in a conceptual climate model. Physica D: Nonlinear Phenomena, 459, p.134043.

