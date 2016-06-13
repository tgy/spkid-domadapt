# Library of Whiteners

Whitening is applied to the data via an affine transformation
$y = S^{-1/2}(w - \bar{w})$ where $w$ is the raw \gls{i-vector}, $\bar{w}$ is
the \gls{i-vector} mean, $S$ is the \gls{i-vector} covariance matrix, and $y$
is the resulting whitened \gls{i-vector}. Ideally $\bar{w}$ and $S$ are
estimated from \glspl{i-vector} derived from the same source as $w$. In
practice, however, the data available to train the whitening parameters may be
derived from a combination of sources making the underlying distribution
multi-modal and thus leading to an improper whitening transformation and
suboptimum Gaussianization via length normalization.

To reduce the effects of domain mismatch on \gls{i-vector} length
normalization, this paper proposes using a \emph{withening library} whose
individual components are estimated from labeled source collections. Each
\gls{i-vector} $w$ is compared against a source-specific Gaussian model
$\mathcal{N}(w|\mu_j, S_j)$, where parameters $(\mu_j, S_j)$ are estimated from
source-specific data. The parameters of the model that produces the maximum
likelihood are used to whiten the \gls{i-vector} $w$ and applied via $y
= S_j^{-1/2}(w - \mu_j)$ where

$$j = \argmax_{i \in (1,\dots,K)} \mathcal{N}(w|\mu_i, S_i)$$
