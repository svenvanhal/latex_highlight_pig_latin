Highlight Pig Latin in LaTeX
==============

Highlight [Pig Latin](https://en.wikipedia.org/wiki/Apache_Pig) in LaTeX documents.

![Pig Latin listing](demo.png)

Add the following line to your LaTeX file:
```latex
\include(pig_style.tex)
```

```\lstset``` has been configured to use Pig by default. Highlighting a code block is as simple as:

```latex
\begin{lstlisting}
wikipedia = LOAD 'wikipedia' USING PigStorage('\t') AS (row:chararray);
tuples = FOREACH wikipedia GENERATE FLATTEN(splitsuc.SPLITSUC(*));
grouped = GROUP tuples BY (word1, word2, word3, word4) PARALLEL 16;
grouped_counted = FOREACH grouped GENERATE group, COUNT(tuples);
STORE grouped_counted INTO 'wikipedia.sql' USING splitsuc.STORESQL();
\end{lstlisting}
```

For different set-ups, add a ```language``` attribute to ```\begin{lstlisting}```

```latex
\begin{lstlisting}[language=Pig]
wikipedia = LOAD 'wikipedia' USING PigStorage('\t') AS (row:chararray);
tuples = FOREACH wikipedia GENERATE FLATTEN(splitsuc.SPLITSUC(*));
grouped = GROUP tuples BY (word1, word2, word3, word4) PARALLEL 16;
grouped_counted = FOREACH grouped GENERATE group, COUNT(tuples);
STORE grouped_counted INTO 'wikipedia.sql' USING splitsuc.STORESQL();
\end{lstlisting}
```
