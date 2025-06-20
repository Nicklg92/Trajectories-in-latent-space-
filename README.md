# Trajectories-in-latent-space
Goal of this repo is to study tokens' trajectories traced in the latent space and, in particular, the shape of the attractors they define and their association (if any) to the token's semantic properties. 

The idea is rooted in "Scaling up Test-Time Compute with Latent Reasoning: A Recurrent Depth Approach", Geiping et al. 2025, available [here](https://arxiv.org/pdf/2502.05171).

In their study, in particular Figure 12, they studied the evolution of the trajectories of a subset of tokens' hidden states (2-dimensionally plotted via PCA) across decoder-layers recurrencies, with an interest in not only checking if said trajectories would converge to an attractor. In doing so, they notice not only that said converge is observed, but even that differently shaped areas for convergence are observed (proper fixed points, sliders, or orbits).
They also point out which are these tokens that define these differently-shaped attractors.

Building on these results, we further investigate two additional research questions:

1) Are the hidden states' representation converging to a given attractors also in standard, decoder-only models, or the recurrency of decoder layers engineered in Geiping et al. 2025 is a necessary condition for it?

2) If the answer to the above is yes, is there a specific relationship between attractors' shapes and the semantic properties of the associated tokens? 


