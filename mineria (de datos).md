---


---

<p><strong>Ley de Zipf:</strong><br>
Los lenguajes naturales (LN) tienen <em><strong>distribucion exponencial</strong></em></p>
<blockquote>
<p>Parametros parecidos para cualquier lenguaje</p>
</blockquote>
<p><a href="https://medium.com/nlplanet/two-minutes-nlp-21-learning-resources-for-text-classification-b6f9c43793e1">Two minutes NLP — 21 Learning Resources for Text Classification</a></p>
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
<p><a href="https://www.kaggle.com/code/parulpandey/getting-started-with-nlp-a-general-intro">Getting started with NLP - A general Intro</a><br>
<a href="https://www.kaggle.com/code/parulpandey/getting-started-with-nlp-feature-vectors#2.Hashing-Vectorizer">Getting started with NLP - Feature Vectors</a></p>
<p><img src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*HMskuHrmqBdQXus2VNvZ0g.png" alt=""></p>
<p><a href="https://arxiv.org/pdf/1904.08067"><strong>Resumen GOD</strong></a><br>
<a href="https://arxiv.org/pdf/1708.00107">CoVe</a><br>
<a href="https://nlp.stanford.edu/projects/glove/">GloVe</a><br>
<a href="https://blog.insightdatascience.com/how-to-solve-90-of-nlp-problems-a-step-by-step-guide-fda605278e4e">How to solve 90% of NLP problems: a step-by-step guide</a></p>
<p>Parte de la muestra sirve estratificar (nose que es)<br>
<em>stop words</em>: son palabras sin significancia dictica (ver bienn)</p>
<h1 id="día-del-filatelista-argentino">21/8 Día del Filatelista Argentino</h1>
<h2 id="analisis-del-lenguaje">Analisis del Lenguaje</h2>
<blockquote>
<p><em><strong>Cancion del dia</strong></em>: <a href="https://open.spotify.com/intl-es/track/22Fvc0gkf7ZCNQEQ2Oxj6D?si=9a43ff5791a64cd9">Smoke Remix  - Blood Orange, Yves Tumor</a></p>
</blockquote>
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
la escritura es un artefacto <em><strong>sobre</strong></em> LN<br>
<em><strong>Pasos:</strong></em></li>
<li>Comprender</li>
<li>Generar<br>
end-to-end vs analisis por niveles<br>
ejemplo trad. autimatica:</li>
<li>analisis y generacion</li>
<li>canal ruidoso</li>
<li>transformers</li>
</ul>
<p><a href="https://docs.google.com/presentation/d/1APyWCRzmQYnyPU1vHGfTF3TNrluGHepyFCV3JkVJBiQ/edit#slide=id.p"><em><strong>SLIDES USADOS</strong></em></a></p>
<h1 id="día-del-archivero-día-de-la-ancianidad">28/8 Día del Archivero, Día de la Ancianidad</h1>
<h2 id="evaluacion-de-modelos">Evaluacion de Modelos</h2>
<blockquote>
<p><em><strong>Cancion del dia</strong></em>: <a href="https://open.spotify.com/intl-es/track/4WiiRw2PHMNQE0ad6y6GdD?si=c42a4b6f2ea744a1">Chocolate - The 1975</a></p>
</blockquote>
<p>Principio de Coperacion<br>
<a href="https://en.wikipedia.org/wiki/Evaluation_of_binary_classifiers">Evaluation of binary classifiers</a><br>
<a href="https://en.wikipedia.org/wiki/Evaluation_of_binary_classifiers#Contingency_table">Contingency Table</a></p>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Sensitivity_and_specificity">Sensitivity (Recall) and Specifity (not Sense and Sensibility)</a></li>
<li><a href="https://en.wikipedia.org/wiki/Positive_and_negative_predictive_values">Positive and negative predictive values</a></li>
<li><a href="https://en.wikipedia.org/wiki/Precision_and_recall">Precision and Recall</a>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Precision_and_recall#F-measure">F-measure</a></li>
</ul>
</li>
</ul>
<p><a href="https://en.wikipedia.org/wiki/Confusion_matrix">Confusion Matrix</a><br>
<a href="https://en.wikipedia.org/wiki/Receiver_operating_characteristic#Basic_concept">ROC</a><br>
<a href="https://en.wikipedia.org/wiki/Cohen%27s_kappa">Kappa de Cohen</a></p>
<p>En contexto de NLP, para reducir el sesgo predictivo, podemos contrastar con variaciones del mimso lenguaje.</p>
<p><a href="https://en.wikipedia.org/wiki/Fairness_(machine_learning)#">Fairness</a></p>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Fairness_(machine_learning)#Group_fairness_criteria">Group fairness criteria</a></li>
</ul>
<p>Para LLMs se suelen usar distintos benchmarks como:<br>
<a href="https://nordicapis.com/7-ways-to-test-llms/?ref=dailydev">7 Ways to Test LLMs</a></p>
<p><a href="https://docs.google.com/presentation/d/10Zz1K8jx3Q5XOs78tlMGFfiTAKkfAXTTaea3KgDBQIk/edit#slide=id.gb0f795d4a0_0_20"><em><strong>SLIDES USADOS</strong></em></a>.</p>
<h1 id="día-de-la-industria">2/9 Día de la Industria</h1>
<h2 id="evaluación-2-posta">Evaluación 2 (Posta)</h2>
<p><a href="https://drive.google.com/file/d/1aOIVdW3ytbapwf1AdwSFsQgkAEltUqaA/view"><strong>CLASE</strong></a></p>
<h1 id="día-del-inmigrante">4/9 Día del Inmigrante</h1>
<h2 id="inteligancia-artificial-responsable">Inteligancia Artificial Responsable</h2>
<blockquote>
<p>Cancion de Dia: <a href="https://open.spotify.com/intl-es/track/34sOdxWu9FljH84UXdRwu1?si=b92d5bbb57f84ed8">All american bitch - Olivia Rodrigo</a></p>
</blockquote>
<p><a href="https://sites.google.com/view/etica-practica-cd/recursos?authuser=0">Etica para Ciencia de Datos, RECURSOS</a><br>
Sesgo estadistoco ta todo biem, pero los sesgos sociales<br>
<a href="https://drive.google.com/file/d/1m63wGShBGgN956PEawKdscwMZ2uEZmpN/view"><strong>CLASE</strong></a></p>
<h1 id="día-mundial-del-trastorno-del-espectro-alcohólico-fetal">9/9 Día Mundial del Trastorno del Espectro Alcohólico Fetal</h1>
<h2 id="modelos-de-lenguaje">Modelos de Lenguaje</h2>
<p>Modelos Macrobianos --&gt; Conditional Random Fields --&gt; RNs</p>
<p><a href="https://jalammar.github.io/illustrated-word2vec/">The Illustrated Word2Vec</a></p>
<p><a href="https://jalammar.github.io/illustrated-transformer/">The Illustrated Transformer</a></p>
<p><a href="https://jalammar.github.io/illustrated-gpt2/">The Illustrated GPT2</a></p>
<p><a href="https://jalammar.github.io/illustrated-bert/">The Illustrated BERT, ELMo, and co. (How NLP Cracked Transfer Learning)</a></p>
<p>Tareas de Pretexto, generacion artificial de ejemplosss.</p>
<ul>
<li>Variaciones en una Imagen, color, saturacion bla bla, desordenar en cuadritos</li>
<li>Quitar palabras de una oraciones</li>
</ul>
<p>Las maquinas siempre son las mismas, pero mejora la perfo. Todo bien pero hay que ‘desmemmorizar’, eh aqui los tranformers pueden ser mas abstastos y sin necesidad de memorizar.</p>
<p><a href="https://colab.research.google.com/github/nanom/llm_adaptation_2nlp_workshop/blob/main/notebook.ipynb"><mark><em><strong>Notebook Fine-Tuning</strong></em></mark></a></p>
<p><a href="https://www.databricks.com/blog/efficient-fine-tuning-lora-guide-llms">Efficient Fine-Tuning with LoRA: A Guide to Optimal Parameter Selection for Large Language Models</a></p>
<p><a href="https://colab.research.google.com/github/GoogleCloudPlatform/generative-ai/blob/main/language/orchestration/langchain/intro_langchain_palm_api.ipynb#scrollTo=c38fe99f"><mark><em><strong>Notebook LangChain</strong></em></mark></a></p>
<p><a href="https://huggingface.co/learn/nlp-course/chapter1/1">Curso NLP HuggingFace</a></p>
<h1 id="dia-de-cataluña-dia-del-maestro">11/9 Dia de cataluña, Dia del maestro</h1>
<h2 id="nosupervisado">Nosupervisado</h2>
<blockquote>
<p><em><strong>Cancion del dia:</strong></em> <a href="https://www.youtube.com/watch?v=uMshgHF9Gso">Red Wine Supernova - Chapell Roan</a></p>
</blockquote>
<p><a href="https://medium.com/analytics-vidhya/latent-dirichelt-allocation-1ec8729589d4">Latent Dirichlet Allocation</a></p>
<p><a href="https://colab.research.google.com/github/gal-a/blog/blob/master/docs/notebooks/nlp/nlp_tf-idf_clustering.ipynb#scrollTo=pYqkfe2b9q2u"><mark><em><strong>Notebook non-supervised</strong></em></mark></a></p>
<p><a href="https://docs.google.com/presentation/d/1_qMyMAkwjHdapEektl0LKQjvaJSETFZe/edit?rtpof=true&amp;sd=true"><em><strong>SLIDES 1 USADOS</strong></em></a></p>
<p><a href="https://docs.google.com/presentation/d/1lD3U1b3W5cs6oc0FKGDWy5vn9r41M0Y3/edit#slide=id.p1"><em><strong>SLIDES 2 USADOS</strong></em></a></p>
<h1 id="día-internacional-del-espeleólogo">16/9 Día Internacional del Espeleólogo</h1>
<h2 id="hate-speech-detection">Hate speech detection</h2>
<p><em><strong>TF - IDF</strong></em> normalizacion (sirve para pocos datos)</p>
<p><a href="https://arxiv.org/abs/2106.09462">PAPER: pysentimiento: A Python Toolkit for Opinion Mining and Social NLP tasks</a><br>
<a href="https://colab.research.google.com/github/pysentimiento/pysentimiento/blob/master/notebooks/examples/pysentimiento_sentiment_analysis_in_spanish.ipynb"><mark><em><strong>Notebook pySentimiento</strong></em></mark></a><br>
<a href="https://drive.google.com/file/d/1eok_nC2sfS-tVmxqQdOqA_NbCPCpiCJ7/view">CLASE</a></p>
<h1 id="día-internacional-del-ventilador">18/9 Día Internacional del Ventilador</h1>
<h2 id="discurso-de-odio-y-argumentación">Discurso de odio y Argumentación</h2>
<blockquote>
<p><em><strong>Cancion del dia:</strong></em> <a href="https://youtu.be/KnGSVIZGkQo?list=PLuJvP70U5L0tc-aIMe8ALcRvqPVjgN085">FKA twigs - Eusexua</a></p>
</blockquote>
<p><a href="https://docs.google.com/presentation/d/1f1u8NCgGChVgAeMC4-hfRXoqs_6V4YojBOKO65gcasY/edit#slide=id.p"><em><strong>SLIDES</strong></em></a></p>
<p>Propuesta contranarrativa del discurso de odio, no solo una repuesta, enfasis en <strong>propositiva</strong>.</p>
<p><a href="https://drive.google.com/file/d/1ykZDc7r65cqoEO7xlC77wquPGr_TJBmt/view"><strong>CLASE</strong></a></p>
<h1 id="día-de-las-bibliotecas-populares">23/9 Día de las Bibliotecas Populares</h1>
<h2 id="traducción-automática">Traducción Automática</h2>
<p><a href="https://drive.google.com/file/d/1gqFjUTmOO7eVCTTvivCQwKyHYSg6aTFr/view">CLASE</a><br>
<mark>Metricas</mark><br>
BLEU<br>
BERT score<br>
Vauquois Triangle</p>
<p><strong>Allocation</strong></p>
<ul>
<li>IBM1: Correspondencia 1a1 de palabras</li>
<li>IBM2: Scuancia a secuencia</li>
</ul>
<p><strong>Traduccion Neuronal</strong></p>
<h1 id="día-internacional-de-la-traducción">30/9 Día Internacional de la Traducción</h1>
<h2 id="semisupervisado">Semisupervisado</h2>
<p><a href="https://drive.google.com/file/d/1oKujo1sGUP-DJgESdnDjYTN4Efj-7Cy7/view">CLASE</a><br>
Autoaprendizaje</p>
<h1 id="día-mundial-del-correo">9/10 Día Mundial del Correo</h1>
<h2 id="adquisicion-lexica">Adquisicion Lexica</h2>
<p>Términos multipalabra – Capítulo 5 de Manning &amp; Schütze 1999</p>
<p><em><strong>Información Mútua (e información mútua puntual)</strong></em></p>
<ul>
<li>identificamos secuencias de palabras cuyo número de ocurrencias juntas es significativo con respecto a su número de ocurrencias separadas</li>
</ul>
<blockquote>
<p>Para daatasets chicos puede performar mal, pues la asuncion de MI es que los datos subyacen en una gausiana falso, minimas diferencias de conteo de palabras en datasets chicos disparan diferencias grandes en MI</p>
</blockquote>
<p><em><strong>Alternativas</strong></em></p>
<ul>
<li>likelihood ratio, chi cuadrado</li>
<li>alternativas ingenieriles: reservar masa de probabilidad para eventos poco frecuentes o no vistos</li>
</ul>
<p>Para secuencias no coninuas, se varian todos los n-gramas sobre la oracion, la <strong>ventana deslizante</strong>. El largo alcance de RNNs le da potencia a las ventanas para reconocer correlaciones ‘lejanas’.</p>
<p>PAPER: <a href="https://www.patrickpantel.com/download/papers/2002/kdd02.pdf">Discovering Word Senses from Text</a></p>
<p><a href="https://drive.google.com/file/d/1yqtaKS3fPbg5wKMMRkRZpMHjuix6MAwx/view">CLASE</a></p>
<h1 id="día-del-seguro">21/10 Día del Seguro</h1>
<h2 id="sistemas-de-dialogo-y-reinforcement-learning">Sistemas de Dialogo y Reinforcement Learning</h2>
<p><a href="https://drive.google.com/file/d/1Gq9Gm80yca75JlU6Q3czOt1xRh0PuqI0/view">CLASE.1</a></p>
<p><a href="https://drive.google.com/file/d/1iR6S-MVT2NZJdG2a4aGfxr-a72jl5ooG/view">CLASE.2</a></p>
<h1 id="día-del-mol">23/10 Día del Mol</h1>
<h2 id="sentiment-analysis-y-stance-detection">Sentiment analysis y Stance detection</h2>
<p><a href="https://drive.google.com/file/d/1e3pEfvdO_aOIokbh3iKY687ulnjY5u97/view">CLASE</a></p>

