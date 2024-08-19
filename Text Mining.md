---


---

<h1 id="spacy">Spacy</h1>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Import spaCy</span>
<span class="token keyword">import</span> spacy <span class="token keyword">as</span> sp

<span class="token comment"># Create a blank English nlp object</span>
nlp <span class="token operator">=</span> spacy<span class="token punctuation">.</span>blank<span class="token punctuation">(</span><span class="token string">"en"</span><span class="token punctuation">)</span>

<span class="token comment"># Created by processing a string of text with the nlp object </span>
doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"Hello world!"</span><span class="token punctuation">)</span>
</code></pre>
<p><code>is_alpha</code>, <code>is_punct</code> and <code>like_num</code> return boolean values indicating whether the token consists of alphabetic characters, whether it’s punctuation or whether it <em>resembles</em> a number.</p>
<p>The index of a token in the <code>doc</code> is <code>token.i</code></p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment">#Load the small English pipeline </span>
nlp <span class="token operator">=</span> spacy<span class="token punctuation">.</span>load<span class="token punctuation">(</span><span class="token string">"en_core_web_sm"</span><span class="token punctuation">)</span>
</code></pre>
<p>For each token in the doc, we can print the text and the <code>.pos_</code> attribute, the predicted part-of-speech tag.</p>
<h1 id="practico">Practico</h1>
<p>ver: two minutes nlp -21 learning sources for text classification (medium)</p>
<p><strong>Preprocesado:</strong></p>
<ul>
<li>
<p>encoding (ntenatar unificar)</p>
</li>
<li>
<p>tokenizar (spacy, nltk)</p>
</li>
<li>
<p>expresiones multipalabra (spacy, nltk)</p>
<blockquote>
<p>se hace a mano, es muy costoso sino</p>
</blockquote>
</li>
<li>
<p>variantes de palabras</p>
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
<p>subconjunstos de palabras</p>
<blockquote>
<p>podemos eliminar el pico y/o la colita de la distribucion</p>
</blockquote>
</li>
<li>
<p>numeros, frecuencias, stopwords</p>
</li>
</ul>
<p>Todos estos pasos deben ser reproducibles!</p>
<p><strong>Vectorizacion</strong></p>
<ul>
<li><em>Bag of Words</em> (Naive): Cada palabra es una columna, por fila (tweets, oraciones, texto) se cuenta la cantidad de veces que aparece cada palabra (en su respectiva columna).
<blockquote>
<p>Contra: Muy sparse, podemos mejorarlo intentando eliminar la cola de la distribucion,  o eliminando palabras distribuidas uniformemente.</p>
</blockquote>
</li>
</ul>
<h1 id="teorico-digamos">Teorico ‘digamos’</h1>
<p>Ley de Zipf:<br>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e6/Zipf-euro-4_German%2C_Russian%2C_French%2C_Italian%2C_Medieval_English.svg/800px-Zipf-euro-4_German%2C_Russian%2C_French%2C_Italian%2C_Medieval_English.svg.png" alt="Texts in German (1669), Russian (1972), French (1865), Italian (1840), and Medieval English (1460)"><br>
LN tienen distribucion exponencial, parametros parecidos para cualquier lenguaje!!!</p>
<blockquote>
<p>Written with <a href="https://stackedit.io/">StackEdit</a>.</p>
</blockquote>

