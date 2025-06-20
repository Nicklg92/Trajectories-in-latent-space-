# Trajectories-in-latent-space
Goal of this repo is to study tokens' trajectories traced in the latent space and, in particular, the shape of the attractors they define and their association (if any) to the token's semantic properties. 

The idea is rooted in "Scaling up Test-Time Compute with Latent Reasoning: A Recurrent Depth Approach", Geiping et al. 2025, available [here](https://arxiv.org/pdf/2502.05171).

In their study, in particular Figure 12, they studied the evolution of the trajectories of a subset of tokens' hidden states (2-dimensionally plotted via PCA) across decoder-layers recurrencies, with an interest in not only checking if said trajectories would converge to an attractor. In doing so, they notice not only that said converge is observed, but even that differently shaped areas for convergence are observed (proper fixed points, sliders, or orbits).
They also point out which are these tokens that define these differently-shaped attractors.

Building on these results, we further investigate two additional research questions:

1) Are the hidden states' representation converging to a given attractors also in standard, decoder-only models, or the recurrency of decoder layers engineered in Geiping et al. 2025 is a necessary condition for it?

2) If the answer to the above is yes, is there a specific relationship between attractors' shapes and the semantic properties of the associated tokens?

How we proceed:

a) We consider the following decoder-only models: LIST OF MODELS TBD HERE.

b) We define subsets of tokens (word-level) on multiple semantic levels. For instance (TBD HERE):  

b.1) Subset of tokens associated by concepts: fruits, animals, countries, trees, emotional states,... 
b.2) Subset of tokens associated by grammar: articles, verbs, adjectives, pronouns,...
b.3) Subset of tokens associated by lexical structure: starting and ending with vowels, not originally English,... 

The important aspect here is that all the tokens included in a subset live on the same conceptual space: for instance, in the subset of countries, one can have France, Germany, Angola, United States but not Europe, USSR, NATO, etc.

c) We engineer prompts and tasks, for each of the considered subsets, so that the considered models generate the tokens of interests in a context that ensures maximum comparability among learned hidden states. For instance, to get the model to generate "orange", "lemon", and "apple", the prompt may be always: "My favourite drink is [orange, lemon, apple] juice. Please tell me which fruit it is made of". This question, for instance, should ensure that the fruit of interest is generated and the context remains comparable.

d) Finally, we extract the hidden state generated at the end of each layer  - after (BEFORE?) the residual connection after the FeedForward sublayer - and we study the trajectory layer after layer. We 2-dimensionally plot it via PCA, but we also study their mathematical properties in the whole embedding space (MAYBE A SLIGHTLY REDUCED VERSION OF IT TO AVOID CURSE OF DIMENSIONALITY). 

e) We check if attractors have emerged, for each token and across subsets of tokens, studying their (eventual) shapes. We test our initial hypotheses regarding an association between meanings (semantic properties) and the attractors' shapes.

Why this study? We can see at least two reasons why this study can be of interest:

A) Interpretability: we may observe that certain subset of tokens define certain structures for their attractors (a less-defined are of convergence, id est spirals and sliders), as opposed to others that eventually make it to a neat fixed point, or even others that simply continue wobblying around. On top of this, also the velocity of the (eventual) convergence may be of interest. These behaviours may inform us about the perceived degree of complexity of processing this or this other typology of tokens for the specific model.

For instance, one may speculate that the attractors of clear-cut tokens like "orange", "lemon", and "pizza" may converge to a neat fixed point and do so quickly, as there isn't much to be learned about them (quite straightforward tokens-concepts). An opposite behaviour may be observed for tokens-concepts like "ethics", "reasoning" or "morality", quite difficult concepts to refine. 

B) Efficiency: if we find that by subset of tokens (and associated topics), for instance, faster rates of convergence, in certain models, are observed, professionals in business and research setting may consider cutting down models if they're working with said topics. 

For instance, building on the above examples, if you're aimed at fine-tuning an LLM to produce fruit-based juices, maybe you only need one-tenth of the layer usually needed. Conversely, if you want a model to discuss complex phylosophical issues like the nature of reasoning or morality, you may want to keep in all the layers or even build your own model.










