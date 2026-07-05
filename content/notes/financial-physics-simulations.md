---
title: Financial & Physics Simulations
tags:
  - notes
  - data-analysis
  - finance
  - physics
---

Two fields, one core idea: take a system that's too messy to solve analytically, model its rules, and let the computer run it forward.

## Why they pair well

- **Both are driven by stochastic processes.** Brownian motion was described for pollen grains before it priced options. The random walk underlying a Monte Carlo stock simulation is the same math as particle diffusion.
- **Both punish bad assumptions loudly.** A physics sim with wrong boundary conditions explodes; a financial model with wrong volatility assumptions loses money. Fast feedback is a feature.
- **Both are visualization problems in disguise.** A million simulated paths mean nothing until you can *see* the distribution. This is where `Plotly`, `Dash`, and `Matplotlib` earn their place in my [[about|tech stack]].

## Things I want to explore

- Monte Carlo option pricing with variance-reduction techniques
- N-body simulations and whether their optimization tricks (Barnes-Hut) transfer to large-scale market data
- Agent-based market models — closer to [[notes/4x-strategy-games|4X games]] than to classic finance

*A living note — expect this to change.*
