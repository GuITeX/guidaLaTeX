# Matematica

LaTeX è famoso per la qualità con la quale si possono comporre formule
matematiche. Ecco un esempio:

Ciao formula: \\( E = m c^2 \\). Ora, ancora testo.

ottenuto con il codice seguente:

```latex
Ciao formula: \( E = m c^2 \). Ora, ancora testo.
```

Nell'esempio precedente una breve formula matematica è stata inserita
all'interno del testo corrente. In gergo si dice che quella è una formula
*inline*. La matematica nei documenti può comparire anche in regioni a sé
stanti: le cosiddette *formule in display*. Eccone un esempio:

\begin{equation}
f(n, \lambda) = \left(\sqrt{1+\frac{1}{n^4}}-1\right)^{\lambda}
\end{equation}

ottenuto con il codice seguente:

```latex
\[
f(n, \lambda) = \left(\sqrt{1+\frac{1}{n^4}}-1\right)^{\lambda}
\]
```

Si notino i comandi di markup che servono a comporre le varie parti della
formula: ad esempio `\sqrt{...}` serve a disegnare il simbolo di radice quadrata
e a comporre i simboli che vanno sotto radice descritto tra graffe.

Un altro esempio di markup è il comando che compone la frazione (fraction): nel
codice `\frac{1}{n^4}` il primo argomento tra parentesi graffe è il numeratore e
il secondo è il denominatore.
