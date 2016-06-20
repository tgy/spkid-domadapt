# Compensation techniques

Several compensation techniques were developed to be applied at different steps
of a speaker recognition system. Some can be applied directly on cepstral
features (\gls{mfcc}) while others can be applied on \glspl{i-vector}.
\textit{Note that multiple compensations strategies can be combined.}

This section lays out examples of strategies that were developed or used for
compensating domain mismatch.

## \Acrlong{cms}

\Gls{cms} is a common and longstanding method of normalization. It was first
developed to provide noise robust speech recognition \cite{viikki1998} and was
soon after applied to speaker recognition \cite{koolwaaij2000}. It is used to
make the system robust to adverse effects that can distort the short-term
distribution of the speech features, such as additive noise and non-linear
effects attributed to handset transducers \cite{kurosawa}.

The recording of a conversation between multiple speakers is often the sum of
two separately recorded channels with possibly different channel
characteristics (e.g.\ two different phones, in the case of a phone
conversation). Parameters should not be calculated over the whole conversation.
Instead, parameters $(\mu, \sigma)$, where $\mu$ is the mean of the cepstral
features and $\sigma$ their standard deviation, are estimated over a limited
sliding time window. The time window has to be long enough to have a reliable
estimation while containing the speech of only one speaker.

This method is equivalent to data whitening assuming that the feature vector
elements are uncorrelated.

## Feature warping

Like \gls{cms}, feature warping is an acoustic feature post-processing method
designed to introduce robustness to linear channel mismatch and additive noise
conditions. \cite{pelecanos2001} It showed improvements over a number of
methods such as \gls{cms}.

The idea is to conform the speech statistics to a target distribution. The
distribution of a cepstral feature stream is warped to a standardised
distribution over a specified time interval.

Unlike feature standardization, feature warping guarantees that
the warped feature distributions are Gaussian, although this may lead to
a suboptimal mapping when the real distribution is non-Gaussian.

Feature warping has now become the standard for compensation at the cepstral
feature level.

## Hyperparameter model conditioning

### \Acrlong{lda}

\Gls{lda} is a channel compensation method used to define a subspace onto which
\glspl{i-vector} are projected that minimizes the intra-class variance caused
by channel effects and maximize the variance between speakers through the
eigenvalue decomposition of,

\begin{equation}
\bm{S}_b \bm{v} = \tau \bm{S}_w \bm{v}
\end{equation}

\noindent where $\tau$ are the eigenvalues, $\bm{v}$ the eigenvectors and
$\bm{S}_b , \bm{S}_w$ the between-classes and within-class matrices, computed
as follows,

\begin{align}
\bm{S}_b &= \sum_{s=1}^S n_s
(\bar{\bm{w}_s} - \bar{\bm{w}})(\bar{\bm{w}_s} - \bar{\bm{w}})^t \\
\bm{S}_w &= \sum_{s=1}^S \sum_{i=1}^{n_s}
(\bar{\bm{w}_i^s} - \bar{\bm{w}_s})(\bar{\bm{w}_i^s} - \bar{\bm{w}_s})^t
\end{align}

\noindent where $S$ is the total number of out-domain speakers, $n_s$ is the
number of sessions of speaker $s$, $\bar{\bm{w}_s}$ is the mean \gls{i-vector}
for each speaker and $\bar{\bm{w}}$ is the mean of all speakers which are
defined by,

\begin{align}
\bar{\bm{w}_s} &= \frac{1}{n_s} \sum_{i=1}^{n_s} \bm{w}_i^s \\
\bar{\bm{w}} &= \frac{1}{N} \sum_{s=1}^S \sum_{i=1}^{n_s} \bm{w}_i^s
\end{align}

\noindent where $N$ is the total number of sessions.

### \gls{lda} variants

Several domain compensation techniques have been proposed that modify the
conventional computation of the within-speaker and between-speaker scatter
matrices used in applying \gls{lda}. In source normalization, the
between-speaker scatter matrix is computed as the average of the individual
in-domain between-speaker scatter matrices, thereby removing cross-domain bias
from the final matrix and avoiding an overestimation of between-speaker
variability. The within-speaker scatter is then computed as the difference
between the total variability scatter and the between-speaker scatter, thus
attempting to introduce cross-domain variability into the within-speaker
scatter matrix. The authors in \cite{mclaren2012} showed that this method
provided improved performance in NIST SRE12 task, which contained cross-domain
utterances from telephony, microphone and interview recordings.

### \Acrlong{wccn}

A related method, referred to as \gls{wccn}, relies on a conventional
computation of the between-speaker \gls{scatter-matrix} but adds a correction
term to the within-scatter matrix using the cross-domain scatter obtained from
a source-labeled dataset. Improvements are reported for both the RATS task and
the 2013 domain adaptation challenge data. Note that both source normalization
and within-class covariance correction rely on the availability of a large
speaker-labeled dataset (although not necessary in-domain) to compute the
\gls{lda} transformation.

## \Acrlong{idvc}

\Gls{idvc} was introduced during the JHU 2013 summer workshop as a means of
conditioning \glspl{i-vector} to compensate for dataset mismatches deliberately
introduced into the domain adaptation challenge task (DAC13). As will be
described in further detail in Section III, the DAC13 corpus consisted of
a fully labeled \gls{swb} dataset, an enroll and test dataset derived from
MIXER data, and an unlabeled SRE dataset available for domain adaptation.
Results presented in TODO show that domain mismatch compensation can be
achieved without using any in-domain adaptation data by applying \gls{nap} to
the \glspl{i-vector} to remove known between-dataset variability. An extension
of the \gls{idvc} concept, described in TODO, showed additional improvements in
performance on the DAC13 challeng task. This method was not evaluated in the
present study.

## Whitening and length normalization

Another \gls{i-vector} conditioning technique is length normalization, which
was introduced in TODO as a means of Gaussianizing \glspl{i-vector} so that
they conform to the Gaussian modeling assumptions made in \gls{plda}. The
length-normalization approach requires that \glspl{i-vector} be whitened before
being projected onto the unit sphere. This relatively simple process allows
conventional \gls{i-vector} recognizers to match the performance of the more
computationally demanding heavy-tailed \gls{plda} model.

Whitening is applied to the data via an affine transformation
$y = S^{-1/2}(w - \bar{w})$ where $w$ is the raw \gls{i-vector}, $\bar{w}$ is
the \gls{i-vector} mean, $S$ is the \gls{i-vector} covariance matrix, and $y$
is the resulting whitened \gls{i-vector}. Ideally $\bar{w}$ and $S$ are
estimated from \glspl{i-vector} derived from the same source as $w$.

Length normalization is a common component of published state-of-the-art
systems, although descriptions do not always make clear whether the
\gls{i-vector} were properly whitened prior to normalization.

