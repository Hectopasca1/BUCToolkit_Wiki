# BUCToolkit Wiki

![logo](https://github.com/Hectopasca1/BUCToolkit_Wiki/blob/main/assets/logo.png "BUCToolkit_logo")

The [wiki webpage](https://hectopasca1.github.io/BUCToolkit_Wiki/) for project [BUCToolkit](https://github.com/TrinitroCat/BM4Ckit)(used to be named "BM4Ckit") is now availble.

Copy "https://hectopasca1.github.io/BUCToolkit_Wiki/" if the hyperlink fails.

<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
Most functions, such as structural optimization, transition state search, molecular dynamics and 
Monte Carlo simulation, support the parallel computing of **both regular batched samples 
(stacked samples with the same atom numbers) and irregular batched samples 
(concatenated samples with different atom numbers)**. 
Input Tensors (of atom coordinates, forces, fixation masks, etc.) should be 3-dimensional. For regular batches,
their shapes are **(batch_size, n_atom, n_dim)**, where `n_dim` is usually 3. For irregular batches, their 
shapes are

$$
(1, \sum_{i} n_{\text{atom}_i}, n_{\text{dim}})
$$

, where `i` is the sample index, and users should provide 
another variable `batch_indices` that records atom numbers of each sample. For example, 
`batch_indices = [64, 56, 72, 83, 102]` means that the samples have 64, 56, 72, 83, 102 atoms, respectively, and 
corresponding shapes of atom coordinates should be `(1, 377, 3)`.
