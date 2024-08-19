---


---

<h1 id="chapter-1-finding-words-phrases-names-and-concepts"><a href="https://course.spacy.io/en/chapter1">Chapter 1: Finding words, phrases, names and concepts</a></h1>
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
<p>For each token in the doc, we can print the text and the  <code>.pos_</code>  attribute, the predicted <em><strong>part-of-speech</strong></em> (<mark>tipo de palabra o categoria gramatical</mark>) tag.</p>
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
<p>The  <code>.dep_</code>  attribute returns the <em><strong>predicted dependency label</strong></em> (<mark>lugar en la sintaxis</mark>).</p>
<p>The  <code>.head</code>  attribute returns the <em><strong>syntactic head token</strong></em>. You can also think of it as <mark>the parent token this word is attached to</mark>.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">for</span> token <span class="token keyword">in</span> doc<span class="token punctuation">:</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span>token<span class="token punctuation">.</span>text<span class="token punctuation">,</span> token<span class="token punctuation">.</span>pos_<span class="token punctuation">,</span> token<span class="token punctuation">.</span>dep_<span class="token punctuation">,</span> token<span class="token punctuation">.</span>head<span class="token punctuation">.</span>text<span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">She PRON nsubj ate
ate VERB ROOT ate
the DET det pizza
pizza NOUN dobj ate
</code></pre>
<h3 id="dependency-label-scheme">Dependency label scheme</h3>
<p>To describe syntactic dependencies, spaCy uses a standardized label scheme. Here’s an example of some common labels:</p>
<p>The pronoun “She” is a nominal subject attached to the verb – in this case, to “ate”.</p>
<p>The noun “pizza” is a direct object attached to the verb “ate”. It is eaten by the subject, “she”.</p>
<p>The determiner “the”, also known as an article, is attached to the noun “pizza”.</p>
<p><img src="https://course.spacy.io/dep_example.png" alt="Visualization of the dependency graph for 'She ate the pizza'"></p>
<h3 id="predicting-named-entities">Predicting Named Entities</h3>
<p>Named entities are “real world objects” that are assigned a name – for example, a person, an organization or a country.</p>
<p>The  <code>doc.ents</code>  property lets you access the <em><strong>named entities</strong></em> predicted by the named entity recognition model.</p>
<p>It returns an iterator of  <code>span</code>  objects, so we can print the entity text and the <em><strong>entity label</strong></em> using the  <code>.label_</code>  attribute.</p>
<p>In this case, the model is correctly predicting “Apple” as an organization, “U.K.” as a geopolitical entity and “$1 billion” as money.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Process a text</span>
doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"Apple is looking at buying U.K. startup for $1 billion"</span><span class="token punctuation">)</span>
<span class="token comment"># Iterate over the predicted entities</span>
<span class="token keyword">for</span> ent <span class="token keyword">in</span> doc<span class="token punctuation">.</span>ents<span class="token punctuation">:</span>
    <span class="token comment"># Print the entity text and its label</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span>ent<span class="token punctuation">.</span>text<span class="token punctuation">,</span> ent<span class="token punctuation">.</span>label_<span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">Apple ORG
U.K. GPE
$1 billion MONEY
</code></pre>
<h3 id="tip-the-spacy.explain-method">Tip: the spacy.explain method</h3>
<p>A quick tip: To get definitions for the most common tags and labels, you can use the  <code>spacy.explain</code>  helper function.</p>
<p>For example, “GPE” for geopolitical entity isn’t exactly intuitive – but  <code>spacy.explain</code>  can tell you that it refers to countries, cities and states.</p>
<p>The same works for part-of-speech tags and dependency labels.</p>
<pre class=" language-python"><code class="prism  language-python">spacy<span class="token punctuation">.</span>explain<span class="token punctuation">(</span><span class="token string">"GPE"</span><span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">'Countries, cities, states'
</code></pre>
<hr>
<pre class=" language-python"><code class="prism  language-python">spacy<span class="token punctuation">.</span>explain<span class="token punctuation">(</span><span class="token string">"NNP"</span><span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">'noun, proper singular'
</code></pre>
<hr>
<pre class=" language-python"><code class="prism  language-python">spacy<span class="token punctuation">.</span>explain<span class="token punctuation">(</span><span class="token string">"dobj"</span><span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">'direct object'
</code></pre>
<h2 id="rule-based-matching">Rule-based matching</h2>
<p><strong>Why not just regular expressions?</strong></p>
<p>Compared to regular expressions, the matcher works with  <code>Doc</code>  and  <code>Token</code>  objects instead of only strings.</p>
<p>It’s also more flexible: you can search for texts but also other lexical attributes.</p>
<p>You can even write rules that use a model’s predictions.</p>
<p>For example, find the word “duck” only if it’s a verb, not a noun.</p>
<h3 id="match-patterns">Match patterns</h3>
<p>Match patterns are lists of dictionaries. Each dictionary describes one token. The keys are the names of token attributes, mapped to their expected values.</p>
<blockquote>
<p>Lists of dictionaries, one per token</p>
</blockquote>
<p>In this example, we’re looking for two tokens with the text “iPhone” and “X”.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token punctuation">[</span><span class="token punctuation">{</span><span class="token string">"TEXT"</span><span class="token punctuation">:</span> <span class="token string">"iPhone"</span><span class="token punctuation">}</span><span class="token punctuation">,</span> <span class="token punctuation">{</span><span class="token string">"TEXT"</span><span class="token punctuation">:</span> <span class="token string">"X"</span><span class="token punctuation">}</span><span class="token punctuation">]</span>
</code></pre>
<p>We can also match on other token attributes. Here, we’re looking for two tokens whose lowercase forms equal “iphone” and “x”.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token punctuation">[</span><span class="token punctuation">{</span><span class="token string">"LOWER"</span><span class="token punctuation">:</span> <span class="token string">"iphone"</span><span class="token punctuation">}</span><span class="token punctuation">,</span> <span class="token punctuation">{</span><span class="token string">"LOWER"</span><span class="token punctuation">:</span> <span class="token string">"x"</span><span class="token punctuation">}</span><span class="token punctuation">]</span>
</code></pre>
<p>We can even write patterns using attributes predicted by a model. Here, we’re matching a token with the lemma “buy”, plus a noun. The lemma is the base form, so this pattern would match phrases like “buying milk” or “bought flowers”.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token punctuation">[</span><span class="token punctuation">{</span><span class="token string">"LEMMA"</span><span class="token punctuation">:</span> <span class="token string">"buy"</span><span class="token punctuation">}</span><span class="token punctuation">,</span> <span class="token punctuation">{</span><span class="token string">"POS"</span><span class="token punctuation">:</span> <span class="token string">"NOUN"</span><span class="token punctuation">}</span><span class="token punctuation">]</span>
</code></pre>
<h3 id="using-the-matcher">Using the Matcher</h3>
<p>To use a pattern, we first <em><strong>import the matcher</strong></em> from  <code>spacy.matcher</code>.</p>
<p>We also load a pipeline and create the  <code>nlp</code>  object.</p>
<p>The matcher is <em><strong>initialized with the shared vocabulary</strong></em>,  <code>nlp.vocab</code>. You’ll learn more about this later – for now, just remember to always pass it in.</p>
<p>The  <code>matcher.add</code>  method lets you <em><strong>add a pattern</strong></em>. The <mark>first argument is a unique ID</mark> to identify which pattern was matched. The <mark>second argument is a list of patterns</mark>.</p>
<p>To match the pattern on a text, we can call the matcher on any doc.</p>
<p>This will return the matches.</p>
<p>When you call the matcher on a doc, it returns a list of tuples.</p>
<p>Each tuple consists of three values: the <em><strong>match ID</strong></em>, the <em><strong>start index</strong></em> and the <em><strong>end index</strong></em> of the matched span.</p>
<p>This means we can iterate over the matches and create a  <code>Span</code>  object: a slice of the doc at the start and end index.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">import</span> spacy
<span class="token comment"># Import the Matcher</span>
<span class="token keyword">from</span> spacy<span class="token punctuation">.</span>matcher <span class="token keyword">import</span> Matcher
<span class="token comment"># Load a pipeline and create the nlp object</span>
nlp <span class="token operator">=</span> spacy<span class="token punctuation">.</span>load<span class="token punctuation">(</span><span class="token string">"en_core_web_sm"</span><span class="token punctuation">)</span>
<span class="token comment"># Initialize the matcher with the shared vocab</span>
matcher <span class="token operator">=</span> Matcher<span class="token punctuation">(</span>nlp<span class="token punctuation">.</span>vocab<span class="token punctuation">)</span>
<span class="token comment"># Add the pattern to the matcher</span>
pattern <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">{</span><span class="token string">"TEXT"</span><span class="token punctuation">:</span> <span class="token string">"iPhone"</span><span class="token punctuation">}</span><span class="token punctuation">,</span> <span class="token punctuation">{</span><span class="token string">"TEXT"</span><span class="token punctuation">:</span> <span class="token string">"X"</span><span class="token punctuation">}</span><span class="token punctuation">]</span>
matcher<span class="token punctuation">.</span>add<span class="token punctuation">(</span><span class="token string">"IPHONE_PATTERN"</span><span class="token punctuation">,</span> <span class="token punctuation">[</span>pattern<span class="token punctuation">]</span><span class="token punctuation">)</span>
<span class="token comment"># Process some text</span>
doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"Upcoming iPhone X release date leaked"</span><span class="token punctuation">)</span>
<span class="token comment"># Call the matcher on the doc</span>
matches <span class="token operator">=</span> matcher<span class="token punctuation">(</span>doc<span class="token punctuation">)</span>
<span class="token comment"># Iterate over the matches  </span>
<span class="token keyword">for</span> match_id<span class="token punctuation">,</span> start<span class="token punctuation">,</span> end <span class="token keyword">in</span> matches<span class="token punctuation">:</span>  
	<span class="token comment"># Get the matched span </span>
	matched_span <span class="token operator">=</span> doc<span class="token punctuation">[</span>start<span class="token punctuation">:</span>end<span class="token punctuation">]</span>  
	<span class="token keyword">print</span><span class="token punctuation">(</span>matched_span<span class="token punctuation">.</span>text<span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">iPhone X
</code></pre>
<h3 id="matching-lexical-attributes">Matching lexical attributes</h3>
<p>Here’s an example of a more complex pattern using lexical attributes.</p>
<p>We’re looking for five tokens:</p>
<p>A token consisting of only digits.</p>
<p>Three case-insensitive tokens for “fifa”, “world” and “cup”.</p>
<p>And a token that consists of punctuation.</p>
<p>The pattern matches the tokens “2018 FIFA World Cup:”.</p>
<pre class=" language-python"><code class="prism  language-python">pattern <span class="token operator">=</span> <span class="token punctuation">[</span>
    <span class="token punctuation">{</span><span class="token string">"IS_DIGIT"</span><span class="token punctuation">:</span> <span class="token boolean">True</span><span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token punctuation">{</span><span class="token string">"LOWER"</span><span class="token punctuation">:</span> <span class="token string">"fifa"</span><span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token punctuation">{</span><span class="token string">"LOWER"</span><span class="token punctuation">:</span> <span class="token string">"world"</span><span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token punctuation">{</span><span class="token string">"LOWER"</span><span class="token punctuation">:</span> <span class="token string">"cup"</span><span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token punctuation">{</span><span class="token string">"IS_PUNCT"</span><span class="token punctuation">:</span> <span class="token boolean">True</span><span class="token punctuation">}</span>
<span class="token punctuation">]</span>
</code></pre>
<pre class=" language-python"><code class="prism  language-python">doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"2018 FIFA World Cup: France won!"</span><span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">2018 FIFA World Cup:
</code></pre>
<h3 id="matching-other-token-attributes">Matching other token attributes</h3>
<p>In this example, we’re looking for two tokens:</p>
<p>A verb with the lemma “love”, followed by a noun.</p>
<p>This pattern will match “loved dogs” and “love cats”</p>
<pre class=" language-python"><code class="prism  language-python">pattern <span class="token operator">=</span> <span class="token punctuation">[</span>
    <span class="token punctuation">{</span><span class="token string">"LEMMA"</span><span class="token punctuation">:</span> <span class="token string">"love"</span><span class="token punctuation">,</span> <span class="token string">"POS"</span><span class="token punctuation">:</span> <span class="token string">"VERB"</span><span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token punctuation">{</span><span class="token string">"POS"</span><span class="token punctuation">:</span> <span class="token string">"NOUN"</span><span class="token punctuation">}</span>
<span class="token punctuation">]</span>
</code></pre>
<pre class=" language-python"><code class="prism  language-python">doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"I loved dogs but now I love cats more."</span><span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">loved dogs
love cats
</code></pre>
<h3 id="using-operators-and-quantifiers">Using operators and quantifiers</h3>
<p>Operators and quantifiers let you define how often a token should be matched. They can be added using the “OP” key.</p>
<p>Here, the “?” operator makes the determiner token optional, so it will match a token with the lemma “buy”, an optional article and a noun.</p>
<pre class=" language-python"><code class="prism  language-python">pattern <span class="token operator">=</span> <span class="token punctuation">[</span>
    <span class="token punctuation">{</span><span class="token string">"LEMMA"</span><span class="token punctuation">:</span> <span class="token string">"buy"</span><span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token punctuation">{</span><span class="token string">"POS"</span><span class="token punctuation">:</span> <span class="token string">"DET"</span><span class="token punctuation">,</span> <span class="token string">"OP"</span><span class="token punctuation">:</span> <span class="token string">"?"</span><span class="token punctuation">}</span><span class="token punctuation">,</span>  <span class="token comment"># optional: match 0 or 1 times</span>
    <span class="token punctuation">{</span><span class="token string">"POS"</span><span class="token punctuation">:</span> <span class="token string">"NOUN"</span><span class="token punctuation">}</span>
<span class="token punctuation">]</span>
</code></pre>
<pre class=" language-python"><code class="prism  language-python">doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"I bought a smartphone. Now I'm buying apps."</span><span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">bought a smartphone
buying apps
</code></pre>
<p>“OP” can have one of four values:</p>
<ul>
<li><code>{"OP": "!"}</code> negates the token, so it’s matched 0 times.</li>
<li><code>{"OP": "?"}</code> makes the token optional, and matches it 0 or 1 times.</li>
<li><code>{"OP": "+"}</code> matches a token 1 or more times.</li>
<li><code>{"OP": "*"}</code> matches 0 or more times.</li>
</ul>
<p>Operators can make your patterns a lot more powerful, but they also add more complexity – so use them wisely.</p>
<h1 id="chapter-2-large-scale-data-analysis-with-spacy"><a href="https://course.spacy.io/en/chapter2">Chapter 2: Large-scale data analysis with spaCy</a></h1>
<h2 id="data-structures-vocab-lexemes-and-stringstore">Data Structures: Vocab, Lexemes and StringStore</h2>
<h3 id="shared-vocab-and-string-store">Shared vocab and string store</h3>
<p>spaCy stores all shared data in a vocabulary, the Vocab.</p>
<p>This includes words, but also the labels schemes for tags and entities.</p>
<p>To save memory, <strong>all strings are encoded to hash IDs</strong>. If a word occurs more than once, we don’t need to save it every time.</p>
<p>Instead, spaCy uses a hash function to generate an ID and <strong>stores the string only once</strong> in the string store. The string store is available as  <code>nlp.vocab.strings</code>.</p>
<p>It’s a <strong>lookup table</strong> that works in both directions. You can look up a string and get its hash, and look up a hash to get its string value. Internally, spaCy only communicates in hash IDs.</p>
<pre class=" language-python"><code class="prism  language-python">nlp<span class="token punctuation">.</span>vocab<span class="token punctuation">.</span>strings<span class="token punctuation">.</span>add<span class="token punctuation">(</span><span class="token string">"coffee"</span><span class="token punctuation">)</span>
coffee_hash <span class="token operator">=</span> nlp<span class="token punctuation">.</span>vocab<span class="token punctuation">.</span>strings<span class="token punctuation">[</span><span class="token string">"coffee"</span><span class="token punctuation">]</span>
coffee_string <span class="token operator">=</span> nlp<span class="token punctuation">.</span>vocab<span class="token punctuation">.</span>strings<span class="token punctuation">[</span>coffee_hash<span class="token punctuation">]</span>
</code></pre>
<p>Hash IDs <strong>can’t be reversed</strong>, though. If a word is not in the vocabulary, there’s no way to get its string. That’s why we always need to pass around the shared vocab.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Raises an error if we haven't seen the string before</span>
string <span class="token operator">=</span> nlp<span class="token punctuation">.</span>vocab<span class="token punctuation">.</span>strings<span class="token punctuation">[</span><span class="token number">3197928453018144401</span><span class="token punctuation">]</span>
</code></pre>
<p>To get the hash for a string, we can look it up in  <code>nlp.vocab.strings</code>.</p>
<p>To get the string representation of a hash, we can look up the hash.</p>
<pre class=" language-python"><code class="prism  language-python">doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"I love coffee"</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"hash value:"</span><span class="token punctuation">,</span> nlp<span class="token punctuation">.</span>vocab<span class="token punctuation">.</span>strings<span class="token punctuation">[</span><span class="token string">"coffee"</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"string value:"</span><span class="token punctuation">,</span> nlp<span class="token punctuation">.</span>vocab<span class="token punctuation">.</span>strings<span class="token punctuation">[</span><span class="token number">3197928453018144401</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">hash value: 3197928453018144401
string value: coffee
</code></pre>
<p>A  <code>Doc</code>  object also exposes its vocab and strings.</p>
<pre class=" language-python"><code class="prism  language-python">doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"I love coffee"</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"hash value:"</span><span class="token punctuation">,</span> doc<span class="token punctuation">.</span>vocab<span class="token punctuation">.</span>strings<span class="token punctuation">[</span><span class="token string">"coffee"</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">hash value: 3197928453018144401
</code></pre>
<h3 id="lexemes-entries-in-the-vocabulary">Lexemes: entries in the vocabulary</h3>
<p>Lexemes are <em><strong>context-independent entries</strong></em> in the vocabulary.</p>
<p>You can get a lexeme by looking up a string or a hash ID in the vocab.</p>
<p>Lexemes expose attributes, just like tokens.</p>
<p>They hold context-independent information about a word, like the text, or whether the word consists of alphabetic characters.</p>
<p>Lexemes don’t have part-of-speech tags, dependencies or entity labels. Those depend on the context.</p>
<pre class=" language-python"><code class="prism  language-python">doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"I love coffee"</span><span class="token punctuation">)</span>
lexeme <span class="token operator">=</span> nlp<span class="token punctuation">.</span>vocab<span class="token punctuation">[</span><span class="token string">"coffee"</span><span class="token punctuation">]</span>

<span class="token comment"># Print the lexical attributes</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>lexeme<span class="token punctuation">.</span>text<span class="token punctuation">,</span> lexeme<span class="token punctuation">.</span>orth<span class="token punctuation">,</span> lexeme<span class="token punctuation">.</span>is_alpha<span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">coffee 3197928453018144401 True
</code></pre>
<p><img src="https://course.spacy.io/vocab_stringstore.png" alt="Illustration of the words 'I', 'love' and 'coffee' across the Doc, Vocab and StringStore"></p>
<h1 id="chapter-3-processing-pipelines"><a href="https://course.spacy.io/en/chapter3">Chapter 3: Processing Pipelines</a></h1>
<h1 id="chapter-4-training-a-neural-network-model"><a href="https://course.spacy.io/en/chapter4">Chapter 4: Training a neural network model</a></h1>

