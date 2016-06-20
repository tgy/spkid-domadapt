# Library of Whiteners

The idea of using different whiteners was introduced in \cite{singer2015}. In
practice, the whitening parameters $(\bar{\bm{w}}, \bm{S})$ are derived from
a combination of sources, making the underlying distribution multi-modal and
thus leading to an improper whitening transformation and suboptimum
Gaussianization via length normalization.

To reduce the effects of domain mismatch on \gls{i-vector} length
normalization, \cite{singer2015} proposes using a \emph{withening library}
whose individual components are estimated from labeled source collections.
Each \gls{i-vector} $\bm{w}$ is compared against a source-specific Gaussian
model $\mathcal{N}(\bm{w}|\mu_j, \bm{S}_j)$, where parameters $(\mu_j,
\bm{S}_j)$ are estimated from source-specific data. The parameters of the
model that produces the maximum likelihood are used to whiten the
\gls{i-vector} $w$ and applied via $y = \bm{S}_j^{-1/2}(\bm{w} - \mu_j)$ where

$$j = \argmax_{i \in (1,\dots,K)} \mathcal{N}(\bm{w}|\mu_i, \bm{S}_i)$$

In other words, the parameters of a Gaussian are estimated independently for
each dataset and a new \gls{i-vector} is whitened using the parameters of the
Gaussian that most likely produced the \gls{i-vector}.
