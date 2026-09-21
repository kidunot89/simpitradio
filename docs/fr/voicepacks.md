# Packs de voix

L'ingénieur ne sonne comme une personne que s'il dispose d'enregistrements d'une
personne. Un pack de voix, c'est exactement cela : un dossier de fichiers WAV, un
dossier par phrase, que l'ingénieur joue au lieu de parler via la voix Windows.
Plusieurs prises d'une même phrase peuvent se trouver dans son dossier, et
l'ingénieur en choisit une au hasard, de sorte qu'un même appel répété deux fois
dans un relais ne sonne pas comme une machine qui se répète.

Tout ce qu'il dit qui n'est pas dans le pack reste prononcé par la voix Windows :
votre nom, un temps au tour, un pilote dont il n'a jamais entendu parler. Un
pack n'a pas besoin d'être complet pour valoir la peine.

## Trois façons d'en obtenir un

**Installer un pack publié.** *Réglages → Voix* liste les packs publiés au
téléchargement et en installe un à la demande, en vérifiant sa somme de contrôle
avant de décompresser quoi que ce soit. C'est la voie pour une langue autre que
la vôtre.

**L'enregistrer vous-même**, dans la fenêtre. C'est la voie sans plafond et celle
autour de laquelle l'application est construite : *Réglages → Voix → Créer un
modèle de voix*.

**Générer une base avec Piper**, hors ligne, puis réenregistrer les parties qui
comptent pour vous. À utiliser si vous voulez tout de suite quelque chose de
correct et d'agréable, ou si vous préférez ne pas lire 171 phrases avant de
rouler.

Ce n'est pas exclusif. Un pack Piper est un pack ordinaire : n'importe quelle
phrase peut y être remplacée plus tard par votre propre prise.

### Pourquoi pas le clonage de voix

Cela a été essayé en premier puis abandonné, et la raison mérite d'être connue
avant d'aller la chercher.

Une voix clonée a été générée pour ce projet à partir de près de trois minutes
d'audio de référence propre. Repassée dans le modèle vocal de
l'application, chaque prise de « five » revenait en « bye », « four » en « boy »
et « zero » en « yo ».

L'inventaire en est la cause. **141 de ses 171 phrases font un ou deux mots**, et
le texte court est exactement là où un modèle de clonage est le plus mauvais :
XTTS génère de façon autorégressive et décide lui-même quand s'arrêter, et avec
une phrase de deux mots, presque rien ne contraint cette décision. Piper est un
modèle de type VITS, une seule passe des phonèmes à la forme d'onde, sans boucle
d'échantillonnage qui puisse s'égarer. Il ne peut pas dire un autre mot, ce qui
sur cet inventaire compte plus que le timbre.

Crew Chief résout le même problème de la même manière : ses packs sont
*enregistrés*, et ses 11 176 noms de pilotes et 1 052 clips de nombres ont été lus
par une personne.

## Enregistrer le vôtre

*Réglages → Voix → Créer un modèle de voix* ouvre un enregistreur : une phrase à
lire, un décompte, une prise, et la lecture pour la vérifier.

C'est moins de travail qu'il n'y paraît. L'inventaire entier représente
**environ quarante minutes à trois prises par phrase**, et il reprend là où vous
en étiez, donc cela peut se faire en plusieurs séances. Un pack couvrant la
moitié des phrases fonctionne dès l'instant où vous l'enregistrez.

Quelques points décident si le résultat est utilisable :

- **Sur le côté de la bouche**, à deux doigts de distance, plutôt que devant
  elle. Un micro casque directement dans le flux d'air sature à chaque *p* et
  *b*, et la saturation ne se rattrape pas après coup.
- **Une pièce silencieuse.** Un ventilateur ou un PC sous le bureau finit dans
  chaque clip, et chaque clip vous est rejoué en pleine course dans un casque.
- **Une distance constante.** Ne vous penchez pas entre les prises. Des clips
  enregistrés à quatre distances différentes sonnent comme quatre personnes
  différentes.
- **Coupez l'amplification du micro de Windows.** C'est un compresseur, et il
  remonte le bruit de la pièce entre les mots.

Lisez-les comme un ingénieur les dit à la radio : neutre, sans hâte, un peu
blasé. L'ingénieur ne joue pas un rôle.

## Générer une base avec Piper

Piper tourne hors ligne, depuis les scripts d'empaquetage et non dans
l'application. Les chemins ci-dessous sont relatifs à `apps/client` dans une
copie de travail depuis les sources :

```
pip install -r packaging/requirements-voices.txt
python -m piper.download_voices --download-dir models/piper en_GB-alan-medium
python packaging/make_piper_pack.py --name Piper
```

Pour construire avec un modèle particulier :

```
python packaging/make_piper_pack.py --name Piper --model models/piper/en_GB-alan-medium.onnx
```

**Hors ligne, et pas dans l'application, volontairement.** Piper est assez rapide
sur un processeur pour donner envie de l'appeler au moment de parler. Cela
mettrait un modèle de 63 Mo et un runtime ONNX dans un build dont les quatre
dernières versions cassées étaient toutes des dépendances natives non collectées.
Un pack est un dossier de WAV ; le générer ici ne coûte rien à l'application et ne
peut pas casser un build.

Ce n'est pas *votre* voix, et rien ne prétend le contraire. C'est une base
correcte et agréable, par-dessus laquelle toute phrase peut être réenregistrée
dans la fenêtre.

**Le japonais demande un paquet de plus, et échoue de façon déroutante sans
lui.** Le modèle japonais réclame `pyopenjtalk` à Piper pour convertir le texte
en phonèmes, et sans lui, chaque phrase ne produit aucun audio. Ce qui remonte
est `wave.Error: # channels not specified`, qui est le fichier de sortie vide et
non la vraie cause. Le `pyopenjtalk` d'origine ne publie que des sources et
réclame CMake et un compilateur C++ ; `pyopenjtalk-plus` est un fork qui publie
des wheels sous le même nom d'import, et il figure dans le fichier de
dépendances ci-dessus.

## À quoi ressemble un pack

Un pack est un dossier contenant un sous-dossier `voice`, et à l'intérieur de
celui-ci, un dossier par phrase contenant ses prises. C'est la disposition
qu'écrit `crew-chief-autovoicepack`, donc **un pack Crew Chief s'insère
directement**. Le dossier extérieur est distinct pour qu'un pack puisse porter
une licence et ses enregistrements sources sans que ceux-ci soient pris pour des
phrases.

```
voices/
  Norman/
    voice/
      pitradio/
        go_ahead/
          1.wav
          2.wav
        box_this_lap/
          1.wav
        ...
```

Le dossier dans lequel se trouve un WAV, c'est la phrase : la profondeur entre
`voice` et ce dossier est libre. L'enregistreur écrit `pitradio/` ; Crew Chief
écrit un dossier par catégorie. Les deux se lisent de la même façon.

WAV uniquement. C'est ce que tout générateur produit, ce que lit la bibliothèque
standard, et cela ne demande aucun décodeur dans un build qui se bat déjà avec
des dépendances natives.

Les noms de dossiers viennent de la phrase, en minuscules, la ponctuation étant
**supprimée** plutôt que remplacée, si bien que « that's enough » et « thats
enough » sont le même clip. Transformer une apostrophe en séparateur donnerait
`that_s_enough`, et un pack enregistré selon l'une des deux graphies manquerait
l'autre en silence.

## Où vivent les packs

**Réglages → Voix** est l'endroit où ils sont tous listés : ce qui est installé,
ce qui est fourni, et ce qui peut être téléchargé. Les packs vivent à côté de
votre configuration, dans `voices/`, plutôt que sous le dossier d'installation.
Une mise à jour remplace ce dossier en entier, et un pack représente beaucoup
d'audio que vous avez choisi d'y mettre. **Réglages → Voix → Ouvrir le dossier
des packs de voix** l'ouvre.

Déposez-y un dossier, rouvrez l'onglet, et il apparaît dans le sélecteur.

## La liste des phrases

**Réglages → Voix → Écrire la liste des phrases** exporte toutes les phrases que
l'ingénieur peut dire, en CSV, dans la langue de l'ingénieur. Un pack
s'enregistre dans la langue où il sera parlé.

Elle est générée depuis l'application plutôt que tenue à la main, elle ne peut
donc pas s'écarter de ce que l'ingénieur dit réellement. Utilisez-la si vous
enregistrez hors de l'application, ou si vous écrivez votre propre générateur.

## Rien ne sort

**Vérifiez qu'un pack est sélectionné.** *Ingénieur → Voix → Voix* doit pointer
vers le pack et non vers *(aucun pack)*.

**Vérifiez le périphérique de sortie.** *Audio → Sortie* devrait être votre
casque, le même que pour le chat vocal, plutôt que la sortie du simulateur.

**Une phrase manquante n'est pas une panne.** Tout ce qui n'est pas dans le pack
retombe sur la voix Windows, si bien qu'un pack à moitié enregistré sonne comme
deux personnes au lieu d'échouer. C'est voulu : c'est ce qui rend un pack
utilisable avant d'être terminé.
