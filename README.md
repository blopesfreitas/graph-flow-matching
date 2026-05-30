# Graph Flow Matching

A prototype generative model for graphs, built from scratch to learn modern
generative methods (flow matching) and apply them to graph-structured data.

## What it does

Given a target graph size and a target **spectral profile** (a histogram of the
normalized Laplacian's eigenvalues), the model generates an adjacency matrix
whose spectrum approximately matches the target.

## How it works

- **Flow matching** on the vectorized upper triangle of the adjacency matrix:
  the model learns a velocity field that transports Gaussian noise to a valid graph.
- **Conditioning** on the target size and spectral histogram via
  **classifier-free guidance**.
- **Training data**: random graphs sampled from Erdős–Rényi, Barabási–Albert,
  and Watts–Strogatz families across a range of sizes and parameters.
- **Evaluation**: a harness that compares generated graphs against baselines
  using spectral (Wasserstein) distance, with optional graph-model parameter
  estimation via the `statGraph` R package.

## Status

This is a learning prototype, not published work. The current architecture
(an MLP over a fixed-size adjacency) doesn't scale or generalize across sizes;
exploring that limitation is part of what the project taught me.

## Running it

Open the notebook in Google Colab (GPU runtime recommended) and run top to bottom.
