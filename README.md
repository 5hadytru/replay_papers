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
- The goal here seems to be this: to minimize the KL divergence between the replay buffer's distribution and the actual distribution of whatever data you're storing in it, while 
