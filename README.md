__word vectors__ for french.

vectors are trained with [Gensim](https://radimrehurek.com/gensim/) on 8 millions sentences and 170 millions tokens, using [word2vec](https://radimrehurek.com/gensim/models/word2vec.html) algorithm (CBOW) and have 100 dimensions.

training data
-------------

the training data is an aggregation of existings corpora (mostly from [Ortolang](https://www.ortolang.fr/fr/accueil/)) available in Creative Common Licenses and books from [Wikisource](https://fr.wikisource.org/wiki/Wikisource:Accueil). all texts have been tokenized using [jusqucy](https://github.com/thjbdvlt/jusquci) tokenizer and normalized with [commecy](https://github.com/thjbdvlt/commecy) normalizer.

### linguistic corpora

- [WikiDisc](https://www.ortolang.fr/market/corpora/wikidisc), a corpus of Wikipedia discussions[^1].
- [Corpus Reporterre](https://www.ortolang.fr/market/corpora/corpus-reporterre), corpus made of articles published in the newspaper Reporterre[^3].
- [CFPR, Corpus Français Parlé de nos Régions](https://cfpr.huma-num.fr/), an oral corpus from which i've only used transcriptions.
- [Fr-EngClimateIPCC](https://www.ortolang.fr/market/corpora/fr-engclimateipcc?lang=en), a corpus that uses GIEC reports[^Climate].


[^1]: Lydia-Mai Ho-Dac, Veronika Laippala. _Le corpus WikiDisc : ressource pour la caractérisation des discussions en ligne_. Wigham, Ciara R.; Ledegen, Gudrun. Corpus de communication médiée par les réseaux : construction, structuration, analyse., l'Harmattan, pp.107-124, 2017, Humanités numériques, 978-2-343-11212-1. 

[^3]: Laboratoire de Linguistique et Didactique des Langues Etrangères et Maternelles - EA 609 (LIDILEM) (2024). _Corpus Reporterre_ [Corpus]. ORTOLANG (Open Resources and TOols for LANGuage) - www.ortolang.fr, v1, https://hdl.handle.net/11403/corpus-reporterre/v1. 

[^Climate]: Alice Breton, Lila Sainero, Ertuğrul Kaşıkçı, et al. (2025). *Fr-EngClimateIPCC* [Corpus]. ORTOLANG (Open Resources and TOols for LANGuage) - www.ortolang.fr, v2, https://hdl.handle.net/11403/fr-engclimateipcc/v2.

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
for mot in ("corriger", "écrire", "semblable"):
    print(mot.upper())
    pprint.pprint(wv.most_similar(mot))
```
```txt
CORRIGER
[('rectifier', 0.9477892518043518),
 ('reformuler', 0.8014981150627136),
 ('retoucher', 0.7997115254402161),
 ('revérifier', 0.7786833047866821),
 ('compléter', 0.7700492739677429),
 ('réinsérer', 0.7668392062187195),
 ('réintroduire', 0.7586169838905334),
 ('neutraliser', 0.7517247200012207),
 ('relire', 0.7496525645256042),
 ('retravailler', 0.7478603720664978)]
ÉCRIRE
[('rédiger', 0.7746878862380981),
 ('introduire', 0.7624995112419128),
 ('éditer', 0.7496927380561829),
 ('lire', 0.7458739876747131),
 ('interpréter', 0.7435053586959839),
 ('ajouter', 0.742584764957428),
 ('utiliser', 0.7347964644432068),
 ('expliquer', 0.7102205157279968),
 ('insérer', 0.709247350692749),
 ('exposer', 0.705054521560669)]
SEMBLABLE
[('analogue', 0.8588128089904785),
 ('similaire', 0.8226010203361511),
 ('comparable', 0.7327669262886047),
 ('identique', 0.6808283925056458),
 ('ressemblant', 0.6401993036270142),
 ('différente', 0.6140844821929932),
 ('réfractaire', 0.6018397808074951),
 ('empruntée', 0.5857769250869751),
 ('lié', 0.5668148994445801),
 ('équivalente', 0.5665000677108765)]
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
