---


---

<h1 id="teorico-digamos">Teorico ‘digamos’</h1>
<p><strong>Ley de Zipf:</strong><br>
Los lenguajes naturales (LN) tienen <em><strong>distribucion exponencial</strong></em></p>
<blockquote>
<p>Parametros parecidos para cualquier lenguaje!!!</p>
</blockquote>
<p><a href="https://open.spotify.com/intl-es/track/22Fvc0gkf7ZCNQEQ2Oxj6D?si=9a43ff5791a64cd9">Smoke - Remix (Blood Orange)</a></p>
<p>LN = Fenomeno Natural</p>
<blockquote>
<p>Sordos de Nicaragua<br>
Cambio del idioma persa (del nom-ac to erg-abs)<br>
‘ser’ es el valor por defecto de varias lenguas no hace falta la oalabra mr Heidegger</p>
</blockquote>
<p><em><strong>No podemos reducir solo a gramática!</strong></em><br>
Siguiendo al Noam:odemosobservar sitemaricidades trarables automaticamente.</p>
<ul>
<li>mayor parte del LN es <em>regular</em></li>
<li>otra es "independiente* del contexto</li>
<li>pequeña parte <em>sebsible</em> al contexto<br>
<mark>LN es oral</mark><br>
la escritura es un artefacto <em><strong>sobre</strong></em> LN</li>
</ul>
<h2 id="analisis-del-lenguaje">Analisis del Lenguaje</h2>
<ul>
<li>Comprender</li>
<li>Generar<br>
end-to-end vs analisis por niveles<br>
ejemplo trad. autimatica:</li>
<li>analisis y generacion</li>
<li>canal ruidoso</li>
<li>transformers</li>
</ul>
<h1 id="practico">Practico</h1>
<p>Ver: <a href="https://medium.com/nlplanet/two-minutes-nlp-21-learning-resources-for-text-classification-b6f9c43793e1">Two minutes NLP — 21 Learning Resources for Text Classification</a></p>
<p><strong>Preprocesado:</strong></p>
<ul>
<li>
<p>Encoding (intenatar unificar)</p>
</li>
<li>
<p>Tokenizar (spacy, nltk)</p>
</li>
<li>
<p>Expresiones multipalabra (spacy, nltk)</p>
<blockquote>
<p>se hace a mano, es muy costoso sino</p>
</blockquote>
</li>
<li>
<p>Variantes de palabras</p>
<ul>
<li>pasar a minuscula,</li>
<li>recetitas varias</li>
<li>analisi morfologico</li>
<li>typos</li>
</ul>
<blockquote>
<p>nombres propios tratados en espresiones multipalabra</p>
</blockquote>
</li>
<li>
<p>Subconjunstos de palabras</p>
<blockquote>
<p>podemos eliminar el pico y/o la colita de la distribucion</p>
</blockquote>
</li>
<li>
<p>Numeros, frecuencias, stopwords</p>
<p><em><strong><mark>Todos estos pasos deben ser reproducibles!</mark></strong></em></p>
</li>
</ul>
<p><strong>Vectorizacion</strong></p>
<ul>
<li><em>Bag of Words</em> (Naive): Cada palabra es una columna, por fila (tweets, oraciones, texto) se cuenta la cantidad de veces que aparece cada palabra (en su respectiva columna).
<blockquote>
<p>Contra: Muy sparse, podemos mejorarlo intentando eliminar la cola de la distribucion,  o eliminando palabras distribuidas uniformemente.</p>
</blockquote>
</li>
</ul>

