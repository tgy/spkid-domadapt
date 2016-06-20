# Understanding domain mismatch

This section gives a brief definition of what \emph{domain mismatch} is. It
attempts to make the context clear, ensuring the reader fully understands the
objectives of this study and the content of the next sections.

\begin{center}$\ast$~$\ast$~$\ast$\end{center}

An audio recording of a speech contains various information, e.g.\:

\begin{itemize}[label=\textbullet]

\item characteristics of the speaker's voice,
\item environment specificities,
\item the content of the speech (language and words used by the speaker),
\item or behavioral information such as the accent or speech rate.

\end{itemize}

Depending on the task, some information can either be very valuable or
completely useless (noise). It even becomes a \textbf{handicap} because the
noise varying from one recording to another leads to an increased error rate
when comparing two speakers. \textit{Note this is not only true for the
particular task of speaker recognition but also in general.} Errors are
observed because the decision is not based \emph{purely} on the speaker's vocal
characteristics, which is the only valuable information in the case of
\emph{text-independent} speaker recognition, but also on information that is
irrelevant.
\newline

\emph{Domain mismatch} happens when the training examples (audio recordings)
used for tuning the hyperparameters\footnote{training the \gls{ubm} and
\gls{tvm}} of the speaker recognition system and the examples used for
enrolment+testing do not come from the same dataset. They were recorded in
different conditions: the microphone used for recording or the environment
surrounding the speaker may not have been the same. Thus, to apply speaker
recognition techniques to real-life conversation, it is necessary to find ways
to make the system more robust to new conditions. The extra-information that
comes from a new domain need to be compensated. A definition of \emph{domain
mismatch compensation} can then be given. \newline

\emph{Compensating} domain mismatch means \emph{filtering out} the information
in the data that is specific to the domain (dataset) while \emph{emphasizing}
(or at least leave unimpaired) the speaker-dependent information.
