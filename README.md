TI2736-B_Latex
==============

Highlight Pig Latin in LaTex.

![Pig Latin listing](demo.png)

Zet bovenin je document de volgende regel:

	\include(pig_style.tex)

De standaard ```\lstset``` is ingesteld op Pig. Gebruik daarom voor een blok Pig Latin code het volgende:

	\begin{lstlisting}
	wikipedia = LOAD 'wikipedia' USING PigStorage('\t') AS (row:chararray);
	tuples = FOREACH wikipedia GENERATE FLATTEN(splitsuc.SPLITSUC(*));
	grouped = GROUP tuples BY (word1, word2, word3, word4) PARALLEL 16;
	grouped_counted = FOREACH grouped GENERATE group, COUNT(tuples);
	STORE grouped_counted INTO 'wikipedia.sql' USING splitsuc.STORESQL();
	\end{lstlisting}
	
Mocht je een andere set-up draaien, voeg je het ```lanuage``` attribuut toe aan de ```\begin{lstlisting}```

	\begin{lstlisting}[language=Pig]
	wikipedia = LOAD 'wikipedia' USING PigStorage('\t') AS (row:chararray);
	tuples = FOREACH wikipedia GENERATE FLATTEN(splitsuc.SPLITSUC(*));
	grouped = GROUP tuples BY (word1, word2, word3, word4) PARALLEL 16;
	grouped_counted = FOREACH grouped GENERATE group, COUNT(tuples);
	STORE grouped_counted INTO 'wikipedia.sql' USING splitsuc.STORESQL();
	\end{lstlisting}
