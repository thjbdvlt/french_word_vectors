__word vectors__ pour le français, entraînés avec [Gensim](https://radimrehurek.com/gensim/).

exemple
-------

```python
from gensim.models import KeyedVectors
import pprint

# load word vectors
wv = KeyedVectors.load_word2vec_format('model.bin', binary=True)

# most similar words
for mot in (
    "écrire", "lire", "iconique", "semblable", "humaine", "nature",
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


ICONIQUE
[('indémodable', 0.7322804927825928),
 ('futuriste', 0.7168718576431274),
 ('intemporel', 0.69966721534729),
 ('stylisé', 0.6945900321006775),
 ('vintage', 0.6915351748466492),
 ('montblanc', 0.6906726360321045),
 ('distinctive', 0.6773362159729004),
 ('multicolore', 0.6764605641365051),
 ('hipster', 0.6754564046859741),
 ('emblématique', 0.6742534041404724)]


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

le corpus utilisé est constitué d'environ 22 millions de phrases et 500 millions de tokens, provenant de différents corpus (normalisés, et plus ou moins modifiés) et de textes littéraires (ou scientifiques) sous licence libres ou dans le domaine public.

corpus linguistiques
--------------------

- [WikiDisc](https://www.ortolang.fr/market/corpora/wikidisc)[^1].
- [Corpora Collection Leipzig](https://wortschatz.uni-leipzig.de/en/download/French)[^2].
- [Corpus Reporterre](https://www.ortolang.fr/market/corpora/corpus-reporterre)[^3].
- [CFPR, Corpus Français Parlé de nos Régions](https://cfpr.huma-num.fr/)[^4].

[^1]: Un corpus de discussions Wikipedia. Référence: _Lydia-Mai Ho-Dac, Veronika Laippala. Le corpus WikiDisc : ressource pour la caractérisation des discussions en ligne. Wigham, Ciara R.; Ledegen, Gudrun. Corpus de communication médiée par les réseaux : construction, structuration, analyse., l'Harmattan, pp.107-124, 2017, Humanités numériques, 978-2-343-11212-1_. 

[^2]: Un ensemble de corpus de divers langues et régions. Référence: _D. Goldhahn, T. Eckart & U. Quasthoff: Building Large Monolingual Dictionaries at the Leipzig Corpora Collection: From 100 to 200 Languages. In: Proceedings of the 8th International Language Resources and Evaluation (LREC'12), 2012_. J'ai téléchargé des fichiers (entre 30'000 et 1'000'000 phrases chacun) pour les régions suivantes: Suisse, Luxembourg, Nouvelle Calédonie, Togo, Congo, Polynésie Française, Côte d'Ivoire, Belgique, France, Madagascar, Cameroun.

[^3]: Un corpus d'articles du média en ligne Reporterre.

[^4]: Corpus oral dont j'ai utilisé uniquement les transcriptions.

textes littéraires et scientifiques
-----------------------------------

- ludwig wittgenstein:
    - _conférence sur l'éthique_ (1929), sur le site the wittgenstein project
    - _le cahier bleu_ et _le cahier brun_ (traductions automatiques avec [deepl](https://www.deepl.com/en/translator))

- des textes littéraires avec license libre édités par FramaBook:
    - gee, _sortilèges et syndicats_ (2018, License Art Libre)
    - pouhiou, Smartarted, _Cycle des néonautes_, Livre I (2012, License Art Libre)
    - stephane crozat, _traces_ (2018)
    - yann kervran, recueil _quit'a_, vol.1-4 (2020), et _les enquetes d'ernaud_, vol.1-4 (2017)

- divers textes dans le domaine public issus de Wikisources, dont:
    - marcel mauss
        - _les techniques du corps_ (1935)
        - _essais de sociologie_ (1971)
        - _mélange d'histoire des religions_ (1909, avec henri hubert)
    - simone weil
        - _la condition ouvrière_ (1951)
        - _sur la science_
    - jack london
        - _l'appel de la forêt_ (1903 / 1908)
        - _lettre au juge samuel_ (1910)
        - _construire un feu_ (1910)
        - _le cabaret de la dernière chance_ (1913 / 1926)
        - _la peste écarlate_ (1915 / 1924)
        - _le vagabond des étoiles_ (1915 / 1925)
    - rachilde
        - _refaire l'amour_ (1928)
        - _monsieur vénus_
    - tolstoi
        - _guerre et paix_
        - _anna karénine_
    - marcel proust
        - _à la recherche du temps perdu_
    - ...

- un texte issu de the anarchist library:
    - peter gelderloos, _l'anarchisme fonctionne_

articles wikipedia
------------------

- article _donnée_
- article _logiciel libre_
- article _copier-coller_
- article _commun_
- extraits de l'article _règles du jeu du football_ et de l'article _football_
