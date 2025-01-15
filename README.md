__word vectors__ for french.

vectors are trained with [Gensim](https://radimrehurek.com/gensim/) on 8 millions sentences and 170 millions tokens, using [word2vec](https://radimrehurek.com/gensim/models/word2vec.html) algorithm (CBOW) and have 100 dimensions.

training data
-------------

the training data is an aggregation of existings corpora (mostly from [Ortolang](https://www.ortolang.fr/fr/accueil/)) available in Creative Common Licenses and books from [Wikisource](https://fr.wikisource.org/wiki/Wikisource:Accueil). all texts have been tokenized using [jusqucy](https://github.com/thjbdvlt/jusquci) tokenizer and normalized with [commecy](https://github.com/thjbdvlt/commecy) normalizer.

### linguistic corpora

- [WikiDisc](https://www.ortolang.fr/market/corpora/wikidisc), a corpus of Wikipedia discussions[^1].
- [Corpora Collection Leipzig](https://wortschatz.uni-leipzig.de/en/download/French), corpora for many languages and regions. i've download files (30K-1M sentences each) for following regions: Belgique, Cameroun, Congo, Côte d'Ivoire, France, Luxembourg, Madagascar, Nouvelle Calédonie, Polynésie Française, Suisse, Togo[^2].
- [Corpus Reporterre](https://www.ortolang.fr/market/corpora/corpus-reporterre), corpus made of articles published in the newspaper Reporterre[^3].
- [CFPR, Corpus Français Parlé de nos Régions](https://cfpr.huma-num.fr/), oral corpus (i only used transcriptions).

[^1]: Lydia-Mai Ho-Dac, Veronika Laippala. _Le corpus WikiDisc : ressource pour la caractérisation des discussions en ligne_. Wigham, Ciara R.; Ledegen, Gudrun. Corpus de communication médiée par les réseaux : construction, structuration, analyse., l'Harmattan, pp.107-124, 2017, Humanités numériques, 978-2-343-11212-1. 

[^2]: D. Goldhahn, T. Eckart & U. Quasthoff: _Building Large Monolingual Dictionaries at the Leipzig Corpora Collection: From 100 to 200 Languages_. In: Proceedings of the 8th International Language Resources and Evaluation (LREC'12), 2012.

[^3]: Laboratoire de Linguistique et Didactique des Langues Etrangères et Maternelles - EA 609 (LIDILEM) (2024). _Corpus Reporterre_ [Corpus]. ORTOLANG (Open Resources and TOols for LANGuage) - www.ortolang.fr, v1, https://hdl.handle.net/11403/corpus-reporterre/v1. 

### wikisource

texts from these authors:

 - Alexandre Dumas
 - André Gide
 - Charles Augustin Sainte-Beuve
 - Charles-Henri Favrod
 - Colette
 - Émile Durkheim
 - Fédor Dostoïevski
 - George Sand
 - Jack London
 - Joseph Texte
 - Jules Verne
 - Juliette Lalonde-Rémillard
 - Leandro Despouy
 - Léon Tolstoï
 - Lucien Fabre
 - Ludwig Wittgenstein
 - Marcel Mauss
 - Marcel Proust
 - Michelle LeNormand
 - Philippe Tamizey de Larroque
 - Pierre Kropotkine
 - Rachilde
 - Robert Carmille
 - Simone Weil
 - Solange Fernex
 - Uppaluri Gopala Krishnamurti

example
-------

```python
from gensim.models import KeyedVectors
import pprint

# load word vectors
wv = KeyedVectors.load_word2vec_format('vectors.bin', binary=True)

# most similar words
for mot in (
    "écrire", "lire", "semblable", "humaine", "nature",
):
    print(mot.upper())
    pprint.pprint(wv.most_similar(mot))
```

```txt
```

use with spacy
--------------

to use the vectors with [spacy](https://spacy.io/), one need to convert the vectiors to text format.

```python
from gensim.models import KeyedVectors

# load binary word vectors
wv = KeyedVectors.load_word2vec_format('vector.bin', binary=True)

# save text word vectors
wv.save_word2vec_format('model.word2vec', binary=False)
```

create the vectors for a pipeline from file:

```bash
spacy init vectors fr model.word2vec vectors
```
