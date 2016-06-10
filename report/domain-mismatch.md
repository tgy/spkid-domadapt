# Domain Mismatch Compensation


This section gives a brief definition of what \emph{domain mismatch} is and
lays out examples of strategies used for compensating it. It attempts to make
the context clear, ensuring the reader fully understands the next sections.
\newline

An audio recording of a speech contains various information, like:

\begin{itemize}[label=\textbullet]

\item characteristics of the speaker's voice,
\item environment specificities,
\item the content of the speech: language and words used by the speaker,
\item or behavioral information such as the accent or speech rate.

\end{itemize}

Depending on the task, some information can either be very valuable or
completely useless (noise). It even becomes a \textbf{handicap} because the
noise varying from one example to another leads to an increased error rate when
attempting to identify speakers in audio recordings. Note this is not only true
for the particular task of speaker recognition but also in general. Errors are
observed because the decision is not made purely on the speaker's vocal
characteristics, which is the only valuable data in the case of
\emph{text-independent} speaker recognition, but also on information that is
not relevant to the task. \newline

\emph{Domain mismatch} happens when the training examples (audio recordings)
used for tuning the hyperparameters\footnote{universal background model (UBM)
and total variability (T) matrix} of the speaker recognition system and the
examples used for enrolment+testing do not come from the same dataset. They
were recorded in different conditions: the microphone used for recording or the
environment surrounding the speaker may not have been the same. \newline

\emph{Compensating} domain mismatch means filtering out the information in the
data that is specific to the domain and emphasizing the speaker-dependent
information.


## Whitening
