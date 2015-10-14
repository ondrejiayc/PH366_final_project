# PH366_final_project
Code and stuff for the final project for Physics 366.

Idealistic plan for the forward model with issues:

1. Propose $\nu$ and $$\sigma$$ in each shell
  * Proper definition of $$\sigma$$ vs. $$\sigma_{rr}$$ in the Jeans' equation -- is some $$\sqrt{3}$$ required?
2. Generate galaxy positions in all shells
  * Presumably we want them uniform in $$x,y,z$$ -- but do we really?
  * Fast uniform draws -- drawing from something weird in $$r,\phi,\theta$$ and transforming, which would give us uniform?
3. Generate velocities in all shells
  * What's ~~better~~ faster but also correct -- drawing each component separately from a gaussian or draw a gaussian speed and uniform direction, and separate into $$x,y,z$$ components?
4. Project into 2D, looking (say) down the $$x$$ axis (shells -> annuli) and compare to the data
  * How exactly to compare? Number of galaxies in each annulus and the spread in velocities? Something else?
5. Repeat 1.-4. a lot
  * How to do the draws the best? There are 2*# of shells parameters; with an ideal acceptance rate of 30%, we drop below 1% acceptance with 2 shells. IDEA: draw parameters one at a time, check acceptance with one new parameter, proceed to a new parameter, till updated all (OK, this is incorrect -- we'd accept 100%, like with Gibbs)
