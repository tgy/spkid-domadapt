# Compensation techniques

Several compensation techniques were developed to be applied at different steps
of a speaker recognition system. Some will be applied on cepstral features
(e.g.\ \gls{mfcc}), others on \glspl{i-vector}. Note that multiple
compensations strategies can be combined.

This section lays out examples of strategies that were developed or used for
compensating domain mismatch.

## Cepstral features standardization and warping

Acoustic feature standardization is a common and longstanding method of
normalization that was originally developed to provide noise robust speech
recognition and was then applied to speaker recognition. The technique is
applied by using parameters estimated over a sliding segmental window to
normalize each element of a signal-processing front-end feature vector to have
a zero mean and unit standard deviation. This method was intended to reduce
mismatches between the training and testing examples. \newline

Feature warping is an acoustic feature vector post-processing method designed
to introduce robustness to linear channel mismatch and additive noise
conditions. Robustness is achieved by warping individual cepstral feature
streams over a short time interval to conform to a standard Gaussian target
distribution. Unlike feature standardization, feature warping guarantees that
the warped feature distributions are Gaussian, although this may lead to
a suboptimal mapping when the real distribution is non-Gaussian.

## Hyperparameter model conditioning

\Gls{lda} is a common method used to identify a subspace onto which
\glspl{i-vector} are projected so as to simultaneously maximize speaker
discrimination while reducing inter-session variability. Several domain
compensation techniques have been proposed that modify the conventional
computation of the within-speaker and between-speaker scatter matrices used in
applying \gls{lda}. In source normalization, the between-speaker scatter matrix
is computed as the average of the individual in-domain between-speaker scatter
matrices, thereby removing cross-domain bias from the final matrix and avoiding
an overestimation of between-speaker variability. The within-speaker scatter is
then computed as the difference between the total variability scatter and the
between-speaker scatter, thus attempting to introduce cross-domain variability
into the within-speaker scatter matrix. The authors in TODO showed that this
method provided improved performance in NIST SRE12 task, which contained
cross-domain utterances from telephony, microphone and interview recordings.

A related method, referred to as within-class covariance correction, relies on
a conventional computation of the between-speaker scatter matrix but adds
a correction term to the within-scatter matrix using the cross-domain scatter
obtained from a source-labeled dataset. Improvements are reported for both the
RATS task and the 2013 domain adaptation challenge data. Note that both source
normalization and within-class covariance correction rely on the availability
of a large speaker-labeled dataset (although not necessary in-domain) to
compute the \gls{lda} transformation.

## Inter-dataset variability compensation

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

Length normalization is a common component of published state-of-the-art
systems, although descriptions do not always make clear whether the
\gls{i-vector} were properly whitened prior to normalization.
