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
<h2 id="data-structures-doc-span-and-token">Data Structures: Doc, Span and Token</h2>
<h3 id="the-doc-object-1">The Doc object</h3>
<p>The  <code>Doc</code>  is one of the central data structures in spaCy. It’s created automatically when you process a text with the  <code>nlp</code>  object. But you can also <strong>instantiate the class manually</strong>.</p>
<p>After creating the  <code>nlp</code>  object, we can import the  <code>Doc</code>  class from  <code>spacy.tokens</code>.</p>
<p>Here we’re creating a doc from three words. The spaces are a list of boolean values indicating whether the word is followed by a space. Every token includes that information – even the last one!</p>
<p>The  <code>Doc</code>  class takes three arguments: the <strong>shared vocab</strong>, the <em><strong>words</strong></em> and the <em><strong>spaces</strong></em>.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Create an nlp object</span>
<span class="token keyword">import</span> spacy
nlp <span class="token operator">=</span> spacy<span class="token punctuation">.</span>blank<span class="token punctuation">(</span><span class="token string">"en"</span><span class="token punctuation">)</span>
<span class="token comment"># Import the Doc class</span>
<span class="token keyword">from</span> spacy<span class="token punctuation">.</span>tokens <span class="token keyword">import</span> Doc
<span class="token comment"># The words and spaces to create the doc from</span>
words <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token string">"Hello"</span><span class="token punctuation">,</span> <span class="token string">"world"</span><span class="token punctuation">,</span> <span class="token string">"!"</span><span class="token punctuation">]</span>
spaces <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token boolean">True</span><span class="token punctuation">,</span> <span class="token boolean">False</span><span class="token punctuation">,</span> <span class="token boolean">False</span><span class="token punctuation">]</span>
<span class="token comment"># Create a doc manually</span>
doc <span class="token operator">=</span> Doc<span class="token punctuation">(</span>nlp<span class="token punctuation">.</span>vocab<span class="token punctuation">,</span> words<span class="token operator">=</span>words<span class="token punctuation">,</span> spaces<span class="token operator">=</span>spaces<span class="token punctuation">)</span>
</code></pre>
<h3 id="the-span-object-1">The Span object</h3>
<p>A <code>Span</code> is a slice of a doc consisting of one or more tokens. The <code>Span</code> takes at least three arguments: the doc it refers to, and the start and end index of the span. Remember that the end index is exclusive!</p>
<p><img src="https://course.spacy.io/span_indices.png" alt="Illustration of a Span object within a Doc with token indices"></p>
<p>To create a  <code>Span</code>  manually, we can also import the class from  <code>spacy.tokens</code>. We can then instantiate it with the doc and the span’s start and end index, and an <em><strong>optional label argument</strong></em>.</p>
<p>The  <code>doc.ents</code>  are writable, so we can <em><strong>add entities manually</strong></em> by overwriting it with a list of spans.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Import the Doc and Span classes</span>
<span class="token keyword">from</span> spacy<span class="token punctuation">.</span>tokens <span class="token keyword">import</span> Doc<span class="token punctuation">,</span> Span
<span class="token comment"># The words and spaces to create the doc from</span>
words <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token string">"Hello"</span><span class="token punctuation">,</span> <span class="token string">"world"</span><span class="token punctuation">,</span> <span class="token string">"!"</span><span class="token punctuation">]</span>
spaces <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token boolean">True</span><span class="token punctuation">,</span> <span class="token boolean">False</span><span class="token punctuation">,</span> <span class="token boolean">False</span><span class="token punctuation">]</span>
<span class="token comment"># Create a doc manually</span>
doc <span class="token operator">=</span> Doc<span class="token punctuation">(</span>nlp<span class="token punctuation">.</span>vocab<span class="token punctuation">,</span> words<span class="token operator">=</span>words<span class="token punctuation">,</span> spaces<span class="token operator">=</span>spaces<span class="token punctuation">)</span>
<span class="token comment"># Create a span manually</span>
span <span class="token operator">=</span> Span<span class="token punctuation">(</span>doc<span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">)</span>
<span class="token comment"># Create a span with a label</span>
span_with_label <span class="token operator">=</span> Span<span class="token punctuation">(</span>doc<span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> label<span class="token operator">=</span><span class="token string">"GREETING"</span><span class="token punctuation">)</span>
<span class="token comment"># Add span to the doc.ents</span>
doc<span class="token punctuation">.</span>ents <span class="token operator">=</span> <span class="token punctuation">[</span>span_with_label<span class="token punctuation">]</span>
</code></pre>
<h3 id="best-practices">Best practices</h3>
<p>A few tips and tricks before we get started:</p>
<p>The  <code>Doc</code>  and  <code>Span</code>  are very powerful and optimized for performance. They give you access to all references and relationships of the words and sentences.</p>
<p>If your application needs to output strings, make sure to <em><strong>convert the doc as late as possible</strong></em>. If you do it too early, you’ll lose all relationships between the tokens.</p>
<p>To keep things consistent, <em><strong>try to use built-in token attributes wherever possible</strong></em>. For example,  <code>token.i</code>  for the token index.</p>
<p>Also, don’t forget to <mark>always pass in the shared vocab!</mark></p>
<h2 id="word-vectors-and-semantic-similarity">Word vectors and semantic similarity</h2>
<h3 id="comparing-semantic-similarity">Comparing semantic similarity</h3>
<p>spaCy can compare two objects and predict <em><strong>how similar they are</strong></em> – for example, documents, spans or single tokens.</p>
<p>The  <code>Doc</code>,  <code>Token</code>  and  <code>Span</code>  objects have a  <code>.similarity</code>  method that takes another object and <mark>returns a floating point number between 0 and 1</mark>, indicating how similar they are.</p>
<p>One thing that’s very important: In order to use similarity, <strong>you need a larger spaCy pipeline that has word vectors included</strong>.</p>
<p>For example, the medium or large English pipeline – but  <em>not</em>  the small one. So if you want to use vectors, always <mark>go with a pipeline that ends in “md” or “lg”</mark>. You can find more details on this in the  <a href="https://spacy.io/models">documentation</a>.</p>
<h3 id="similarity-examples">Similarity examples</h3>
<p>Here’s an example. Let’s say we want to find out whether two documents are similar.</p>
<p>First, we load the medium English pipeline, “en_core_web_md”.</p>
<p>We can then create two doc objects and use the first doc’s  <code>similarity</code>  method to compare it to the second.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Load a larger pipeline with vectors</span>
nlp <span class="token operator">=</span> spacy<span class="token punctuation">.</span>load<span class="token punctuation">(</span><span class="token string">"en_core_web_md"</span><span class="token punctuation">)</span>
<span class="token comment"># Compare two documents</span>
doc1 <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"I like fast food"</span><span class="token punctuation">)</span>
doc2 <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"I like pizza"</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>doc1<span class="token punctuation">.</span>similarity<span class="token punctuation">(</span>doc2<span class="token punctuation">)</span><span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">0.8627204117787385
</code></pre>
<p>Here, a fairly high similarity score of 0.86 is predicted for “I like fast food” and “I like pizza”.</p>
<hr>
<p>The same works for tokens.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Compare two tokens</span>
doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"I like pizza and pasta"</span><span class="token punctuation">)</span>
token1 <span class="token operator">=</span> doc<span class="token punctuation">[</span><span class="token number">2</span><span class="token punctuation">]</span>
token2 <span class="token operator">=</span> doc<span class="token punctuation">[</span><span class="token number">4</span><span class="token punctuation">]</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>token1<span class="token punctuation">.</span>similarity<span class="token punctuation">(</span>token2<span class="token punctuation">)</span><span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">0.7369546
</code></pre>
<p>According to the word vectors, the tokens “pizza” and “pasta” are kind of similar, and receive a score of 0.7.</p>
<hr>
<p>You can also use the  <code>similarity</code>  methods to compare different types of objects.</p>
<p>For example, a document and a token.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Compare a document with a token</span>
doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"I like pizza"</span><span class="token punctuation">)</span>
token <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"soap"</span><span class="token punctuation">)</span><span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">]</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>doc<span class="token punctuation">.</span>similarity<span class="token punctuation">(</span>token<span class="token punctuation">)</span><span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">0.32531983166759537
</code></pre>
<p>Here, the similarity score is pretty low and the two objects are considered fairly dissimilar.</p>
<hr>
<p>Here’s another example comparing a span – “pizza and pasta” – to a document about McDonalds.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Compare a span with a document</span>
span <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"I like pizza and pasta"</span><span class="token punctuation">)</span><span class="token punctuation">[</span><span class="token number">2</span><span class="token punctuation">:</span><span class="token number">5</span><span class="token punctuation">]</span>
doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"McDonalds sells burgers"</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>span<span class="token punctuation">.</span>similarity<span class="token punctuation">(</span>doc<span class="token punctuation">)</span><span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">0.619909235817623
</code></pre>
<p>The score returned here is 0.61, so it’s determined to be kind of similar.</p>
<h3 id="how-does-spacy-predict-similarity">How does spaCy predict similarity?</h3>
<p>But how does spaCy do this under the hood?</p>
<p>Similarity is determined using <em><strong>word vectors</strong></em>, multi-dimensional representations of meanings of words.</p>
<p>You might have heard of <a href="https://en.wikipedia.org/wiki/Word2vec"><em><strong>Word2Vec</strong></em></a>, which is an algorithm that’s often used to train word vectors from raw text.</p>
<p>Vectors can be added to spaCy’s pipelines.</p>
<p>By default, the similarity returned by spaCy is the <em><strong>cosine similarity between two vectors</strong></em> – but this can be adjusted if necessary.</p>
<p>Vectors for objects consisting of several tokens, like the  <code>Doc</code>  and  <code>Span</code>, <em><strong>default to the average of their token vectors</strong></em>.</p>
<p>That’s also why you usually get more value out of shorter phrases with fewer irrelevant words.</p>
<h3 id="word-vectors-in-spacy">Word vectors in spaCy</h3>
<p>To give you an idea of what those vectors look like, here’s an example.</p>
<p>First, we load the medium pipeline again, which ships with word vectors.</p>
<p>Next, we can process a text and look up a token’s vector using the  <code>.vector</code>  attribute.</p>
<p>The result is a 300-dimensional vector of the word “banana”.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Load a larger pipeline with vectors</span>
nlp <span class="token operator">=</span> spacy<span class="token punctuation">.</span>load<span class="token punctuation">(</span><span class="token string">"en_core_web_md"</span><span class="token punctuation">)</span>
doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"I have a banana"</span><span class="token punctuation">)</span>
<span class="token comment"># Access the vector via the token.vector attribute</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>doc<span class="token punctuation">[</span><span class="token number">3</span><span class="token punctuation">]</span><span class="token punctuation">.</span>vector<span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out"> [2.02280000e-01,  -7.66180009e-02,   3.70319992e-01,
  3.28450017e-02,  -4.19569999e-01,   7.20689967e-02,
 -3.74760002e-01,   5.74599989e-02,  -1.24009997e-02,
  5.29489994e-01,  -5.23800015e-01,  -1.97710007e-01,
 -3.41470003e-01,   5.33169985e-01,  -2.53309999e-02,
  1.73800007e-01,   1.67720005e-01,   8.39839995e-01,
  5.51070012e-02,   1.05470002e-01,   3.78719985e-01,
  2.42750004e-01,   1.47449998e-02,   5.59509993e-01,
  1.25210002e-01,  -6.75960004e-01,   3.58420014e-01,
 -4.00279984e-02,   9.59490016e-02,  -5.06900012e-01,
 -8.53179991e-02,   1.79800004e-01,   3.38669986e-01,
  ...
</code></pre>
<h3 id="similarity-depends-on-the-application-context">Similarity depends on the application context</h3>
<p>Predicting similarity can be useful for many types of applications. For example, to recommend a user similar texts based on the ones they have read. It can also be helpful to flag duplicate content, like posts on an online platform.</p>
<p>However, it’s important to keep in mind that there’s no objective definition of what’s similar and what isn’t. <em><strong>It always depends on the context and what your application needs to do</strong></em>.</p>
<p>Here’s an example: spaCy’s default word vectors assign a very high similarity score to “I like cats” and “I hate cats”. This makes sense, because both texts express sentiment about cats. But in a different application context, you might want to consider the phrases as very  <em>dissimilar</em>, because they talk about opposite sentiments.</p>
<pre class=" language-python"><code class="prism  language-python">doc1 <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"I like cats"</span><span class="token punctuation">)</span>
doc2 <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"I hate cats"</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>doc1<span class="token punctuation">.</span>similarity<span class="token punctuation">(</span>doc2<span class="token punctuation">)</span><span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">0.9501447503553421
</code></pre>
<h2 id="combining-predictions-and-rules">Combining predictions and rules</h2>
<h3 id="statistical-predictions-vs.-rules">Statistical predictions vs. rules</h3>
<p>Statistical models are useful if your application needs to be able to <em><strong>generalize based on a few examples</strong></em>.</p>
<p>For instance, detecting product or person names usually benefits from a trained model. Instead of providing a list of all person names ever, your application will be able to predict whether a span of tokens is a person name. Similarly, you can predict dependency labels to find subject/object relationships.</p>
<p>To do this, you would use spaCy’s <mark>entity recognizer</mark>, <mark>dependency parser</mark> or <mark>part-of-speech tagger</mark>.</p>
<p>Rule-based approaches on the other hand come in handy if <em><strong>there’s a more or less finite number of instances you want to find</strong></em>. For example, all countries or cities of the world, drug names or even dog breeds.</p>
<p>In spaCy, you can achieve this with <mark>custom tokenization rules</mark>, as well as the <mark>matcher</mark> and <mark>phrase matcher</mark>.</p>
<h3 id="recap-rule-based-matching">Recap: Rule-based Matching</h3>
<p>In the last chapter, you learned how to use spaCy’s rule-based matcher to find complex patterns in your texts. Here’s a quick recap.</p>
<p>The matcher is initialized with the shared vocabulary – usually  <code>nlp.vocab</code>.</p>
<p>Patterns are lists of dictionaries, and each dictionary describes one token and its attributes. Patterns can be added to the matcher using the  <code>matcher.add</code>  method.</p>
<p>Operators let you specify how often to match a token. For example, “+” will match one or more times.</p>
<p>Calling the matcher on a doc object will return a list of the matches. Each match is a tuple consisting of an ID, and the start and end token index in the document.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Initialize with the shared vocab</span>
<span class="token keyword">from</span> spacy<span class="token punctuation">.</span>matcher <span class="token keyword">import</span> Matcher
matcher <span class="token operator">=</span> Matcher<span class="token punctuation">(</span>nlp<span class="token punctuation">.</span>vocab<span class="token punctuation">)</span>
<span class="token comment"># Patterns are lists of dictionaries describing the tokens</span>
pattern <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">{</span><span class="token string">"LEMMA"</span><span class="token punctuation">:</span> <span class="token string">"love"</span><span class="token punctuation">,</span> <span class="token string">"POS"</span><span class="token punctuation">:</span> <span class="token string">"VERB"</span><span class="token punctuation">}</span><span class="token punctuation">,</span> <span class="token punctuation">{</span><span class="token string">"LOWER"</span><span class="token punctuation">:</span> <span class="token string">"cats"</span><span class="token punctuation">}</span><span class="token punctuation">]</span>
matcher<span class="token punctuation">.</span>add<span class="token punctuation">(</span><span class="token string">"LOVE_CATS"</span><span class="token punctuation">,</span> <span class="token punctuation">[</span>pattern<span class="token punctuation">]</span><span class="token punctuation">)</span>
<span class="token comment"># Operators can specify how often a token should be matched</span>
pattern <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">{</span><span class="token string">"TEXT"</span><span class="token punctuation">:</span> <span class="token string">"very"</span><span class="token punctuation">,</span> <span class="token string">"OP"</span><span class="token punctuation">:</span> <span class="token string">"+"</span><span class="token punctuation">}</span><span class="token punctuation">,</span> <span class="token punctuation">{</span><span class="token string">"TEXT"</span><span class="token punctuation">:</span> <span class="token string">"happy"</span><span class="token punctuation">}</span><span class="token punctuation">]</span>
matcher<span class="token punctuation">.</span>add<span class="token punctuation">(</span><span class="token string">"VERY_HAPPY"</span><span class="token punctuation">,</span> <span class="token punctuation">[</span>pattern<span class="token punctuation">]</span><span class="token punctuation">)</span>
<span class="token comment"># Calling matcher on doc returns list of (match_id, start, end) tuples</span>
doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"I love cats and I'm very very happy"</span><span class="token punctuation">)</span>
matches <span class="token operator">=</span> matcher<span class="token punctuation">(</span>doc<span class="token punctuation">)</span>
</code></pre>
<h3 id="adding-statistical-predictions">Adding statistical predictions</h3>
<p>Here’s an example of a matcher rule for “golden retriever”.</p>
<p>If we iterate over the matches returned by the matcher, we can get the match ID and the start and end index of the matched span. We can then find out more about it.  <code>Span</code>  objects give us access to the original document and all other token attributes and linguistic features predicted by a model.</p>
<p>For example, we can get the span’s root token. If the span consists of more than one token, this will be the token that decides the category of the phrase. For example, the root of “Golden Retriever” is “Retriever”. We can also find the head token of the root. This is the syntactic “parent” that governs the phrase – in this case, the verb “have”.</p>
<p>Finally, we can look at the previous token and its attributes. In this case, it’s a determiner, the article “a”.</p>
<pre class=" language-python"><code class="prism  language-python">matcher <span class="token operator">=</span> Matcher<span class="token punctuation">(</span>nlp<span class="token punctuation">.</span>vocab<span class="token punctuation">)</span>
matcher<span class="token punctuation">.</span>add<span class="token punctuation">(</span><span class="token string">"DOG"</span><span class="token punctuation">,</span> <span class="token punctuation">[</span><span class="token punctuation">[</span><span class="token punctuation">{</span><span class="token string">"LOWER"</span><span class="token punctuation">:</span> <span class="token string">"golden"</span><span class="token punctuation">}</span><span class="token punctuation">,</span> <span class="token punctuation">{</span><span class="token string">"LOWER"</span><span class="token punctuation">:</span> <span class="token string">"retriever"</span><span class="token punctuation">}</span><span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"I have a Golden Retriever"</span><span class="token punctuation">)</span>
<span class="token keyword">for</span> match_id<span class="token punctuation">,</span> start<span class="token punctuation">,</span> end <span class="token keyword">in</span> matcher<span class="token punctuation">(</span>doc<span class="token punctuation">)</span><span class="token punctuation">:</span>
    span <span class="token operator">=</span> doc<span class="token punctuation">[</span>start<span class="token punctuation">:</span>end<span class="token punctuation">]</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Matched span:"</span><span class="token punctuation">,</span> span<span class="token punctuation">.</span>text<span class="token punctuation">)</span>
    <span class="token comment"># Get the span's root token and root head token</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Root token:"</span><span class="token punctuation">,</span> span<span class="token punctuation">.</span>root<span class="token punctuation">.</span>text<span class="token punctuation">)</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Root head token:"</span><span class="token punctuation">,</span> span<span class="token punctuation">.</span>root<span class="token punctuation">.</span>head<span class="token punctuation">.</span>text<span class="token punctuation">)</span>
    <span class="token comment"># Get the previous token and its POS tag</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Previous token:"</span><span class="token punctuation">,</span> doc<span class="token punctuation">[</span>start <span class="token operator">-</span> <span class="token number">1</span><span class="token punctuation">]</span><span class="token punctuation">.</span>text<span class="token punctuation">,</span> doc<span class="token punctuation">[</span>start <span class="token operator">-</span> <span class="token number">1</span><span class="token punctuation">]</span><span class="token punctuation">.</span>pos_<span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">Matched span: Golden Retriever
Root token: Retriever
Root head token: have
Previous token: a DET
</code></pre>
<h3 id="efficient-phrase-matching">Efficient phrase matching</h3>
<p>The phrase matcher is another helpful tool to find sequences of words in your data.</p>
<p>It performs a keyword search on the document, but instead of only finding strings, it <em><strong>gives you direct access to the tokens in context</strong></em>.</p>
<p>It takes  <code>Doc</code>  objects as patterns.</p>
<p>It’s also really fast.</p>
<p>This makes it very useful for matching large dictionaries and word lists on large volumes of text.</p>
<p>Here’s an example.</p>
<p>The phrase matcher can be imported from  <code>spacy.matcher</code>  and follows the same API as the regular matcher.</p>
<p>Instead of a list of dictionaries, we pass in a  <code>Doc</code>  object as the pattern.</p>
<p>We can then iterate over the matches in the text, which gives us the match ID, and the start and end of the match. This lets us create a  <code>Span</code>  object for the matched tokens “Golden Retriever” to analyze it in context.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">from</span> spacy<span class="token punctuation">.</span>matcher <span class="token keyword">import</span> PhraseMatcher
matcher <span class="token operator">=</span> PhraseMatcher<span class="token punctuation">(</span>nlp<span class="token punctuation">.</span>vocab<span class="token punctuation">)</span>
pattern <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"Golden Retriever"</span><span class="token punctuation">)</span>
matcher<span class="token punctuation">.</span>add<span class="token punctuation">(</span><span class="token string">"DOG"</span><span class="token punctuation">,</span> <span class="token punctuation">[</span>pattern<span class="token punctuation">]</span><span class="token punctuation">)</span>
doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"I have a Golden Retriever"</span><span class="token punctuation">)</span>
<span class="token comment"># Iterate over the matches</span>
<span class="token keyword">for</span> match_id<span class="token punctuation">,</span> start<span class="token punctuation">,</span> end <span class="token keyword">in</span> matcher<span class="token punctuation">(</span>doc<span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token comment"># Get the matched span</span>
    span <span class="token operator">=</span> doc<span class="token punctuation">[</span>start<span class="token punctuation">:</span>end<span class="token punctuation">]</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Matched span:"</span><span class="token punctuation">,</span> span<span class="token punctuation">.</span>text<span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">Matched span: Golden Retriever
</code></pre>
<h1 id="chapter-3-processing-pipelines"><a href="https://course.spacy.io/en/chapter3">Chapter 3: Processing Pipelines</a></h1>
<h2 id="processing-pipelines">Processing Pipelines</h2>
<h3 id="what-happens-when-you-call-nlp">What happens when you call nlp?</h3>
<p>You’ve already written this plenty of times by now: pass a string of text to the  <code>nlp</code>  object, and receive a  <code>Doc</code>  object.</p>
<p>But what does the  <code>nlp</code>  object  <em>actually</em>  do?</p>
<p><img src="https://course.spacy.io/pipeline.png" alt="Illustration of the spaCy pipeline transforming a text into a processed Doc"></p>
<p>First, the tokenizer is applied to turn the string of text into a  <code>Doc</code>  object. Next, a series of pipeline components is applied to the doc in order. In this case, the tagger, then the parser, then the entity recognizer. Finally, the processed doc is returned, so you can work with it.</p>
<h3 id="built-in-pipeline-components">Built-in pipeline components</h3>
<p>spaCy ships with a variety of built-in pipeline components. Here are some of the most common ones that you’ll want to use in your projects.</p>
<p>The <strong>part-of-speech tagger</strong> sets the  <code>token.tag</code>  and  <code>token.pos</code>  attributes.</p>
<p>The <strong>dependency parser</strong> adds the  <code>token.dep</code>  and  <code>token.head</code>  attributes and is also responsible for detecting sentences and base noun phrases, also known as noun chunks.</p>
<p>The <strong>named entity recognizer</strong> adds the detected entities to the  <code>doc.ents</code>  property. It also sets entity type attributes on the tokens that indicate if a token is part of an entity or not.</p>
<p>Finally, the <em><strong>text classifier</strong></em> sets category labels that apply to the whole text, and adds them to the  <code>doc.cats</code>  property.</p>
<p>Because text categories are always very specific, <mark>the text classifier is not included in any of the trained pipelines by default</mark>. But you can use it to train your own system.</p>
<h3 id="under-the-hood">Under the hood</h3>
<p>All pipeline packages you can load into spaCy include several files and a  <code>config.cfg</code>.</p>
<p>The config defines things like the language and pipeline. This tells spaCy which components to instantiate and how they should be configured.</p>
<p>The built-in components that make predictions also need binary data. The data is included in the pipeline package and loaded into the component when you load the pipeline.</p>
<h3 id="pipeline-attributes">Pipeline attributes</h3>
<p>To see the names of the pipeline components present in the current nlp object, you can use the  <code>nlp.pipe_names</code>  attribute.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">print</span><span class="token punctuation">(</span>nlp<span class="token punctuation">.</span>pipe_names<span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">['tok2vec', 'tagger', 'parser', 'ner', 'attribute_ruler', 'lemmatizer']
</code></pre>
<hr>
<p>For a list of component name and component function tuples, you can use the  <code>nlp.pipeline</code>  attribute.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">print</span><span class="token punctuation">(</span>nlp<span class="token punctuation">.</span>pipeline<span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">[('tok2vec', &lt;spacy.pipeline.Tok2Vec&gt;),
 ('tagger', &lt;spacy.pipeline.Tagger&gt;),
 ('parser', &lt;spacy.pipeline.DependencyParser&gt;),
 ('ner', &lt;spacy.pipeline.EntityRecognizer&gt;),
 ('attribute_ruler', &lt;spacy.pipeline.AttributeRuler&gt;),
 ('lemmatizer', &lt;spacy.pipeline.Lemmatizer&gt;)]
</code></pre>
<p>The component functions are the functions applied to the doc to process it and set attributes – for example, part-of-speech tags or named entities.</p>
<h2 id="custom-pipeline-components">Custom pipeline components</h2>
<h3 id="why-custom-components">Why custom components?</h3>
<p>After the text is tokenized and a  <code>Doc</code>  object has been created, pipeline components are applied in order. spaCy supports a range of built-in components, but also lets you define your own.</p>
<p>Custom components are executed automatically when you call the  <code>nlp</code>  object on a text.</p>
<p>They’re especially useful for adding your own custom metadata to documents and tokens.</p>
<p>You can also use them to update built-in attributes, like the named entity spans.</p>
<h3 id="anatomy-of-a-component">Anatomy of a component</h3>
<p>Fundamentally, a pipeline component is a function or callable that takes a doc, modifies it and returns it, so it can be processed by the next component in the pipeline.</p>
<p>To tell spaCy where to find your custom component and how it should be called, you can decorate it using the  <code>@Language.component</code>  decorator. Just add it to the line right above the function definition.</p>
<p>Once a component is registered, it can be added to the pipeline using the  <code>nlp.add_pipe</code>  method. The method takes at least one argument: the string name of the component.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">from</span> spacy<span class="token punctuation">.</span>language <span class="token keyword">import</span> Language

@Language<span class="token punctuation">.</span>component<span class="token punctuation">(</span><span class="token string">"custom_component"</span><span class="token punctuation">)</span>
<span class="token keyword">def</span> <span class="token function">custom_component_function</span><span class="token punctuation">(</span>doc<span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token comment"># Do something to the doc here</span>
    <span class="token keyword">return</span> doc

nlp<span class="token punctuation">.</span>add_pipe<span class="token punctuation">(</span><span class="token string">"custom_component"</span><span class="token punctuation">)</span>
</code></pre>
<hr>
<p>To specify  <em>where</em>  to add the component in the pipeline, you can use the following keyword arguments:</p>
<p>Setting  <code>last=True</code>  will add the component last in the pipeline. This is the default behavior.</p>
<p>Setting  <code>first=True</code>  will add the component first in the pipeline, right after the tokenizer.</p>
<p>The  <code>before</code>  and  <code>after</code>  arguments let you define the name of an existing component to add the new component before or after. For example,  <code>before="ner"</code>  will add it before the named entity recognizer.</p>
<p>The other component to add the new component before or after needs to exist, though – otherwise, spaCy will raise an error.</p>
<h3 id="example-a-simple-component">Example: a simple component</h3>
<p>We start off with the small English pipeline.</p>
<p>We then define the component – a function that takes a  <code>Doc</code>  object and returns it.</p>
<p>Let’s do something simple and print the length of the doc that passes through the pipeline.</p>
<p>Don’t forget to return the doc so it can be processed by the next component in the pipeline! The doc created by the tokenizer is passed through all components, so it’s important that they all return the modified doc.</p>
<p>To tell spaCy about the new component, we register it using the  <code>@Language.component</code>  decorator and call it “custom_component”.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Create the nlp object</span>
nlp <span class="token operator">=</span> spacy<span class="token punctuation">.</span>load<span class="token punctuation">(</span><span class="token string">"en_core_web_sm"</span><span class="token punctuation">)</span>

<span class="token comment"># Define a custom component</span>
@Language<span class="token punctuation">.</span>component<span class="token punctuation">(</span><span class="token string">"custom_component"</span><span class="token punctuation">)</span>
<span class="token keyword">def</span> <span class="token function">custom_component_function</span><span class="token punctuation">(</span>doc<span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token comment"># Print the doc's length</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Doc length:"</span><span class="token punctuation">,</span> <span class="token builtin">len</span><span class="token punctuation">(</span>doc<span class="token punctuation">)</span><span class="token punctuation">)</span>
    <span class="token comment"># Return the doc object</span>
    <span class="token keyword">return</span> doc
</code></pre>
<p>We can now add the component to the pipeline. Let’s add it to the very beginning right after the tokenizer by setting  <code>first=True</code>.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Add the component first in the pipeline</span>
nlp<span class="token punctuation">.</span>add_pipe<span class="token punctuation">(</span><span class="token string">"custom_component"</span><span class="token punctuation">,</span> first<span class="token operator">=</span><span class="token boolean">True</span><span class="token punctuation">)</span>
</code></pre>
<p>When we print the pipeline component names, the custom component now shows up at the start. This means it will be applied first when we process a doc.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Print the pipeline component names</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Pipeline:"</span><span class="token punctuation">,</span> nlp<span class="token punctuation">.</span>pipe_names<span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">Pipeline: ['custom_component', 'tok2vec', 'tagger', 'parser', 'ner', 'attribute_ruler', 'lemmatizer']
</code></pre>
<hr>
<p>Now when we process a text using the <code>nlp</code> object, the custom component will be applied to the doc and the length of the document will be printed.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Create the nlp object</span>
nlp <span class="token operator">=</span> spacy<span class="token punctuation">.</span>load<span class="token punctuation">(</span><span class="token string">"en_core_web_sm"</span><span class="token punctuation">)</span>

<span class="token comment"># Define a custom component</span>
@Language<span class="token punctuation">.</span>component<span class="token punctuation">(</span><span class="token string">"custom_component"</span><span class="token punctuation">)</span>
<span class="token keyword">def</span> <span class="token function">custom_component_function</span><span class="token punctuation">(</span>doc<span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token comment"># Print the doc's length</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Doc length:"</span><span class="token punctuation">,</span> <span class="token builtin">len</span><span class="token punctuation">(</span>doc<span class="token punctuation">)</span><span class="token punctuation">)</span>
    <span class="token comment"># Return the doc object</span>
    <span class="token keyword">return</span> doc

<span class="token comment"># Add the component first in the pipeline</span>
nlp<span class="token punctuation">.</span>add_pipe<span class="token punctuation">(</span><span class="token string">"custom_component"</span><span class="token punctuation">,</span> first<span class="token operator">=</span><span class="token boolean">True</span><span class="token punctuation">)</span>

<span class="token comment"># Process a text</span>
doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"Hello world!"</span><span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">Doc length: 3
</code></pre>
<h2 id="extension-attributes">Extension attributes</h2>
<h3 id="setting-custom-attributes">Setting custom attributes</h3>
<p>Custom attributes let you add any metadata to docs, tokens and spans. The data can be added once, or it can be computed dynamically.</p>
<p>Custom attributes are available via the  <code>._</code>  (dot underscore) property. This makes it clear that they were added by the user, and not built into spaCy, like  <code>token.text</code>.</p>
<pre class=" language-python"><code class="prism  language-python">doc<span class="token punctuation">.</span>_<span class="token punctuation">.</span>title <span class="token operator">=</span> <span class="token string">"My document"</span>
token<span class="token punctuation">.</span>_<span class="token punctuation">.</span>is_color <span class="token operator">=</span> <span class="token boolean">True</span>
span<span class="token punctuation">.</span>_<span class="token punctuation">.</span>has_color <span class="token operator">=</span> <span class="token boolean">False</span>
</code></pre>
<hr>
<p>Attributes need to be registered on the global  <code>Doc</code>,  <code>Token</code>  and  <code>Span</code>  classes you can import from  <code>spacy.tokens</code>. You’ve already worked with those in the previous chapters. To register a custom attribute on the  <code>Doc</code>,  <code>Token</code>  and  <code>Span</code>, you can use the  <code>set_extension</code>  method.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Import global classes</span>
<span class="token keyword">from</span> spacy<span class="token punctuation">.</span>tokens <span class="token keyword">import</span> Doc<span class="token punctuation">,</span> Token<span class="token punctuation">,</span> Span

<span class="token comment"># Set extensions on the Doc, Token and Span</span>
Doc<span class="token punctuation">.</span>set_extension<span class="token punctuation">(</span><span class="token string">"title"</span><span class="token punctuation">,</span> default<span class="token operator">=</span><span class="token boolean">None</span><span class="token punctuation">)</span>
Token<span class="token punctuation">.</span>set_extension<span class="token punctuation">(</span><span class="token string">"is_color"</span><span class="token punctuation">,</span> default<span class="token operator">=</span><span class="token boolean">False</span><span class="token punctuation">)</span>
Span<span class="token punctuation">.</span>set_extension<span class="token punctuation">(</span><span class="token string">"has_color"</span><span class="token punctuation">,</span> default<span class="token operator">=</span><span class="token boolean">False</span><span class="token punctuation">)</span>
</code></pre>
<p>The first argument is the attribute name. Keyword arguments let you define how the value should be computed. In this case, it has a default value and can be overwritten.</p>
<p>There are three types of extensions: attribute extensions, property extensions and method extensions.</p>
<h3 id="attribute-extensions">Attribute extensions</h3>
<p>Attribute extensions <mark>set a default value that can be overwritten</mark>.</p>
<p>For example, a custom  <code>is_color</code>  attribute on the token that defaults to  <code>False</code>.</p>
<p>On individual tokens, its value can be changed by overwriting it – in this case, True for the token “blue”.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">from</span> spacy<span class="token punctuation">.</span>tokens <span class="token keyword">import</span> Token

<span class="token comment"># Set extension on the Token with default value</span>
Token<span class="token punctuation">.</span>set_extension<span class="token punctuation">(</span><span class="token string">"is_color"</span><span class="token punctuation">,</span> default<span class="token operator">=</span><span class="token boolean">False</span><span class="token punctuation">)</span>

doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"The sky is blue."</span><span class="token punctuation">)</span>

<span class="token comment"># Overwrite extension attribute value</span>
doc<span class="token punctuation">[</span><span class="token number">3</span><span class="token punctuation">]</span><span class="token punctuation">.</span>_<span class="token punctuation">.</span>is_color <span class="token operator">=</span> <span class="token boolean">True</span>
</code></pre>
<h3 id="property-extensions">Property extensions</h3>
<p>Property extensions work like properties in Python: they <mark>can define a getter function and an optional setter</mark>.</p>
<p>The getter function is only called when you retrieve the attribute. This lets you compute the value dynamically, and even take other custom attributes into account.</p>
<p>Getter functions take one argument: the object, in this case, the token. In this example, the function returns whether the token text is in our list of colors.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">from</span> spacy<span class="token punctuation">.</span>tokens <span class="token keyword">import</span> Token

<span class="token comment"># Define getter function</span>
<span class="token keyword">def</span> <span class="token function">get_is_color</span><span class="token punctuation">(</span>token<span class="token punctuation">)</span><span class="token punctuation">:</span>
    colors <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token string">"red"</span><span class="token punctuation">,</span> <span class="token string">"yellow"</span><span class="token punctuation">,</span> <span class="token string">"blue"</span><span class="token punctuation">]</span>
    <span class="token keyword">return</span> token<span class="token punctuation">.</span>text <span class="token keyword">in</span> colors
</code></pre>
<p>We can then provide the function via the  <code>getter</code>  keyword argument when we register the extension.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Set extension on the Token with getter</span>
Token<span class="token punctuation">.</span>set_extension<span class="token punctuation">(</span><span class="token string">"is_color"</span><span class="token punctuation">,</span> getter<span class="token operator">=</span>get_is_color<span class="token punctuation">)</span>

doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"The sky is blue."</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>doc<span class="token punctuation">[</span><span class="token number">3</span><span class="token punctuation">]</span><span class="token punctuation">.</span>_<span class="token punctuation">.</span>is_color<span class="token punctuation">,</span> <span class="token string">"-"</span><span class="token punctuation">,</span> doc<span class="token punctuation">[</span><span class="token number">3</span><span class="token punctuation">]</span><span class="token punctuation">.</span>text<span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">True - blue
</code></pre>
<p>The token “blue” now returns  <code>True</code>  for  <code>._.is_color</code>.</p>
<hr>
<p>If you want to set extension attributes on a span, you almost always want to use a property extension with a getter. <mark>Otherwise, you’d have to update  <em>every possible span ever</em>  by hand to set all the values</mark>.</p>
<p>In this example, the  <code>get_has_color</code>  function takes the span and returns whether the text of any of the tokens is in the list of colors.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">from</span> spacy<span class="token punctuation">.</span>tokens <span class="token keyword">import</span> Span

<span class="token comment"># Define getter function</span>
<span class="token keyword">def</span> <span class="token function">get_has_color</span><span class="token punctuation">(</span>span<span class="token punctuation">)</span><span class="token punctuation">:</span>
    colors <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token string">"red"</span><span class="token punctuation">,</span> <span class="token string">"yellow"</span><span class="token punctuation">,</span> <span class="token string">"blue"</span><span class="token punctuation">]</span>
    <span class="token keyword">return</span> <span class="token builtin">any</span><span class="token punctuation">(</span>token<span class="token punctuation">.</span>text <span class="token keyword">in</span> colors <span class="token keyword">for</span> token <span class="token keyword">in</span> span<span class="token punctuation">)</span>

<span class="token comment"># Set extension on the Span with getter</span>
Span<span class="token punctuation">.</span>set_extension<span class="token punctuation">(</span><span class="token string">"has_color"</span><span class="token punctuation">,</span> getter<span class="token operator">=</span>get_has_color<span class="token punctuation">)</span>
</code></pre>
<p>After we’ve processed the doc, we can check different slices of the doc and the custom  <code>._.has_color</code>  property returns whether the span contains a color token or not.</p>
<pre class=" language-python"><code class="prism  language-python">doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"The sky is blue."</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>doc<span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">:</span><span class="token number">4</span><span class="token punctuation">]</span><span class="token punctuation">.</span>_<span class="token punctuation">.</span>has_color<span class="token punctuation">,</span> <span class="token string">"-"</span><span class="token punctuation">,</span> doc<span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">:</span><span class="token number">4</span><span class="token punctuation">]</span><span class="token punctuation">.</span>text<span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>doc<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">:</span><span class="token number">2</span><span class="token punctuation">]</span><span class="token punctuation">.</span>_<span class="token punctuation">.</span>has_color<span class="token punctuation">,</span> <span class="token string">"-"</span><span class="token punctuation">,</span> doc<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">:</span><span class="token number">2</span><span class="token punctuation">]</span><span class="token punctuation">.</span>text<span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">True - sky is blue
False - The sky
</code></pre>
<h3 id="method-extensions">Method extensions</h3>
<p>Method extensions make <mark>the extension attribute a callable method</mark>.</p>
<p>You can then pass one or more arguments to it, and compute attribute values dynamically – for example, based on a certain argument or setting.</p>
<p>In this example, the method function checks whether the doc contains a token with a given text. The first argument of the method is always the object itself – in this case, the doc. It’s passed in automatically when the method is called. All other function arguments will be arguments on the method extension. In this case,  <code>token_text</code>.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">from</span> spacy<span class="token punctuation">.</span>tokens <span class="token keyword">import</span> Doc

<span class="token comment"># Define method with arguments</span>
<span class="token keyword">def</span> <span class="token function">has_token</span><span class="token punctuation">(</span>doc<span class="token punctuation">,</span> token_text<span class="token punctuation">)</span><span class="token punctuation">:</span>
    in_doc <span class="token operator">=</span> token_text <span class="token keyword">in</span> <span class="token punctuation">[</span>token<span class="token punctuation">.</span>text <span class="token keyword">for</span> token <span class="token keyword">in</span> doc<span class="token punctuation">]</span>
    <span class="token keyword">return</span> in_doc

<span class="token comment"># Set extension on the Doc with method</span>
Doc<span class="token punctuation">.</span>set_extension<span class="token punctuation">(</span><span class="token string">"has_token"</span><span class="token punctuation">,</span> method<span class="token operator">=</span>has_token<span class="token punctuation">)</span>

doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"The sky is blue."</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>doc<span class="token punctuation">.</span>_<span class="token punctuation">.</span>has_token<span class="token punctuation">(</span><span class="token string">"blue"</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token string">"- blue"</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>doc<span class="token punctuation">.</span>_<span class="token punctuation">.</span>has_token<span class="token punctuation">(</span><span class="token string">"cloud"</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token string">"- cloud"</span><span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">True - blue
False - cloud
</code></pre>
<p>Here, the custom  <code>._.has_token</code>  method returns  <code>True</code>  for the word “blue” and  <code>False</code>  for the word “cloud”.</p>
<h2 id="scaling-and-performance">Scaling and performance</h2>
<h3 id="processing-large-volumes-of-text">Processing large volumes of text</h3>
<p>If you need to process a lot of texts and create a lot of  <code>Doc</code>  objects in a row, the  <code>nlp.pipe</code>  method can speed this up significantly.</p>
<p>It processes the texts as a stream and yields  <code>Doc</code>  objects.</p>
<p>It is much faster than just calling nlp on each text, because <mark>it batches up the texts</mark>.</p>
<p><code>nlp.pipe</code>  is a generator that yields  <code>Doc</code>  objects, so in order to get a list of docs, remember to call the  <code>list</code>  method around it.</p>
<p><strong>BAD:</strong></p>
<pre class=" language-python"><code class="prism  language-python">docs <span class="token operator">=</span> <span class="token punctuation">[</span>nlp<span class="token punctuation">(</span>text<span class="token punctuation">)</span> <span class="token keyword">for</span> text <span class="token keyword">in</span> LOTS_OF_TEXTS<span class="token punctuation">]</span>
</code></pre>
<p><strong>GOOD:</strong></p>
<pre class=" language-python"><code class="prism  language-python">docs <span class="token operator">=</span> <span class="token builtin">list</span><span class="token punctuation">(</span>nlp<span class="token punctuation">.</span>pipe<span class="token punctuation">(</span>LOTS_OF_TEXTS<span class="token punctuation">)</span><span class="token punctuation">)</span>
</code></pre>
<h3 id="passing-in-context">Passing in context</h3>
<p><code>nlp.pipe</code>  also supports passing in tuples of text / context if you set  <code>as_tuples</code>  to  <code>True</code>.</p>
<p>The method will then yield doc / context tuples.</p>
<p>This is useful for passing in additional metadata, like an ID associated with the text, or a page number.</p>
<pre class=" language-python"><code class="prism  language-python">data <span class="token operator">=</span> <span class="token punctuation">[</span>
    <span class="token punctuation">(</span><span class="token string">"This is a text"</span><span class="token punctuation">,</span> <span class="token punctuation">{</span><span class="token string">"id"</span><span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token string">"page_number"</span><span class="token punctuation">:</span> <span class="token number">15</span><span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
    <span class="token punctuation">(</span><span class="token string">"And another text"</span><span class="token punctuation">,</span> <span class="token punctuation">{</span><span class="token string">"id"</span><span class="token punctuation">:</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token string">"page_number"</span><span class="token punctuation">:</span> <span class="token number">16</span><span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">]</span>

<span class="token keyword">for</span> doc<span class="token punctuation">,</span> context <span class="token keyword">in</span> nlp<span class="token punctuation">.</span>pipe<span class="token punctuation">(</span>data<span class="token punctuation">,</span> as_tuples<span class="token operator">=</span><span class="token boolean">True</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span>doc<span class="token punctuation">.</span>text<span class="token punctuation">,</span> context<span class="token punctuation">[</span><span class="token string">"page_number"</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
</code></pre>
<p><strong>out</strong></p>
<pre class=" language-out"><code class="prism  language-out">This is a text 15
And another text 16
</code></pre>
<hr>
<p>You can even add the context metadata to custom attributes.</p>
<p>In this example, we’re registering two extensions,  <code>id</code>  and  <code>page_number</code>, which default to  <code>None</code>.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">from</span> spacy<span class="token punctuation">.</span>tokens <span class="token keyword">import</span> Doc

Doc<span class="token punctuation">.</span>set_extension<span class="token punctuation">(</span><span class="token string">"id"</span><span class="token punctuation">,</span> default<span class="token operator">=</span><span class="token boolean">None</span><span class="token punctuation">)</span>
Doc<span class="token punctuation">.</span>set_extension<span class="token punctuation">(</span><span class="token string">"page_number"</span><span class="token punctuation">,</span> default<span class="token operator">=</span><span class="token boolean">None</span><span class="token punctuation">)</span>

data <span class="token operator">=</span> <span class="token punctuation">[</span>
    <span class="token punctuation">(</span><span class="token string">"This is a text"</span><span class="token punctuation">,</span> <span class="token punctuation">{</span><span class="token string">"id"</span><span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token string">"page_number"</span><span class="token punctuation">:</span> <span class="token number">15</span><span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
    <span class="token punctuation">(</span><span class="token string">"And another text"</span><span class="token punctuation">,</span> <span class="token punctuation">{</span><span class="token string">"id"</span><span class="token punctuation">:</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token string">"page_number"</span><span class="token punctuation">:</span> <span class="token number">16</span><span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">]</span>
</code></pre>
<p>After processing the text and passing through the context, we can overwrite the doc extensions with our context metadata.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">for</span> doc<span class="token punctuation">,</span> context <span class="token keyword">in</span> nlp<span class="token punctuation">.</span>pipe<span class="token punctuation">(</span>data<span class="token punctuation">,</span> as_tuples<span class="token operator">=</span><span class="token boolean">True</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
    doc<span class="token punctuation">.</span>_<span class="token punctuation">.</span><span class="token builtin">id</span> <span class="token operator">=</span> context<span class="token punctuation">[</span><span class="token string">"id"</span><span class="token punctuation">]</span>
    doc<span class="token punctuation">.</span>_<span class="token punctuation">.</span>page_number <span class="token operator">=</span> context<span class="token punctuation">[</span><span class="token string">"page_number"</span><span class="token punctuation">]</span>
</code></pre>
<h3 id="using-only-the-tokenizer">Using only the tokenizer</h3>
<p>Another common scenario: Sometimes you already have a model loaded to do other processing, but you only need the tokenizer for one particular text.</p>
<p>Running the whole pipeline is unnecessarily slow, because you’ll be getting a bunch of predictions from the model that you don’t need.</p>
<p>If you only need a tokenized  <code>Doc</code>  object, you can use the  <code>nlp.make_doc</code>  method instead, which takes a text and returns a doc.</p>
<p>This is also how spaCy does it behind the scenes:  <code>nlp.make_doc</code>  turns the text into a doc before the pipeline components are called.</p>
<p><strong>BAD:</strong></p>
<pre class=" language-python"><code class="prism  language-python">doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"Hello world"</span><span class="token punctuation">)</span>
</code></pre>
<p><strong>GOOD:</strong></p>
<pre class=" language-python"><code class="prism  language-python">doc <span class="token operator">=</span> nlp<span class="token punctuation">.</span>make_doc<span class="token punctuation">(</span><span class="token string">"Hello world!"</span><span class="token punctuation">)</span>
</code></pre>
<h3 id="disabling-pipeline-components">Disabling pipeline components</h3>
<p>spaCy also allows you to temporarily disable pipeline components using the  <code>nlp.select_pipes</code>  context manager.</p>
<p>It accepts the keyword arguments  <code>enable</code>  or  <code>disable</code>  that can define a list of string names of the pipeline components to disable. For example, if you only want to use the entity recognizer to process a document, you can temporarily disable the tagger and parser.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Disable tagger and parser</span>
<span class="token keyword">with</span> nlp<span class="token punctuation">.</span>select_pipes<span class="token punctuation">(</span>disable<span class="token operator">=</span><span class="token punctuation">[</span><span class="token string">"tagger"</span><span class="token punctuation">,</span> <span class="token string">"parser"</span><span class="token punctuation">]</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token comment"># Process the text and print the entities</span>
    doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span>text<span class="token punctuation">)</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span>doc<span class="token punctuation">.</span>ents<span class="token punctuation">)</span>
</code></pre>
<p>After the  <code>with</code>  block, the disabled pipeline components are automatically restored.</p>
<p>In the  <code>with</code>  block, spaCy will only run the remaining components.</p>
<h1 id="chapter-4-training-a-neural-network-model"><a href="https://course.spacy.io/en/chapter4">Chapter 4: Training a neural network model</a></h1>
<h2 id="training-and-updating-models">Training and updating models</h2>
<p>Before we get starting with explaining  <em>how</em>, it’s worth taking a second to ask ourselves: Why would we want to update the model with our own examples? Why can’t we just rely on pre-trained pipelines?</p>
<p>Statistical models make predictions based on the examples they were trained on.</p>
<p>You can usually make the model more accurate by showing it examples from your domain.</p>
<p>You often also want to predict categories specific to your problem, so the model needs to learn about them.</p>
<p>This is essential for text classification, very useful for entity recognition and a little less critical for tagging and parsing.</p>
<h3 id="how-training-works">How training works</h3>
<p>spaCy supports updating existing models with more examples, and training new models. If we’re not starting with a trained pipeline, we first <em><strong>initialize the weights randomly</strong></em>.</p>
<p>Next, spaCy calls  <code>nlp.update</code>, which predicts a <em><strong>batch of examples with the current weights</strong></em>.</p>
<p>The model then <em><strong>checks the predictions against</strong></em> the correct answers, and <em><strong>decides how to change the weights</strong></em> to achieve better predictions next time.</p>
<p>Finally, <em><strong>we make a small correction to the current weights</strong></em> and move on to the next batch of examples.</p>
<p>spaCy then continues calling  <code>nlp.update</code>  for each batch of examples in the data. During training, you usually want to make multiple passes over the data and train until the model stops improving.</p>
<p><img src="https://course.spacy.io/training.png" alt="Diagram of the training process"></p>
<p>The training data are the examples we want to update the model with.</p>
<p>The text should be a sentence, paragraph or longer document. For the best results, it should be similar to what the model will see at runtime.</p>
<p>The label is what we want the model to predict. This can be a text category, or an entity span and its type.</p>
<p>The gradient is how we should change the model to reduce the current error. It’s computed when we compare the predicted label to the true label.</p>
<p>After training, we can then save out an updated model and use it in our application.</p>
<h3 id="example-training-the-entity-recognizer">Example: Training the entity recognizer</h3>
<p>Let’s look at an example for a specific component: the entity recognizer.</p>
<p>The entity recognizer takes a document and predicts phrases and their labels  <em>in context</em>. This means that the <mark>training data needs to include texts, the entities they contain, and the entity labels</mark>.</p>
<p>Entities can’t overlap, so each token can only be part of one entity.</p>
<p>The easiest way to do this is to show the model a text and entity spans. spaCy can be updated from regular  <code>Doc</code>  objects with entities annotated as the  <code>doc.ents</code>. For example, “iPhone X” is a gadget, starts at token 0 and ends at token 1.</p>
<pre class=" language-python"><code class="prism  language-python">doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"iPhone X is coming"</span><span class="token punctuation">)</span>
doc<span class="token punctuation">.</span>ents <span class="token operator">=</span> <span class="token punctuation">[</span>Span<span class="token punctuation">(</span>doc<span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> label<span class="token operator">=</span><span class="token string">"GADGET"</span><span class="token punctuation">)</span><span class="token punctuation">]</span>
</code></pre>
<p>It’s also very important for the model to learn words that  <em>aren’t</em>  entities.</p>
<p>In this case, the list of span annotations will be empty.</p>
<pre class=" language-python"><code class="prism  language-python">doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"I need a new phone! Any tips?"</span><span class="token punctuation">)</span>
doc<span class="token punctuation">.</span>ents <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">]</span>
</code></pre>
<p>Our goal is to teach the model to recognize new entities in similar contexts, even if they weren’t in the training data.</p>
<h3 id="the-training-data">The training data</h3>
<p>The training data tells the model what we want it to predict. This could be texts and named entities we want to recognize, tokens and their correct part-of-speech tags or anything else the model should predict.</p>
<p>To update an existing model, we can start with a <mark>few hundred to a few thousand examples</mark>.</p>
<p>To train a new category we may need <mark>up to a million</mark>.</p>
<p>spaCy’s trained English pipelines for instance were trained on 2 million words labelled with part-of-speech tags, dependencies and named entities.</p>
<p>Training data is usually created by humans who assign labels to texts.</p>
<p>This is a lot of work, but can be semi-automated – for example, using spaCy’s  <code>Matcher</code>.</p>
<h3 id="training-vs.-evaluation-data">Training vs. evaluation data</h3>
<p>When training your model, it’s important to know how it’s doing and whether it’s learning the right thing. This is done by comparing the model’s predictions on examples it  <em>hasn’t</em>  seen during training to answers we already know. So in addition to the training data, you also need evaluation data, also called development data.</p>
<p>The evaluation data is used to calculate how accurate your model is. For example, an accuracy score of 90% means that the model predicted 90% of the evaluation examples correctly.</p>
<p>This also means that the evaluation data needs to be representative of the data your model will see at runtime. Otherwise, the accuracy score will be meaningless, because it won’t tell you how good your model  <em>really</em>  is.</p>
<h3 id="generating-a-training-corpus">Generating a training corpus</h3>
<p>spaCy can be updated from data in the same format it creates:  <code>Doc</code>  objects. You already learned all about creating  <code>Doc</code>  and  <code>Span</code>  objects in chapter 2.</p>
<p>In this example, we’re creating two  <code>Doc</code>  objects for our corpus: one that contains an entity and another one that doesn’t contain any entities. To set the entities on the  <code>Doc</code>, we can add a  <code>Span</code>  to the  <code>doc.ents</code>.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">import</span> spacy

nlp <span class="token operator">=</span> spacy<span class="token punctuation">.</span>blank<span class="token punctuation">(</span><span class="token string">"en"</span><span class="token punctuation">)</span>

<span class="token comment"># Create a Doc with entity spans</span>
doc1 <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"iPhone X is coming"</span><span class="token punctuation">)</span>
doc1<span class="token punctuation">.</span>ents <span class="token operator">=</span> <span class="token punctuation">[</span>Span<span class="token punctuation">(</span>doc1<span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> label<span class="token operator">=</span><span class="token string">"GADGET"</span><span class="token punctuation">)</span><span class="token punctuation">]</span>
<span class="token comment"># Create another doc without entity spans</span>
doc2 <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"I need a new phone! Any tips?"</span><span class="token punctuation">)</span>

docs <span class="token operator">=</span> <span class="token punctuation">[</span>doc1<span class="token punctuation">,</span> doc2<span class="token punctuation">]</span>  <span class="token comment"># and so on...</span>
</code></pre>
<p>Of course, you’ll need a lot more examples to effectively train your model to generalize and predict similar entities in context. Depending on the task, you usually want at least a few hundred to a few thousand representative examples.</p>
<p>As I mentioned earlier, we don’t just need data to train the model. We also want to evaluate its accuracy on examples it hasn’t seen during training. This is usually done by shuffling and splitting your data in two: one portion for training and one for evaluation. Here, we’re using a simple 50/50 split.</p>
<pre class=" language-python"><code class="prism  language-python">random<span class="token punctuation">.</span>shuffle<span class="token punctuation">(</span>docs<span class="token punctuation">)</span>
train_docs <span class="token operator">=</span> docs<span class="token punctuation">[</span><span class="token punctuation">:</span><span class="token builtin">len</span><span class="token punctuation">(</span>docs<span class="token punctuation">)</span> <span class="token operator">//</span> <span class="token number">2</span><span class="token punctuation">]</span>
dev_docs <span class="token operator">=</span> docs<span class="token punctuation">[</span><span class="token builtin">len</span><span class="token punctuation">(</span>docs<span class="token punctuation">)</span> <span class="token operator">//</span> <span class="token number">2</span><span class="token punctuation">:</span><span class="token punctuation">]</span>
</code></pre>
<p>You typically want to store your training and development data as files on disk so you can load them into spaCy’s training process.</p>
<p>The  <code>DocBin</code>  is a container for efficiently storing and serializing  <code>Doc</code>  objects. You can instantiate it with a list of  <code>Doc</code>  objects and call its  <code>to_disk</code>  method to save it to a binary file. We typically use the file extension  <code>.spacy</code>  for these files.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Create and save a collection of training docs</span>
train_docbin <span class="token operator">=</span> DocBin<span class="token punctuation">(</span>docs<span class="token operator">=</span>train_docs<span class="token punctuation">)</span>
train_docbin<span class="token punctuation">.</span>to_disk<span class="token punctuation">(</span><span class="token string">"./train.spacy"</span><span class="token punctuation">)</span>
<span class="token comment"># Create and save a collection of evaluation docs</span>
dev_docbin <span class="token operator">=</span> DocBin<span class="token punctuation">(</span>docs<span class="token operator">=</span>dev_docs<span class="token punctuation">)</span>
dev_docbin<span class="token punctuation">.</span>to_disk<span class="token punctuation">(</span><span class="token string">"./dev.spacy"</span><span class="token punctuation">)</span>
</code></pre>
<p>Compared to other binary serialization protocols like  <code>pickle</code>, the  <code>DocBin</code>  is faster and produces smaller file sizes because it only stores the shared vocabulary once. You can read more about how it works in the  <a href="https://spacy.io/api/docbin">documentation</a>.</p>
<h3 id="tip-converting-your-data">Tip: Converting your data</h3>
<p>In some cases, you might already have training and development data in a common format – for example, CoNLL or IOB. spaCy’s <code>convert</code> command automatically converts these files into spaCy’s binary format. It also converts JSON files in the old format used by spaCy v2.</p>
<pre class=" language-python"><code class="prism  language-python">$ python <span class="token operator">-</span>m spacy convert <span class="token punctuation">.</span><span class="token operator">/</span>train<span class="token punctuation">.</span>gold<span class="token punctuation">.</span>conll <span class="token punctuation">.</span><span class="token operator">/</span>corpus
</code></pre>
<h2 id="configuring-and-running-the-training">Configuring and running the training</h2>
<h3 id="the-training-config">The training config</h3>
<p>spaCy uses a config file, usually called  <code>config.cfg</code>, as the “single source of truth” for all settings. The config file defines how to initialize the  <code>nlp</code>  object, which pipeline components to add and how their internal model implementations should be configured. It also includes all settings for the training process and how to load the data, including hyperparameters.</p>
<p>Instead of providing lots of arguments on the command line or having to remember to define every single setting in code, <mark>you only need to pass your config file to spaCy’s training command</mark>.</p>
<p>Config files also help with reproducibility: you’ll have all settings in one place and always know how your pipeline was trained. You can even check your config file into a Git repo to version it and share it with others so they can train the same pipeline with the same settings.</p>
<p>Here’s an excerpt from a config file used to train a pipeline with a named entity recognizer. The config is grouped into sections, and nested sections are defined using a dot. For example,  <code>[components.ner.model]</code>  defines the settings for the named entity recognizer’s model implementation.</p>
<pre class=" language-ini"><code class="prism  language-ini"><span class="token selector">[nlp]</span>
<span class="token constant">lang</span> <span class="token attr-value"><span class="token punctuation">=</span> "en"</span>
<span class="token constant">pipeline</span> <span class="token attr-value"><span class="token punctuation">=</span> ["tok2vec", "ner"]</span>
<span class="token constant">batch_size</span> <span class="token attr-value"><span class="token punctuation">=</span> 1000</span>

<span class="token selector">[nlp.tokenizer]</span>
<span class="token constant">@tokenizers</span> <span class="token attr-value"><span class="token punctuation">=</span> "spacy.Tokenizer.v1"</span>

<span class="token selector">[components]</span>

<span class="token selector">[components.ner]</span>
<span class="token constant">factory</span> <span class="token attr-value"><span class="token punctuation">=</span> "ner"</span>

<span class="token selector">[components.ner.model]</span>
<span class="token constant">@architectures</span> <span class="token attr-value"><span class="token punctuation">=</span> "spacy.TransitionBasedParser.v2"</span>
<span class="token constant">hidden_width</span> <span class="token attr-value"><span class="token punctuation">=</span> 64</span>
# And so on...
</code></pre>
<p>Config files can also reference Python functions using the  <code>@</code>  notation. For example, the tokenizer defines a registered tokenizer function. You can use this to customize different parts of the  <code>nlp</code>  object and training – from plugging in your own tokenizer, all the way to implementing your own model architectures. But let’s not worry about this for now – what you’ll learn in this chapter will simply use the defaults spaCy provides out-of-the-box!</p>
<h3 id="generating-a-config">Generating a config</h3>
<p>Of course, you don’t have to write the config files by hand, and in a lot of cases, you won’t even need to customize it at all. spaCy can auto-generate a config file for you.</p>
<p>The quickstart widget in the documentation lets you generate a config interactively by selecting the language and pipeline components you need, as well as optional hardware and optimization settings.</p>
<p>Alternatively, you can also use spaCy’s built-in  <code>init config</code>  command. It <mark>takes the output file as the first argument</mark>. We usually call this file  <code>config.cfg</code>. The argument  <code>--lang</code>  defines the language class that should be used for the pipeline, for example,  <code>en</code>  for English. The  <code>--pipeline</code>  argument lets you specify one or more comma-separated pipeline components to include. In this example, we’re creating a config with one pipeline component, the named entity recognizer.</p>
<pre class=" language-bash"><code class="prism  language-bash">$ python -m spacy init config ./config.cfg --lang en --pipeline ner
</code></pre>
<h3 id="training-a-pipeline">Training a pipeline</h3>
<p>To train a pipeline, all you need is the config file and the training and development data. These are the  <code>.spacy</code>  files you already worked with in the previous exercises.</p>
<p>The first argument of  <code>spacy train</code>  is the path to the config file. The  <code>--output</code>  argument lets you specify a directory for saving the final trained pipeline.</p>
<p>You can also override different config settings on the command line. In this case, we override  <code>paths.train</code>  using the path to the  <code>train.spacy</code>  file and  <code>paths.dev</code>  using the  <code>dev.spacy</code>  file.</p>
<pre class=" language-bash"><code class="prism  language-bash">$ python -m spacy train ./config.cfg --output ./output --paths.train train.spacy --paths.dev dev.spacy
</code></pre>
<p>Here’s an example of the output you’ll see during and after training. You might remember from earlier in this chapter that you usually want to make several passes over the data during training. Each pass over the data is also called an “epoch”. This is shown in the first column of the table.</p>
<p>Within each epoch, spaCy outputs the accuracy scores every 200 examples. These are the steps shown in the second column. You can change the frequency in the config. Each line shows the loss and calculated accuracy score at this point during training.</p>
<pre><code>============================ Training pipeline ============================
ℹ Pipeline: ['tok2vec', 'ner']
ℹ Initial learn rate: 0.001

E    #       LOSS TOK2VEC  LOSS NER  ENTS_F  ENTS_P  ENTS_R  SCORE
---  ------  ------------  --------  ------  ------  ------  ------
  0       0          0.00     26.50    0.73    0.39    5.43    0.01
  0     200         33.58    847.68   10.88   44.44    6.20    0.11
  1     400         70.88    267.65   33.50   45.95   26.36    0.33
  2     600         67.56    156.63   45.32   62.16   35.66    0.45
  3     800        138.28    134.12   48.17   74.19   35.66    0.48
  4    1000        177.95    109.77   51.43   66.67   41.86    0.51
  6    1200         94.95     52.13   54.63   67.82   45.74    0.55
  8    1400        126.85     66.19   56.00   65.62   48.84    0.56
 10    1600         38.34     24.16   51.96   70.67   41.09    0.52
 13    1800        105.14     23.23   56.88   69.66   48.06    0.57

✔ Saved pipeline to output directory
/path/to/output/model-last
</code></pre>
<p>The most interesting score to keep an eye on is the combined score in the last column. It reflects how accurately your model predicted the correct answers in the evaluation data.</p>
<p>The training runs until the model stops improving and exits automatically.</p>
<h3 id="loading-a-trained-pipeline">Loading a trained pipeline</h3>
<p>The pipeline saved after training is a regular loadable spaCy pipeline – just like the trained pipelines provided by spaCy, for example  <code>en_core_web_sm</code>. At the end, the last trained pipeline and the pipeline with the best score is saved to the output directory.</p>
<p>You can load your trained pipeline by passing the path to  <code>spacy.load</code>. You can then use it to process and analyze text.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">import</span> spacy

nlp <span class="token operator">=</span> spacy<span class="token punctuation">.</span>load<span class="token punctuation">(</span><span class="token string">"/path/to/output/model-best"</span><span class="token punctuation">)</span>
doc <span class="token operator">=</span> nlp<span class="token punctuation">(</span><span class="token string">"iPhone 11 vs iPhone 8: What's the difference?"</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>doc<span class="token punctuation">.</span>ents<span class="token punctuation">)</span>
</code></pre>
<h3 id="tip-packaging-your-pipeline">Tip: Packaging your pipeline</h3>
<p>To make it easy to deploy your pipelines, spaCy provides a handy command to package them as Python packages. The  <code>spacy package</code>  command takes the path to your exported pipeline and an output directory. It then generates a Python package containing your pipeline. The Python package is a  <code>.tar.gz</code>  file and can be installed into your environment.</p>
<p>You can also provide an optional name and version on the command. This lets you manage multiple different versions of a pipeline, for example, if you decide to customize your pipeline later or train it with more data.</p>
<pre class=" language-bash"><code class="prism  language-bash">$ python -m spacy package /path/to/output/model-best ./packages --name my_pipeline --version 1.0.0
</code></pre>
<pre class=" language-bash"><code class="prism  language-bash">$ <span class="token function">cd</span> ./packages/en_my_pipeline-1.0.0
$ pip <span class="token function">install</span> dist/en_my_pipeline-1.0.0.tar.gz
</code></pre>
<p>The package behaves just like any other Python package. After installation, you can load your pipeline using its name. Note that spaCy will automatically add the language code to the name. So your pipeline  <code>my_pipeline</code>  will become  <code>en_my_pipeline</code>.</p>
<pre class=" language-python"><code class="prism  language-python">nlp <span class="token operator">=</span> spacy<span class="token punctuation">.</span>load<span class="token punctuation">(</span><span class="token string">"en_my_pipeline"</span><span class="token punctuation">)</span>
</code></pre>
<h2 id="best-practices-for-training-spacy-models">Best practices for training spaCy models</h2>
<h3 id="problem-1-models-can-forget-things">Problem 1: Models can “forget” things</h3>
<p>Statistical models can learn lots of things – but <mark>they can also unlearn them</mark>.</p>
<p>If you’re updating an existing model with new data, especially new labels, it can <mark>overfit</mark> and adjust  <em>too much</em>  to the new examples.</p>
<p>For instance, if you’re only updating it with examples of  <code>"WEBSITE"</code>, it may “forget” other labels it previously predicted correctly – like  <code>"PERSON"</code>.</p>
<p>This is also known as the catastrophic forgetting problem.</p>
<h3 id="solution-1-mix-in-previously-correct-predictions">Solution 1: Mix in previously correct predictions</h3>
<p>To prevent this, make sure to always <mark>mix in examples of what the model previously got correct</mark>.</p>
<p>If you’re training a new category  <code>"WEBSITE"</code>, also include examples of  <code>"PERSON"</code>.</p>
<p>spaCy can help you with this. You can create those additional examples by running the existing model over data and extracting the entity spans you care about.</p>
<p>You can then mix those examples in with your existing data and update the model with annotations of all labels.</p>
<h3 id="problem-2-models-cant-learn-everything">Problem 2: Models can’t learn everything</h3>
<p>Another common problem is that your model just won’t learn what you want it to.</p>
<p>spaCy’s models make predictions based on the local context – for example, for named entities, the surrounding words are most important.</p>
<p>If the decision is difficult to make based on the context, the model can struggle to learn it.</p>
<p>The label scheme also needs to be consistent and not too specific.</p>
<p>For example, it may be very difficult to teach a model to predict whether something is adult clothing or children’s clothing based on the context. However, just predicting the label “clothing” may work better.</p>
<h3 id="solution-2-plan-your-label-scheme-carefully">Solution 2: Plan your label scheme carefully</h3>
<p>Before you start training and updating models, it’s worth taking a step back and planning your label scheme.</p>
<p>Try to <mark>pick categories that are reflected in the local context and make them more generic if possible</mark>.</p>
<p>You can always add a rule-based system later to go from generic to specific.</p>
<p>Generic categories like “clothing” or “band” are both easier to label and easier to learn.</p>
<p><strong>BAD:</strong></p>
<pre class=" language-python"><code class="prism  language-python">LABELS <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token string">"ADULT_SHOES"</span><span class="token punctuation">,</span> <span class="token string">"CHILDRENS_SHOES"</span><span class="token punctuation">,</span> <span class="token string">"BANDS_I_LIKE"</span><span class="token punctuation">]</span>
</code></pre>
<p><strong>GOOD:</strong></p>
<pre class=" language-python"><code class="prism  language-python">LABELS <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token string">"CLOTHING"</span><span class="token punctuation">,</span> <span class="token string">"BAND"</span><span class="token punctuation">]</span>
</code></pre>

