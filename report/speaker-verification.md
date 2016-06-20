# \Gls{i-vector} based speaker verification

This section gives a brief overview of the \gls{i-vector} based speaker
verification system used in this study. The different steps of the process used
to extract an \gls{i-vector} from an audio signal are described.\newline

\begin{figure}[H]
\begin{center}
    \includestandalone[width=9cm]{fig/flowchart}
    \caption{Flowchart of an \gls{i-vector} based speaker verification system}
    \label{fig:spkid:flowchart}
\end{center}
\end{figure}

Once an \gls{i-vector} is obtained from an \gls{utterance}, the extraction
mechanism is ignored and the \gls{i-vector} is regarded as an observation from
a probabilistic generative model.
