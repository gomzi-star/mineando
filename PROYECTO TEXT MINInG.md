---


---

<p><em><strong>Tools:</strong></em></p>
<ul>
<li><a href="https://huggingface.co/PleIAs/OCRonos">PleIAs/OCRonos · <mark>Hugging Face</mark></a> : OCR Post-Process</li>
<li><a href="https://github.com/gretelai/gretel-synthetics">Gretel Synthetics · <mark>GitHub</mark></a>: Pago :(</li>
<li><a href="https://github.com/microsoft/dp-transformers">dp-transformers · <mark>GitHub</mark></a>: DP finetune</li>
<li><a href="https://github.com/AI-secure/aug-pe">aug-pe · <mark>GitHub</mark></a>: DP prompt (PE)</li>
<li><a href="https://huggingface.co/meta-llama/Meta-Llama-3.1-8B-Instruct">Meta-Llama-3.1-8B-Instruct · <mark>Hugging Face</mark></a></li>
<li><a href="https://huggingface.co/mistralai/Mistral-Nemo-Instruct-2407">Mistral-Nemo-Instruct-2407 · <mark>Hugging Face</mark></a></li>
<li><a href="https://huggingface.co/bigscience/bloom">bloom · <mark>Hugging Face</mark></a></li>
<li><a href="https://huggingface.co/flax-community/gpt-2-spanish">gpt-2-spanish · <mark>Hugging Face</mark></a></li>
<li><a href="https://docs.python.org/3/library/re.html">Regular expression operations</a></li>
<li><a href="https://huggingface.co/iiiorg/piiranha-v1-detect-personal-information?text=27+de+Abril+al+2000">piiranha-v1-detect-personal-information · <mark>Hugging Face</mark></a></li>
<li><a href="https://spacy.io/usage/spacy-101">spaCy</a></li>
<li><a href="https://chunkviz.up.railway.app/">ChunkViz</a>: Visualizacion de Chunk (Character y Recursive)</li>
<li><a href="https://github.com/FullStackRetrieval-com/RetrievalTutorials/blob/main/tutorials/LevelsOfTextSplitting/5_Levels_Of_Text_Splitting.ipynb">5 Levels Of Text Splitting</a></li>
</ul>
<p><img src="https://alphapav.github.io/augpe-dpapitext/static/images/method.png" alt="illustrative-example"></p>
<ul>
<li><strong>Step 1 (RANDOM_API):</strong>  we use prompts to generate random samples from the LLM.</li>
<li><strong>Step 2:</strong>  we iteratively go through steps 2.1-2.3 to refine the synthetic samples towards the private samples.
<ul>
<li><strong>Step 2.1:</strong>  each private sample votes for their closest synthetic sample in the embedding space induced by embedding model. “A great spot for pizza” gets 2 votes, and the other sample gets 0 votes. We then add Gaussian noise to the votes to ensure DP. This gives us the  <strong>DP Nearest Neighbor Histogram (DP_NN_HISTOGRAM).</strong></li>
<li><strong>Step 2.2:</strong>  we resample the generated texts according to the histogram. We assume that only “A great spot for pizza” remains.</li>
<li><strong>Step 2.3 (VARIATION_API):</strong>  we use prompts to ask the LLM to generate new similar samples, which will be used in the initial synthetic samples for the next iteration.<br>
<em><strong>Datasets</strong></em></li>
</ul>
</li>
<li><a href="https://huggingface.co/datasets/ai4privacy/pii-masking-300k/viewer/default/train?f%5Blanguage%5D%5Bvalue%5D=%27Spanish%27&amp;row=148907">https://huggingface.co/datasets/ai4privacy/pii-masking-300k/viewer/default/train?f[language][value]='Spanish'&amp;row=148907</a></li>
</ul>
<p><em><strong>Papers:</strong></em></p>
<ul>
<li><a href="https://drive.google.com/open?id=11r9C6AYiOOHMV9hhXRmeAl2EApwkoDrP&amp;usp=drive_fs">Survey of Post-OCR Processing Approaches</a></li>
<li><a href="https://drive.google.com/open?id=10cdcv4rk7ymZmQhCSSBK1qaWE0O3ZmK9&amp;usp=drive_fs">CTRL</a></li>
<li><a href="https://drive.google.com/open?id=105fOMEQiZ9p0oq6BsIP1eHgIkv3aSV5h&amp;usp=drive_fs">Synthetically generated text for supervised text analysis</a>: Teorico</li>
<li><a href="https://drive.google.com/open?id=11SF0GMG5nNHbd-dxt_hCn5Y-JhtAJFOq&amp;usp=drive_fs">Synthetic Text Generation with Differential Privacy - A simple and Practical Recipe</a>: <strong>DP</strong> finetuneando GPT2, usando CTRL tambien</li>
<li><a href="https://drive.google.com/open?id=112-ABUi2Qd6vOFUZYKWJkYPHb6sYVdIp&amp;usp=drive_fs">Differentially Private Synthetic Data via Foundation Model APIs 2: Text</a>: <strong>DP</strong> con <em><strong>PE</strong></em> (Private Evolution) <em>‘Prompteado Privado’ si es que esiste eso</em> con GPT3.5</li>
<li><a href="https://drive.google.com/open?id=11aaTJqEBM3URVm0Z2gK0gPcZiGTzZKOx&amp;usp=drive_fs">Privacy-Preserving Instructions for Aligning Large Language Models</a>: <em><strong>DP</strong></em> finetuneando Llama</li>
<li><a href="https://drive.google.com/open?id=11r7qcrIiOH1XnaaAUP6KitO0PD3mVuIr&amp;usp=drive_fs">Private prediction for large-scale synthetic text generation</a>: <em><strong>DP</strong></em> con <em><strong>PP</strong></em> (Private Prediction) en Gemma</li>
</ul>
<p><em><strong>Libros:</strong></em></p>
<ul>
<li><a href="https://programming-dp.com/cover.html">Programming Differential Privacy</a>: Libro sobre <strong>DP</strong></li>
<li><a href="https://drive.google.com/open?id=123gsFI_cLnM32D0y5ntswcaNQIhvmomR&amp;usp=drive_fs">The Algorithmic Foundations of Differential Privacy</a>: Otro libro sobre <strong>DP</strong></li>
</ul>
<p><em><strong>Otro:</strong></em></p>
<ul>
<li><a href="https://arxiv.org/pdf/2305.17333">Fine-Tuning Language Models with Just Forward Passes</a></li>
<li><a href="https://shairozsohail.medium.com/reading-and-categorizing-scanned-documents-using-deep-learning-4ab2c0e3f34c">Reading and Categorizing Scanned Documents using Deep Learning</a></li>
<li><a href="https://arxiv.org/pdf/2302.00539">https://arxiv.org/pdf/2302.00539</a></li>
</ul>
<p><a href="https://drive.google.com/drive/folders/1IqlNGfmTxmIHW6rRZ73cuQsxAn_j0uVo?usp=sharing"><strong>DRIVE CON TODO</strong></a></p>

