__word vectors__ pour le français (`word2vec`, 100 dimensions, CBOW), entraînés avec [Gensim](https://radimrehurek.com/gensim/).

le corpus utilisé est constitué d'environ 22 millions de phrases et 500 millions de tokens, provenant de différents corpus (normalisés, et plus ou moins modifiés) et de textes littéraires (ou scientifiques) sous licence libres ou dans le domaine public.

exemple
=======

```python
from gensim.models import KeyedVectors
import pprint

# load word vectors
wv = KeyedVectors.load_word2vec_format('model.bin', binary=True)

# most similar words
for mot in (
    "écrire", "lire", "semblable", "humaine", "nature",
):
    print(mot.upper())
    pprint.pprint(wv.most_similar(mot))
```

```
ÉCRIRE
[('lire', 0.7958993911743164),
 ('interpréter', 0.7516734600067139),
 ('éditer', 0.7383493781089783),
 ('rédiger', 0.7355990409851074),
 ('apprendre', 0.7343490123748779),
 ('utiliser', 0.7281709313392639),
 ('inventer', 0.7118361592292786),
 ('employer', 0.7102519273757935),
 ('écouter', 0.7078548073768616),
 ('appeler', 0.702791690826416)]


LIRE
[('relire', 0.8466554880142212),
 ('regarder', 0.8015256524085999),
 ('écrire', 0.7958993315696716),
 ('consulter', 0.7852454781532288),
 ('publier', 0.7608461380004883),
 ('recopier', 0.7554864883422852),
 ('feuilleter', 0.7442073822021484),
 ('rédiger', 0.7388473153114319),
 ('poster', 0.7297687530517578),
 ('voir', 0.7152807712554932)]


SEMBLABLE
[('similaire', 0.8344558477401733),
 ('analogue', 0.8341560363769531),
 ('comparable', 0.799608051776886),
 ('identique', 0.7407772541046143),
 ('ressemblant', 0.738508403301239),
 ('apparentée', 0.6046147346496582),
 ('lié', 0.600321888923645),
 ('différente', 0.5880765318870544),
 ('assimilable', 0.5812517404556274),
 ('réfractaire', 0.5703239440917969)]


HUMAINE
[('animale', 0.7537525296211243),
 ('spirituelle', 0.7472118735313416),
 ('surnaturelle', 0.7453622817993164),
 ('immatérielle', 0.7149630188941956),
 ('réelle', 0.7088828086853027),
 ('innée', 0.7061097025871277),
 ('naturelle', 0.703719437122345),
 ('fondamentale', 0.6810879111289978),
 ('émotionnelle', 0.6754382252693176),
 ('sous-jacente', 0.6738153100013733)]


NATURE
[('faune', 0.6992893218994141),
 ('biodiversité', 0.6951753497123718),
 ('diversité', 0.6917913556098938),
 ('perception', 0.691189706325531),
 ('richesse', 0.6776712536811829),
 ('dignité', 0.6773139238357544),
 ('contemplation', 0.6590573191642761),
 ('matérialité', 0.657234251499176),
 ('réalité', 0.6533279418945312),
 ('fragilité', 0.651949942111969)]
```

sources
=======

corpus linguistiques
--------------------

- [WikiDisc](https://www.ortolang.fr/market/corpora/wikidisc), un corpus de discussions Wikipedia[^1].
- [Corpora Collection Leipzig](https://wortschatz.uni-leipzig.de/en/download/French), un ensemble de corpus de divers langues et régions[^2]. J'ai téléchargé des fichiers (entre 30'000 et 1'000'000 phrases chacun) pour les régions suivantes: Belgique, Cameroun, Congo, Côte d'Ivoire, France, Luxembourg, Madagascar, Nouvelle Calédonie, Polynésie Française, Suisse, Togo.
- [Corpus Reporterre](https://www.ortolang.fr/market/corpora/corpus-reporterre), un corpus d'articles du média en ligne Reporterre.
- [CFPR, Corpus Français Parlé de nos Régions](https://cfpr.huma-num.fr/), corpus oral dont j'ai utilisé uniquement les transcriptions.

[^1]: Référence: _Lydia-Mai Ho-Dac, Veronika Laippala. Le corpus WikiDisc : ressource pour la caractérisation des discussions en ligne. Wigham, Ciara R.; Ledegen, Gudrun. Corpus de communication médiée par les réseaux : construction, structuration, analyse., l'Harmattan, pp.107-124, 2017, Humanités numériques, 978-2-343-11212-1_. 

[^2]: Référence: _D. Goldhahn, T. Eckart & U. Quasthoff: Building Large Monolingual Dictionaries at the Leipzig Corpora Collection: From 100 to 200 Languages. In: Proceedings of the 8th International Language Resources and Evaluation (LREC'12), 2012_.

textes littéraires et scientifiques
-----------------------------------

- des textes de ludwig wittgenstein, depuis le site [the wittgenstein project](https://www.wittgensteinproject.org/w/index.php?title=Main_Page):
    - [_conférence sur l'éthique_](https://www.wittgensteinproject.org/w/index.php/Une_conf%C3%A9rence_sur_l%E2%80%99Ethique) (1929)
    - [_le cahier bleu_](https://www.wittgensteinproject.org/w/index.php/Blue_Book) et [_le cahier brun_](https://wittgensteinproject.org/w/index.php/Brown_Book) (trad. automatique avec [deepl](https://www.deepl.com/en/translator))

- divers textes dans le domaine public issus de [Wikisource](https://fr.wikisource.org/wiki/Wikisource:Accueil), dont:
    - marcel mauss
        - _les techniques du corps_ (1935)
        - _essais de sociologie_ (1971)
        - _mélange d'histoire des religions_, avec henri hubert (1909)
    - simone weil
        - _la condition ouvrière_ (1951, rédaction en 1934-1937)
        - _sur la science_ (1966, rédaction en 1929-1942)
    - jack london
        - _l'appel de la forêt_ (1903, trad. 1908)
        - _lettre au juge samuel_ (1910)
        - _construire un feu_ (1910, trad. 1924)
        - _le cabaret de la dernière chance_ (1913, trad. 1926)
        - _la peste écarlate_ (1915, trad. 1924)
        - _le vagabond des étoiles_ (1915, trad. 1925)
    - rachilde
        - _refaire l'amour_ (1928)
        - _monsieur vénus_ (1884)
    - léon tolstoi
        - _qu'est-ce que l'art_ (1898, trad. 1918)
        - _guerre et paix_ (1864-1869, trad. 1903-1904)
        - _anna karénine_ (1873-1877, trad. 1906-1908)
    - marcel proust
        - _à la recherche du temps perdu_ (1913-1927, éd. 1946)
    - ...

- un texte issu de [the anarchist library](https://www.google.com/search?q=the%20anarchist%20library):
    - peter gelderloos, [_l'anarchisme fonctionne_](https://fr.anarchistlibraries.net/library/peter-gelderloos-anarchie-fonctionne) (2010, traduction par mikail marchand à l'aide de deepl)

- des textes littéraires édités par [FramaBook](https://archives.framabook.org/category/romans/index.html), sous Licence Art Libre:
    - gee, [_sortilèges et syndicats_](https://archives.framabook.org/working-class-heroic-fantasy/index.html) (2018)
    - pouhiou, [_smartarted_](https://archives.framabook.org/smartarded-le-cycle-des-noenautes-ii/index.html) (2012)
    - stephane crozat, [_traces_](https://archives.framabook.org/traces/index.html) (2018)
    - yann kervran, recueil [_quit'a_](https://archives.framabook.org/qita_01/index.html), vol.1-4 (2020), et [_les enquetes d'ernaud_](https://archives.framabook.org/la-nef-des-loups/index.html), t.1-3 (2017)

articles wikipedia
------------------

- article [_donnée_](https://fr.wikipedia.org/wiki/Donn%C3%A9e)
- article [_logiciel libre_](https://fr.wikipedia.org/wiki/Logiciel_libre)
- article [_copier-coller_](https://fr.wikipedia.org/wiki/Copier-coller)
- article [_commun_](https://fr.wikipedia.org/wiki/Communs)
- extraits de l'article [_football_](https://fr.wikipedia.org/wiki/Football) et [_lois du jeu_](https://fr.wikipedia.org/wiki/Lois_du_jeu)

usage avec spacy
================

pour utiliser ces vecteurs avec [spacy](https://spacy.io/). il faut d'abord convertir les vecteurs dans un format texte.

```python
from gensim.models import KeyedVectors

wv = KeyedVectors.load_word2vec_format('model.bin', binary=True)

wv.save_word2vec_format('model.word2vec', binary=False)
```

on peut ensuite créer les vecteurs l'aide de l'outil `spacy` en ligne de commande:

```bash
spacy init vectors fr model.word2vec vectors
```
