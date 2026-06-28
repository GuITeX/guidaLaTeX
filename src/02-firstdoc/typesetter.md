# Compositori

Assieme all'originale compositore `tex` ne esistono molti altri. `luatex` è uno
degli ultimi arrivati e, come dice il nome, include un interprete
[Lua](https://www.lua.org/), un linguaggio di programmazione semplice, potente
ed efficiente.

Per avvalersi di Lua e delle altre nuove funzionalità come quella della
compatibilità con i font Open Type, è consigliabile utilizzare il compositore
`luatex` con il formato LaTeX ovvero il comando `lualatex`.

Il codice del sorgente dovrà essere adattato se si vuole cambiare compositore, e
anche di molto se cambia anche il formato. Lo sviluppo del sistema tende invece
a garantire la retrocompatibilità.
