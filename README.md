# Replay Papers

A structured catalog of replay papers in the continual learning literature

### What are the main design decisions when using replay for continual learning?

1. The type(s) of data in replay buffer
- What kind of data am I storing in my replay buffer? Is my replay 'buffer' generative?
- Am I replaying in the input space, in activation space, or both?
- Examples:
  - Raw inputs (https://arxiv.org/abs/1611.07725)
  - Raw activations (https://arxiv.org/abs/2004.00713)
  - Raw logits (https://arxiv.org/abs/2004.07211)
  - Generative model for inputs (https://arxiv.org/abs/1705.08690)
  - Generative model for activations (https://www.nature.com/articles/s41467-020-17866-2)

2. The algorithm for selecting the contents of the buffer
- In my experience (in CL with pre-trained models), simple diversity + setting a maximum loss for items in the replay buffer works very well
- Insights:
  - Store "easy"/prototypical samples
    - Memory Population in Continual Learning via Outlier Elimination (https://arxiv.org/pdf/2207.01145.pdf)
    - POPULATING MEMORY IN CONTINUAL LEARNING WITH CONSISTENCY AWARE SAMPLING (https://openreview.net/pdf?id=AFhaaOZTkKA)
    - INFORMATION-THEORETIC ONLINE MEMORY SELECTION FOR CONTINUAL LEARNING (https://openreview.net/pdf?id=IpctgL7khPp)
  - Store diverse samples
    - GCR: Gradient Coreset Based Replay Buffer Selection For Continual Learning (https://arxiv.org/abs/2111.11210)
    - Gradient based sample selection for online continual learning (https://arxiv.org/abs/1903.08671)
    - Online Class-Incremental Continual Learning with Adversarial Shapley Value (https://arxiv.org/abs/2009.00093)

3. The algorithm for retrieving samples from the replay buffer
- Ideally is based on characteristics (esp model activations) of current samples
- Understudied area of CL
- Insights:
  - Retrieve samples that are similar to current samples in feature space
    - Ensure that these samples have labels/text-embeddings that are in conflict with current samples' labels
      - Online Class-Incremental Continual Learning with Adversarial Shapley Value (https://arxiv.org/abs/2009.00093)
    - Ensure that each old class is sampled *in proportion* to its samples' similarity to current samples in feature space
      - Learning in deep neural networks and brains with similarity-weighted interleaved learning (https://www.pnas.org/doi/full/10.1073/pnas.2115229119)
  - Can try a brute force approach (retrieve n samples from replay buffer and see which samples have the highest loss increases after the current gradient step)
    - Online Continual Learning with Maximally Interfered Retrieval (https://arxiv.org/abs/1908.04742)

4. The algorithm for regularizing the network such that information contained in replayed samples is exploited properly
- 
