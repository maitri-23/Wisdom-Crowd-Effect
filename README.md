# Wisdom Crowd Effect

## The union/contraction of star and complete graph is wise, but not one-time wise

### Simulation Approach

Construct 2𝑛×2𝑛 adjacency matrix for the union graph of star graph and complete graph: (W = np.zeros((2*n, 2*n)) n)))

Connect all the leaf nodes(1 to n-1) of star graph to the central node ‘0’: W[0, j] = W[j, 0] = 1 1for j in range(1, n)

Connect each node to every other node (n to 2n-1) in the complete graph: W[i, j] = 1 for i, j in range(n, 2n)

Connect the leaf node n-1 of star graph to node n of the complete graph: W[n, 0] = W[0, n] = 1

Construct the equal-neighbor matrix P[n] where each row iis W[i] / sum(W[i]): (P = np.diag(1 / W.sum(axis=1)) @ W)

Initialize opinions: opinions = np.random.normal(mu, sigma, 2*n); opinions[0]=1 with mu=0 and sigma=1

Update opinions for T iterations: opinions = P @ opinions