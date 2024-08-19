---


---

<h1 id="spacy">Spacy</h1>
<h2 id="intro">Intro</h2>
<h3 id="the-nlp-object">The nlp object</h3>
<p>At the center of spaCy is the object containing the processing pipeline. We usually call this variable “nlp”.</p>
<p>For example, to create an English  <code>nlp</code>  object, you can import  <code>spacy</code>  and use the  <code>spacy.blank</code>  method to create a blank English pipeline. You can use the  <code>nlp</code>  object like a function to analyze text.</p>
<p>It contains all the different components in the pipeline.</p>
<p>It also includes language-specific rules used for tokenizing the text into words and punctuation. spaCy supports a variety of languages.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Import spaCy</span>
<span class="token keyword">import</span> spacy
<span class="token comment"># Create a blank English nlp object</span>
nlp <span class="token operator">=</span> spacy<span class="token punctuation">.</span>blank<span class="token punctuation">(</span><span class="token string">"en"</span><span class="token punctuation">)</span>
<span class="token comment"># Created by processing a string of text with the nlp object </span>
doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"Hello world!"</span><span class="token punctuation">)</span>
</code></pre>
<h3 id="the-doc-object">The doc object</h3>
<p>When you process a text with the  <code>nlp</code>  object, spaCy creates a  <code>doc</code>  object – short for “document”. The doc lets you access information about the text in a structured way, and no information is lost.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Created by processing a string of text with the nlp object </span>
doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"Hello world!"</span><span class="token punctuation">)</span>  
<span class="token comment"># Iterate over tokens in a doc  </span>
<span class="token keyword">for</span> token <span class="token keyword">in</span> doc<span class="token punctuation">:</span>  
	<span class="token keyword">print</span><span class="token punctuation">(</span>token<span class="token punctuation">.</span>text<span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre><code>Hello
world
!
</code></pre>
<h3 id="the-token-object">The token object</h3>
<p><code>token</code>  objects represent the tokens in a document – for example, a word or a punctuation character.</p>
<p>To get a token at a specific position, you can index into the doc.</p>
<p><code>token</code>  objects also provide various attributes that let you access more information about the tokens. For example, the  <code>.text</code>  attribute returns the verbatim token text.</p>
<pre class=" language-python"><code class="prism  language-python">doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"Hello world!"</span><span class="token punctuation">)</span>
<span class="token comment"># Index into the Doc to get a single Token</span>
token <span class="token operator">=</span> doc<span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">]</span>
<span class="token comment"># Get the token text via the .text attribute</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>token<span class="token punctuation">.</span>text<span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre><code>world
</code></pre>
<h3 id="the-span-object">The span object</h3>
<p>A  <code>span</code>  object is a slice of the document consisting of one or more tokens. It’s only a view of the  <code>doc</code>  and doesn’t contain any data itself.</p>
<p>To create a span, you can use Python’s slice notation. For example,  <code>1:3</code>  will create a slice starting from the token at position 1, up to – <em><strong>but not including!</strong></em> – the token at position 3.</p>
<pre class=" language-python"><code class="prism  language-python">doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"Hello world!"</span><span class="token punctuation">)</span>
<span class="token comment"># A slice from the Doc is a Span object</span>
span <span class="token operator">=</span> doc<span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">:</span><span class="token number">3</span><span class="token punctuation">]</span>
<span class="token comment"># Get the span text via the .text attribute</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>span<span class="token punctuation">.</span>text<span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre><code>world!
</code></pre>
<h3 id="lexical-attributes">Lexical Attributes</h3>
<p><code>i</code>  is the index of the token within the parent document.</p>
<p><code>text</code>  returns the token text.</p>
<p><code>is_alpha</code>,  <code>is_punct</code>  and  <code>like_num</code>  return boolean values indicating whether the token consists of alphabetic characters, whether it’s punctuation or whether it  <em>resembles</em>  a number.</p>
<p>These attributes are also called lexical attributes: they refer to the entry in the vocabulary and don’t depend on the token’s context.</p>
<pre class=" language-python"><code class="prism  language-python">doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"It costs $5."</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Index:   "</span><span class="token punctuation">,</span> <span class="token punctuation">[</span>token<span class="token punctuation">.</span>i <span class="token keyword">for</span> token <span class="token keyword">in</span> doc<span class="token punctuation">]</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Text:    "</span><span class="token punctuation">,</span> <span class="token punctuation">[</span>token<span class="token punctuation">.</span>text <span class="token keyword">for</span> token <span class="token keyword">in</span> doc<span class="token punctuation">]</span>

<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"is_alpha:"</span><span class="token punctuation">,</span> <span class="token punctuation">[</span>token<span class="token punctuation">.</span>is_alpha <span class="token keyword">for</span> token <span class="token keyword">in</span> doc<span class="token punctuation">]</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"is_punct:"</span><span class="token punctuation">,</span> <span class="token punctuation">[</span>token<span class="token punctuation">.</span>is_punct <span class="token keyword">for</span> token <span class="token keyword">in</span> doc<span class="token punctuation">]</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"like_num:"</span><span class="token punctuation">,</span> <span class="token punctuation">[</span>token<span class="token punctuation">.</span>like_num <span class="token keyword">for</span> token <span class="token keyword">in</span> doc<span class="token punctuation">]</span><span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre><code>Index:    [0, 1, 2, 3, 4]
Text:     ['It', 'costs', '$', '5', '.']
is_alpha: [True, True, False, False, False]
is_punct: [False, False, False, False, True]
like_num: [False, False, False, True, False]
</code></pre>
<h2 id="trained-pipelines">Trained pipelines</h2>
<p>What are trained pipelines?</p>
<ul>
<li>Models that enable spaCy to predict linguistic attributes  <em>in context</em>
<ul>
<li>Part-of-speech tags</li>
<li>Syntactic dependencies</li>
<li>Named entities</li>
</ul>
</li>
<li>Trained on labeled example texts</li>
<li>Can be updated with more examples to fine-tune predictions</li>
</ul>
<h3 id="pipeline-packages">Pipeline Packages</h3>
<p>spaCy provides a number of trained pipeline packages you can download using the  <code>spacy download</code>  command. For example, the “en_core_web_sm” package is a small English pipeline that supports all core capabilities and is trained on web text.</p>
<p>The  <code>spacy.load</code>  method loads a pipeline package by name and returns an  <code>nlp</code>  object.</p>
<p>The package provides the binary weights that enable spaCy to make predictions.</p>
<p>It also includes the vocabulary, meta information about the pipeline and the configuration file used to train it. It tells spaCy which language class to use and how to configure the processing pipeline.</p>
<pre class=" language-python"><code class="prism  language-python">$ python <span class="token operator">-</span>m spacy download en_core_web_sm
</code></pre>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment">#Load the small English pipeline </span>
nlp <span class="token operator">=</span> spacy<span class="token punctuation">.</span>load<span class="token punctuation">(</span><span class="token string">"en_core_web_sm"</span><span class="token punctuation">)</span>
</code></pre>
<h3 id="predicting-part-of-speech-tags">Predicting Part-of-speech Tags</h3>
<p>Let’s take a look at the model’s predictions. In this example, we’re using spaCy to predict <em>part-of-speech tags</em>, the word types in context.</p>
<p>First, we load the small English pipeline and receive an  <code>nlp</code>  object.</p>
<p>Next, we’re processing the text “She ate the pizza”.</p>
<p>For each token in the doc, we can print the text and the  <code>.pos_</code>  attribute, the predicted <em><strong>part-of-speech</strong></em> (tipo de palabra o categoria gramatical) tag.</p>
<p>In spaCy, attributes that return strings usually end with an underscore</p>
<blockquote>
<p>attributes without the underscore return an integer ID value.</p>
</blockquote>
<p>Here, the model correctly predicted “ate” as a verb and “pizza” as a noun.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">import</span> spacy
<span class="token comment"># Load the small English pipeline</span>
nlp <span class="token operator">=</span> spacy<span class="token punctuation">.</span>load<span class="token punctuation">(</span><span class="token string">"en_core_web_sm"</span><span class="token punctuation">)</span>
<span class="token comment"># Process a text</span>
doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"She ate the pizza"</span><span class="token punctuation">)</span>
<span class="token comment"># Iterate over the tokens</span>
<span class="token keyword">for</span> token <span class="token keyword">in</span> doc<span class="token punctuation">:</span>
    <span class="token comment"># Print the text and the predicted part-of-speech tag</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span>token<span class="token punctuation">.</span>text<span class="token punctuation">,</span> token<span class="token punctuation">.</span>pos_<span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">She PRON
ate VERB
the DET
pizza NOUN
</code></pre>
<h3 id="predicting-syntactic-dependencies">Predicting Syntactic Dependencies</h3>
<p>In addition to the part-of-speech tags, we can also predict how the words are related. For example, whether a word is the subject of the sentence or an object.</p>
<p>The  <code>.dep_</code>  attribute returns the <em><strong>predicted dependency label</strong></em>.</p>
<p>The  <code>.head</code>  attribute returns the <em><strong>syntactic head token</strong></em>. You can also think of it as the parent token this word is attached to.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">for</span> token <span class="token keyword">in</span> doc<span class="token punctuation">:</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span>token<span class="token punctuation">.</span>text<span class="token punctuation">,</span> token<span class="token punctuation">.</span>pos_<span class="token punctuation">,</span> token<span class="token punctuation">.</span>dep_<span class="token punctuation">,</span> token<span class="token punctuation">.</span>head<span class="token punctuation">.</span>text<span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">She PRON nsubj ate
ate VERB ROOT ate
the DET det pizza
pizza NOUN dobj ate
</code></pre>
<h1 id="practico">Practico</h1>
<p>Ver: <a href="https://medium.com/nlplanet/two-minutes-nlp-21-learning-resources-for-text-classification-b6f9c43793e1">Two minutes NLP — 21 Learning Resources for Text Classification</a></p>
<p><strong>Preprocesado:</strong></p>
<ul>
<li>
<p>Encoding (ntenatar unificar)</p>
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
<p><em><strong>Todos estos pasos deben ser reproducibles!</strong></em></p>
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
<h1 id="teorico-digamos">Teorico ‘digamos’</h1>
<p><strong>Ley de Zipf:</strong><br>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e6/Zipf-euro-4_German%2C_Russian%2C_French%2C_Italian%2C_Medieval_English.svg/800px-Zipf-euro-4_German%2C_Russian%2C_French%2C_Italian%2C_Medieval_English.svg.png" alt="Texts in German (1669), Russian (1972), French (1865), Italian (1840), and Medieval English (1460)"><br>
Los lenguajes naturales (LN) tienen <em><strong>distribucion exponencial</strong></em></p>
<blockquote>
<p>Parametros parecidos para cualquier lenguaje!!!</p>
</blockquote>
<blockquote>
<p>Written with <a href="https://stackedit.io/">StackEdit</a>.</p>
</blockquote>

