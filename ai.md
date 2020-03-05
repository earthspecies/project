<img src="https://raw.githubusercontent.com/earthspecies/roadmaps/master/images/ai/image_0.png" alt="ESP Logo" width="200px">

## Earth Species Project

An open-source collaborative and nonprofit dedicated to decoding animal communication.

This document aims to track the high-level technical approach towards the translation of non-human languages.

### Contributing

If you would like to propose changes, new directions, or references you can click on the small edit button in the top-right corner of this document. When you are done, you'll be asked for a name for your proposed change and a description of the change. Select "Create a new branch for this commit and start a pull request" and then  "Propose file change".

## BACKGROUND

In 2013, T. Mikolov et al<sup>[1](#footnotes)</sup> proposed an efficient unsupervised algorithm that represents words as points in a high-dimension space, where the distance and direction between points encodes the relationship between words. This mapping of the words in a language to a geometric structure is known as a '[word embedding](http://jalammar.github.io/illustrated-word2vec/)’.

![Example of the word embeddings for English](https://raw.githubusercontent.com/earthspecies/roadmaps/master/images/ai/image_1.png)

<span style="font-size:80%;padding:20px;">An example of a geometric representation, an ‘embedding,’ of the top 10,000 most spoken words in English. While each word is actually represented by a point in hundreds of dimensions, here it is projected down to three for visualization. The hundreds of axes are semantically meaningful but hard to interpret.</span>

The ability to represent words in a physical space sparked an explosion in the field of natural language processing and the research is foundational in all modern techniques. Contextual embeddings came more recently<sup>[2, ](#footnotes)</sup><sup>[3](#footnotes)</sup>, that use unsupervised neural networks to create embeddings that incorporate the deeper nuances of words, like their polysemy<sup>[4](#footnotes)</sup>.

One of the most striking properties of these embeddings is that analogies have geometric representation<sup>[5](#footnotes)</sup>, allowing for the comparison and mapping of the relationships between concepts, giving rise to both local and global structure.

![image alt text](https://raw.githubusercontent.com/earthspecies/roadmaps/master/images/ai/image_2.png)

<div style="font-size:80%;padding:20px;">A schematic representation of an embedding projected to two dimensions. You can see how analogous pairs of words share the same geometric relationships. The geometry of an embedding represents the structure of the language’s internal relationships.</div>

## TRANSLATION

Imagine being given two entirely unknown languages and that just by analyzing each for long enough you could discover how to translate between them.

In late 2017, A. Conneau et al<sup>[6](#footnotes)</sup> and M. Artetxe et al<sup>[7](#footnotes)</sup> demonstrated how to do exactly that: to translate between unknown languages without the need for a Rosetta Stone, dictionary, or any examples of translation.

> "There is now a way to learn to translate between, say, Urdu and English by having access only to text in English and completely unrelated text in Urdu – without having any of the respective translations."
>
> – Guillaume Lample, Facebook AI Research (2018)

The method is as elegant as its implications are profound: align the languages’ embeddings by rotating one over the other until their shapes match. This aligns the structure of their internal relationships so the points of one language are overlaid with the points from a second language. To translate a word, you find the point in the second language closest to the word’s point in the first language.

![image alt text](https://raw.githubusercontent.com/earthspecies/roadmaps/master/images/ai/image_3.png)

<div style="font-size:80%;padding:20px;">Human languages appear to share the same rough structure. You can translate between languages by matching their structures.</div>

These multi-lingual embeddings—sometimes called universal embeddings<sup>[8](#footnotes)</sup>–are used by the major tech companies in their modern machine translation products<sup>[9](#footnotes)</sup>.

In late 2018, these unsupervised techniques were extended from text to audio. A paper from James Glass’ lab at MIT<sup>[10](#footnotes)</sup> demonstrated that recorded spoken language can also be turned into a geometric embedding alignable with written text. The paper translates from German audio to French text, requiring an acoustic data set of only a couple hundred hours.

## TOWARDS DECODING ANIMAL LANGUAGE

Taken together, these new techniques form deep comparative tools for the exploration of languages without dictionaries. They identify previously unrecognizable communications systems and create a rich toolset to translate them into the human experience.

To tackle the problem, we are building an open-source toolkit, data sets, benchmarks, and community for unsupervised translation that incorporates a focus on non-human languages with state-of-the-art academic research.

**ROADMAP:**

*Areas of Research*

* **Extending unsupervised translation of audio to increasingly difficult human languages.** Moving from the Indo-European languages to the Silbo Gomerian whistle language and beyond. This work creates a set of milestones that will teach us the power and nuance of our tools as we begin research on languages that have no current translation.  
* **Better unsupervised multilingual dictionary alignment**. Some (but not all) of the techniques used to align embeddings exploit similarities in morphology across human languages. We are focusing on extending techniques that do not make this assumption.
* **Abstracted meaning**. For non-human languages the objective isn’t perfect sentence translation, but to understand their meaning in an abstracted way.
* **Modality inference.** We are extending comparative embedding analysis towards inferring the type of data a corpus contains. By comparing an unknown embedding to embeddings of human languages, music, images, 3D models, etc., we can infer the kind of experience that is being communicated, getting us closer to the question: What is it *‘like’* to be another species?
* **Cross-modality translation.** Human and non-human communication can be extra-linguistic: The many sign languages are a perfect candidate for attempting unsupervised translation by aligning their embedding of a visual communication (sign language, facial and postural language, etc) with the embeddings of a written or spoken language.

**CHALLENGES**

**The Umwelt Problem**

To what extent is the experience-of-the world for different species translatable? Can an experience in the umwelt of one species be translated by analogy into terms understandable by the other?

For primates, it seems likely we have significant umwelt overlap, but even with cetaceans there are reasons to be hopeful: We share being social mammals living in the same physical world, we are live-born, breath to live, have families, relationships, personalities, and complex evolving cultures. Our roadmap includes determining what experientiality between species is translatable.

At the same time, we are taking a bottom-up approach: we can learn a lot by comparing the embedding structures of, say, many individual sperm whales: analyzing how they change between individuals and pods; amongst clans and cultures; between captive populations and wild ones; over time; and from one species to a related species.

**The Carrier-Signal and Cocktail Party Problems**

One of the difficulties in decoding an unknown vocalized language is determining the part of the signal which encodes the parts that matter: Is it tone, pitch, tempo, rhythm, repetition, harmonic structure, or some other attribute entirely that matters? This is the carrier-signal problem.

![image alt text](https://raw.githubusercontent.com/earthspecies/roadmaps/master/images/ai/image_4.png)

<div style="font-size:80%;padding:20px;">A hyper-resolution<sup><a href="#footnotes">11, </a></sup><sup><a href="#footnotes">12</a></sup> spectrogram of a single dolphin whistle with two echolocation clicks, showing the calls fine structure.</div>

*Resolving which part of this signal is meaningful is an unsolved problem.*

The cocktail party problem is the task of separating out an individual speaker from a complex acoustic signal with multiple speakers and background noise.

Deep learning, unsupervised language models, and rich embeddings are giving us massive new computation tools to tackle these problems.

For example, instead of using embedding alignment to translate between species, we can use the same technique to translate between individuals *in the same species*. This lets us discover all the different ways of saying the same thing. This in turn lets us see which part of the sound matters: that is, discover which part of the sound is true signal and which part is background carrier.

### Footnotes

1. T. Mikolov, K. Chen, G. Corrado: "Efficient Estimation of Word Representations in Vector Space", 2013; http://arxiv.org/abs/1301.3781
2. M. Peters, M. Neumann, M. Iyyer, M. Gardner, C. Clark, K. Lee: "Deep contextualized word representations", 2018; http://arxiv.org/abs/1802.05365
3. Tal Schuster, Ori Ram, Regina Barzilay: “Cross-Lingual Alignment of Contextual Word Embeddings, with Applications to Zero-shot Dependency Parsing”, 2019; <a href='http://arxiv.org/abs/1902.09492'>arXiv:1902.09492</a>.
4. K. Ethayarajh: “How Contextual are Contextualized Word Representations? Comparing the Geometry of BERT, ELMo, and GPT-2 Embeddings”, 2019; https://www.aclweb.org/anthology/D19-1006.pdf.
5. K. Ethayarajh, D. Duvenaud, G. Hirst: “Towards Understanding Linear Word Analogies”, 2018; <a href='http://arxiv.org/abs/1810.04882'>arXiv:1810.04882</a>.
6. A. Conneau, G. Lample, M. Ranzato, L. Denoyer: "Word Translation Without Parallel Data", 2017; http://arxiv.org/abs/1710.04087
7. M. Artetxe, G. Labaka, E. Agirre: “Unsupervised Neural Machine Translation”, 2017; http://arxiv.org/abs/1710.11041
8. D. Cer, Y. Yang, S. Kong, N. Hua, N. Limtiaco, R. John, N. Constant, M. Guajardo-Cespedes, S. Yuan, C. Tar, Y. Sung, B.: "Universal Sentence Encoder", 2018; http://arxiv.org/abs/1803.11175
9. MUSE: Multilingual Unsupervised and Supervised Embeddings; https://github.com/facebookresearch/MUSE
10. Y. Chung, W. Weng, S. Tong, J. Glass: "Unsupervised Cross-Modal Alignment of Speech and Text Embedding Spaces", 2018; http://arxiv.org/abs/1805.07467
11. T. Gardner, M. Magnasco: "Sparse time-frequency representations", 2006 PNAS; https://doi.org/10.1073/pnas.0601707103
12. Earth Species's Pythonic Implementation of Linear Reassignment and Spectral Hyper-resolution: https://github.com/earthspecies/spectral_hyperresolution
