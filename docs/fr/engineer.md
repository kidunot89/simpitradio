# L'ingénieur

Une voix nommée qui surveille le simulateur et vous parle : vos temps au tour, les
voitures à côté, et des réponses quand vous demandez quelque chose.

Elle partage la touche de push-to-talk avec tout ce que fait SimPitRadio. Maintenez
le déclencheur, dites « Chief, target P3 », relâchez — et au lieu d'aller dans la
fenêtre de chat, l'ingénieur répond.

**Il est coupé jusqu'à ce que vous l'activiez.** Rien n'est dit tant que vous
n'êtes pas allé dans Réglages → Ingénieur cocher la case.

---

## Démarrage rapide

1. Ouvrez **Réglages → Ingénieur** et cochez **Ingénieur activé**.
2. Choisissez l'un des quatre ingénieurs. Cela fixe son nom, sa voix et combien il
   parle.
3. Appuyez sur **Test**. Vous devriez l'entendre redire son nom.
4. Réglez le **Périphérique de sortie** sur votre casque — le même que pour le
   chat vocal, pas la sortie du simulateur.
5. Roulez. Il lira votre temps au tour à la ligne.
6. Maintenez le déclencheur et dites **« Chief, target P3 »** pour lancer le coach
   de virage face à celui qui est troisième.

Si Test ne dit rien, voir [Rien n'est dit](#rien-nest-dit) en bas.

---

## Lui parler

Il y a deux façons pour qu'une phrase devienne une commande, et les deux sont
volontairement étroites. La même touche envoie des messages à tout le monde dans
votre session, donc une commande que l'ingénieur *invente* est un message qui
n'arrive jamais, en silence.

**Dites son nom d'abord.** « Chief, target P3. » Le nom d'abord, la formule juste
après. `hey`, `ok` et `right` sont autorisés devant le nom.

**Ou dites une formule seule** — mais seulement celles qui ne prennent pas de
pilote. « initiate corner coaching » marche sans rien devant. « target Verstappen »
non, parce que « target » pourrait commencer une phrase ordinaire et que son
argument n'a pas de fin : *« target time is a twenty three »* serait sinon avalé
en entier et n'atteindrait jamais la fenêtre de chat.

Dire juste le nom donne « go ahead », comme le ferait une vraie radio — et garde un
« Chief » égaré hors d'un message envoyé à vingt autres personnes.

**« Stop »** marche toujours, quoi qu'il tourne et quoi que l'ait lancé. De même
pour « stand down », « cancel », « that's enough » et « forget it ».

Tout ce que l'ingénieur ne reconnaît pas est un message, et part dans la fenêtre de
chat exactement comme avant.

---

## Choisir un ingénieur

Quatre sont fournis avec l'application :

| | Voix | Style |
| --- | --- | --- |
| **Chief** | masculine | Posé et complet. « Virage quatre, Tandy était plus rapide en sortie, deux dixièmes. » |
| **Ada** | féminine | Sec. Laisse tomber le numéro de virage : « Tandy, meilleure sortie, deux dixièmes. » |
| **Marshall** | masculine | Plus lent et plus fourni, si les autres semblent pressés. |
| **Vic** | féminine | Rapide et court. Celle qui parle le moins des quatre. |

Ce sont des **préréglages, pas des enregistrements** — un nom, une voix Windows
préférée, un rythme, et la quantité de paroles. Cela vaut la peine d'être dit
franchement, parce que « quatre voix » signifie d'habitude quatre jeux d'audio : un
pack de voix généré fait un à deux gigaoctets, et en livrer quatre serait un
téléchargement de huit gigaoctets pour remplacer quelque chose déjà présent
gratuitement sur toute machine Windows.

Chacun choisit la meilleure voix Windows installée correspondant à sa préférence et
à votre langue. Sur une installation standard de Windows 11 il y en a
habituellement deux ou trois, donc deux ingénieurs peuvent partager une voix et se
distinguer par le rythme et la formulation. Si vous en voulez une précise, réglez
**Voix Windows** et cela l'emporte sur le préréglage.

**Appelé** est ce à quoi il répond. Mettez-y ce que vous voulez — le nom ne sert
qu'à s'adresser à lui, et « Bob, target P3 » marche tout aussi bien.

---

## Ce qu'il vous dit

### Temps au tour

Lit votre tour au passage de la ligne, et dit quand c'était votre meilleur. Activé
par défaut.

### Spotter

Annonce les voitures à côté : « car left », « car right », « cars both sides »,
puis « clear » une fois qu'elles sont parties. Désactivé par défaut, et il y a une
chose à savoir.

**Quel côté est lequel n'a pas pu être vérifié sans une voiture sur une piste.**
Les positions viennent des coordonnées du monde du simulateur, et que le calcul
donne gauche ou droite dépend d'une convention de main que ce projet n'a pas pu
vérifier depuis une machine de développement. Donc s'il annonce « gauche » pour une
voiture à votre droite, activez **Inverser les côtés du spotter** dans Profils →
réglages du plugin du jeu. Une case, une fois.

Tout le reste du spotter est exact : il utilise les positions du jeu, il laisse
tomber la hauteur (pour qu'un pont ou les esses du Mans ne mette personne contre
votre portière) et il n'annonce pas les voitures d'une ligne droite voisine.

### Dégâts

Dit ce qui est cassé et s'il faut rentrer pour ça. Activé par défaut, et il faut un
simulateur qui publie l'état de la voiture — aujourd'hui, c'est Le Mans Ultimate.

> *Vous avez perdu de la carrosserie. Aux stands ce tour-ci.*

**Dit quand cela change, pas tant que cela dure.** Un pilote qui traîne un arrière
gauche cabossé pendant une demi-heure n'a pas besoin qu'on le lui rappelle à chaque
passage, donc il parle au moment où cela empire puis se tait. Chaque partie de la
lecture est surveillée, pas seulement la pire — une deuxième chose qui se détache
d'une voiture déjà cabossée est une nouvelle, même si la gravité n'a pas bougé.

**Ce qu'il dit, c'est où, puis s'il faut.** Vous savez déjà que vous avez tapé
quelque chose ; ce que vous ne voyez pas depuis le baquet, c'est la gravité et s'il
y a le temps de réparer. Il nomme donc l'endroit — le nez, l'arrière, tout le côté
gauche — puis donne l'une de trois réponses :

| | |
| --- | --- |
| **Aux stands ce tour-ci** | la voiture ne peut pas être courue, seulement ramenée : une pièce qui pend, une crevaison, une roue perdue, un nez cassé. Le temps restant n'y change rien — l'alternative est un drapeau noir ou un mur |
| **Aux stands dès que possible** | ça vaut la réparation. Toujours aux essais et en qualification, où un arrêt ne coûte rien et où l'intérêt d'être dehors est d'avoir une voiture qui marche |
| **Restez dehors, on fera avec** | une course dont il reste moins d'un cinquième. À trois tours de la fin, mieux vaut ramener une voiture abîmée au drapeau que rendre une minute |

Les dégâts légers reçoivent la première moitié et aucun conseil. Se voir demander
de peser un arrêt pour un quart arrière éraflé est pire que de ne rien entendre.

Il ne parle jamais par-dessus le coach. Les dégâts sont urgents — on veut savoir
que l'aileron est parti avant le virage suivant et non après — mais une critique
que vous avez demandée ne mérite pas d'être coupée pour une voiture qui sera encore
cassée dans quatre secondes. Le spotter est la seule annonce qui parle par-dessus
quoi que ce soit.

---

## Qui il surveille

L'ingénieur garde un **focus** : un pilote auquel il vous compare. Vous n'avez pas
à le régler. Par défaut c'est **la voiture devant dans votre catégorie**, ou celle
derrière quand vous la menez — parce qu'il n'y a personne devant à chasser, et que
la question devient de savoir si vous les tenez derrière.

Il ne suit un changement qu'une fois la position **tenue huit secondes**. Les
positions bougent sans cesse : mesuré à un vrai départ de course, quinze pilotes
différents ont été la voiture de devant en quatre-vingt-dix secondes, et chaque
bascule jetait les tours accumulés, si bien qu'il n'en avait jamais assez pour dire
quoi que ce soit.

Dites-le si vous voulez quelqu'un d'autre :

- `focus on {pilote}` — ou « keep an eye on », « keep tabs on », « study », « watch »
- `default focus` — retour au choix automatique
- `stop focusing` — coupé, et cela reste coupé jusqu'à ce qu'on le rappelle

Un pilote que vous nommez n'est jamais outrepassé. Repartir deux virages plus tard
vers celui qui est devant serait l'application qui vous contredit.

L'onglet État montre qui est surveillé, et `what are we watching` le demande.

---

## Lui demander des choses

Chaque question a une boîte de formules dans Réglages → Ingénieur, une par ligne,
et ce que vous tapez remplace les valeurs par défaut. Chacune peut être coupée ;
une question coupée n'apporte aucune formule, donc ses mots atteignent la fenêtre
de chat comme les autres au lieu d'être pris et répondus par rien.

- **Votre voiture** — `what's my best lap`, `how are the tyres`, `what's the
  damage`, `how's the fuel`, `how much fuel do I need to finish the race when I
  pit on the next lap`
- **La session** — `who has the fastest lap`, `who's fastest`,
  `who has the fastest sector`, `who's in the lead`, `who's ahead`
- **Où passe le temps** — `where am I slower`, `where am I faster`, l'un ou l'autre
  avec `than {pilote}` à la fin

**Les questions doublent la file.** Une question posée pendant que l'ingénieur était
en pleine annonce attendait derrière ou était purement abandonnée — la file en tient
six et un tour chargé la remplit — donc vous demandiez, l'entendiez parler d'autre
chose, et n'obteniez pas de réponse. Une réponse dégage désormais le trafic
ordinaire, coupe ce qui est en train d'être dit, et ne peut pas être évincée. Elle
cède toujours devant le spotter, parce qu'une voiture à côté, c'est ne pas se
crasher.

**Une question à laquelle il ne peut pas répondre reste hors de la fenêtre de
chat.** « Who's faster ? » n'est pas une formule qu'il connaît, et cela passait
autrefois à travers et partait à la session. Tout ce qui se lit comme une question
— cela finit par un point d'interrogation, ou commence par un interrogatif — reçoit
« say again » à la place. Il y a une case à cocher sur l'onglet Chat texte si vous
préférez l'ancien comportement, et une question que vous avez explicitement coupée
atteint quand même le chat, parce que la couper est votre façon de dire que ces
mots sont à vous.

Vous pouvez mettre le nom de l'ingénieur à l'un ou l'autre bout : « Bono, how are
the tyres » et « how are the tyres, Bono » marchent tous les deux. C'est la virgule
qui le marque comme un nom, donc `focus on Bono` cible toujours un pilote appelé
Bono.

### Où suis-je plus lent

Celle qui vaut d'être connue. Elle vous compare à votre focus **virage par virage,
moyenné sur chaque tour de cette session** plutôt que lu sur un seul — un tour isolé
dit ce qui s'est passé sur ce tour, et la question porte sur ce qui se répète.

> Chief, where am I slower
>
> *Virage trois, vous êtes plus lent à l'entrée, deux dixièmes.*
>
> *Virage sept, il a une meilleure sortie, un dixième.*

Elle dit *comment*, pas seulement où : entrée, sortie, freinage plus tardif, ou plus
lent dans tout le virage. Là où un catalogue de virages existe pour le circuit, elle
utilise le nom — « Eau Rouge » plutôt que « virage trois ».

**Comment elle trouve les virages.** Il n'y a pas de carte de circuit et il n'y en
aura pas — il faudrait un fichier par tracé, cela vieillirait à chaque changement de
configuration, et cela marcherait sur les quatre circuits que quelqu'un aurait eu le
temps de faire. Un virage est un endroit où le tour de référence a ralenti puis
réaccéléré, ce qui est vrai sur tous les circuits de tous les simulateurs. Les
chicanes comptent pour un seul virage.

**Elle décrit, elle n'instruit pas.** « Il a une meilleure sortie » est ce que
l'application sait. Elle ne sait pas si c'était la trajectoire, les pneus ou
l'aspiration, et « freine plus tard » serait une supposition déguisée en coaching.

**S'il manque des tours, elle dit lesquels.** Les vôtres ou les siens — sinon « pas
de tours à comparer » vous laisse deviner.

### Ce qu'elle ne prendra pas comme référence

- Un tour dont une partie est dans la voie des stands. Un tour rapide qui était en
  réalité un raccourci par les stands deviendrait sinon la cible à laquelle tout le
  monde est comparé, et rien n'y paraîtrait anormal.
- Un tour que vous avez rejoint en cours de route.
- Un tour pour lequel le simulateur n'a donné aucun temps — un tour de sortie, ou
  une voiture qui vient d'arriver.
- Tout ce qui vient d'un autre circuit. Changer de tracé efface tout.

Elle se tait aussi pendant que vous êtes spectateur. Commenter un tour que vous
regardez au lieu de conduire n'aurait aucun sens.

---

## Quand votre simulateur ne peut pas répondre

Tous les simulateurs ne publient pas la même chose, et l'ingénieur le dit plutôt que
de deviner. L'Assetto Corsa d'origine, par exemple, publie **votre propre voiture et
rien sur les autres** — ni nom, ni position, ni temps au tour d'un autre pilote —
donc tout ce qui vous compare à la grille n'a de données par aucune voie.

Demandez-y « who's leading » et il répond **« ce jeu ne le dit pas »**. C'est voulu
et ce n'est pas la même chose que « personne à surveiller », qui signifie que la
grille est réellement vide. Dire à un pilote septième que personne n'est devant lui
n'est pas une réponse inutile, c'est une réponse fausse.

Les comportements qui ont besoin de données que votre simulateur ne fournit pas sont
sautés avec une ligne dans le journal plutôt que laissés activés et muets :

```
Spotter is on but this sim does not publish positions or spotter; it will stay quiet
```

`--telemetry` affiche ce que votre simulateur envoie réellement — voir la dernière
section.

---

## Autres langues

L'ingénieur parle la langue que vous avez réglée pour la **transcription**, sauf si
vous la fixez sur l'onglet Ingénieur. C'est la bonne valeur par défaut et pas une
valeur arbitraire : vos commandes arrivent par Whisper, donc si Whisper produit de
l'espagnol, un ingénieur à l'écoute de formules anglaises n'en entendra jamais une
seule.

Tout ce qu'il dit — y compris les formules de déclenchement — passe par les mêmes
catalogues de traduction que la fenêtre. Ajouter une langue est un fichier JSON dans
`src/pitradio/locale/` ; voir le README principal.

**Les nombres sont écrits en toutes lettres en anglais et lus en chiffres partout
ailleurs.** Pas par paresse : la grammaire des nombres est réellement propre à
chaque langue — l'allemand inverse dizaines et unités, l'espagnol fusionne les
vingtaines — et une implémentation à moitié faite produirait des absurdités
assénées avec assurance dans la langue de quelqu'un. Les chiffres confient le
problème à la voix de synthèse de cette langue, qui le résout déjà correctement. Le
corollaire est qu'un pack de voix non anglais ne peut pas couvrir les nombres, et
qu'ils sortent synthétisés.

---

## Packs de voix

**Le pack dont parle cet ingénieur se règle ici, sur l'onglet Ingénieur**, et le
coach choisit le sien sur l'onglet Coaching — ce sont deux métiers distincts et un
pilote peut raisonnablement vouloir entendre lequel des deux parle.

**Installer, enregistrer et supprimer des packs, c'est Réglages → Voix.** Un pack
est quelque chose que l'application détient ; celui dont une persona parle est un
réglage de cette persona.

Deux packs sont fournis : **Norman** et **Claudia**. Les deux ont été générés avec
Piper — voir [voicepacks.md](voicepacks.md) — et l'un comme l'autre peut être
remplacé par un pack à vous.

Un pack de voix remplace le synthétiseur par de l'audio enregistré : un dossier de
fichiers WAV, un dossier par phrase, plusieurs prises chacune. L'ingénieur choisit
une prise au hasard, et c'est l'essentiel de ce qui fait qu'un pack sonne comme une
personne et pas la synthèse vocale.

**La disposition est celle de Crew Chief**, volontairement :

```
%APPDATA%\pitradio\voices\
  Ada\
    voice\
      corners\
        two_tenths\
          a.wav
          b.wav
```

Un `<pack>/<phrase>/*.wav` à plat fonctionne aussi, et c'est ce que donne un
enregistrement fait par vous.

Cette disposition fait qu'un pack généré par
[crew-chief-autovoicepack](https://github.com/cktlco/crew-chief-autovoicepack) peut
être déposé tel quel. Pour en générer un pour les phrases de SimPitRadio plutôt que
celles de Crew Chief :

1. Réglages → **Voix** → **Écrire la liste des phrases**. Cela écrit
   `phrase_inventory.csv` dans le dossier des voix, dans la langue de l'ingénieur.
2. Donnez cet inventaire au générateur à la place du sien.
3. Mettez le dossier de sortie sous `voices\` et choisissez-le sur l'onglet
   Ingénieur (ou utilisez **Réglages → Voix → Ouvrir le dossier des packs de voix**
   pour y arriver).

**Les noms et les nombres ne sont jamais dans un pack** et sont toujours dits par
la voix Windows. Il n'y a pas moyen d'y couper — aucun pack ne peut contenir tous
les noms de pilotes ni tous les temps au tour — donc une annonce comme « virage
quatre, Tandy était plus rapide en sortie » est en partie enregistrée et en partie
synthétisée. Cette couture s'entend. C'est quand même le bon compromis :
l'alternative est un pack qui ne sert plus dès qu'un pilote est nommé, c'est-à-dire
la plupart des annonces.

Les packs sont rangés à côté de votre configuration, pas dans le dossier
d'installation, pour qu'une mise à jour n'efface pas un gigaoctet d'audio que vous
avez choisi d'installer.

---

## Comment tout s'articule

L'ingénieur tourne sur **son propre thread**, distinct des quatre que SimPitRadio a
déjà, et la parole obtient un thread en dessous. Ni l'un ni l'autre ne peut retarder
le hook clavier, le worker ou la fenêtre.

Tout ce qu'il fait a le droit d'échouer. Que l'ingénieur devienne muet ne doit jamais
vous coûter un déclenchement, une transcription ou un message dans le chat — donc si
quelque chose casse ici, les mots partent au chat comme toujours et le problème est
une ligne dans le journal.

Il lit le simulateur dix fois par seconde via le même plugin qui fournit les noms de
pilotes pour les mentions. Il n'y a pas de second chemin de données ni de connexion
supplémentaire au jeu.

---

## Rien n'est dit

**Test ne fait rien.** Le synthétiseur tourne dans un hôte PowerShell via
`System.Speech`, qui fait partie du .NET Framework sur toute machine Windows 10 et
11. Cherchez `no speech host` dans le journal — une machine verrouillée avec
PowerShell bloqué est la cause habituelle.

**Vous l'entendez, mais pas dans votre casque.** Réglez le périphérique de sortie
sur l'onglet Audio. Il vaut par défaut le périphérique système, qui pendant une
course est souvent le haut-parleur du volant.

**Il lit les temps au tour mais ne coache jamais.** Le coach de virage a besoin d'un
tour de référence. Tant que le pilote ciblé n'en a pas bouclé un — proprement, pas
par les stands — il n'y a rien à comparer. La ligne d'état de l'onglet Ingénieur dit
combien de virages il a cartographiés.

**Il coache mais ne dit rien à certains virages.** C'est le principe : ces virages
étaient dans le seuil. Baissez **Seuil de virage** si vous en voulez plus.

**Il ne répond à rien de ce que vous dites.** Vérifiez le nom sur l'onglet
Ingénieur, et souvenez-vous que toute formule prenant un pilote a besoin du nom
devant. Dites « Chief » tout seul — si vous obtenez « go ahead », il écoute et c'est
la formule qui pose problème.

**Il a mangé un message.** Il ne devrait pas. Si l'ingénieur a pris quelque chose que
vous vouliez envoyer, la ligne du journal dit `that was for the engineer` avec ce
qu'il a reconnu — merci d'ouvrir un ticket avec cette ligne, parce qu'un matcher trop
zélé est le seul bug de cette fonction qui coûte quelque chose de réel.

---

## Vérifier ce que votre simulateur envoie vraiment

La plupart des problèmes « l'ingénieur ne dit rien » ne viennent pas de l'ingénieur.
Lancez le jeu, mettez-vous **en piste et en mouvement**, puis :

```bash
python -m pitradio --telemetry
```

Cela affiche chaque voiture telle que l'ingénieur la voit — distance au tour,
vitesse, nombre de tours, secteur, temps, drapeau stands, position dans le monde —
et, plus utile encore, cela compare des lectures consécutives et vous dit si quelque
chose change.

Cette dernière partie compte plus qu'il n'y paraît. Un simulateur en pause ou posé
dans un menu continue de publier un bloc qui a l'air parfaitement sain : voitures,
positions, vitesses, tout est plausible. Rien ne bouge, donc l'ingénieur n'a rien à
dire, et aucun instantané ne le montre. S'il signale

> Nothing changed across 4 reads, including the sim's own clock.

alors le jeu est en pause, dans un menu, ou la session est terminée — pas cassé.

Ce qu'il faut regarder quand c'est *vivant* :

| Colonne | Alimente |
| --- | --- |
| `lapdist`, `speed` | la détection des virages, et où passe le temps |
| `lap`, `last lap`, `best lap` | les annonces de temps au tour et de meilleur tour |
| `sec` — change trois fois par tour | toutes les annonces de secteur |
| `world x/y/z` — différent par voiture | le spotter |

La ligne `provides:` en haut dit lesquelles de ces choses le plugin prétend fournir.
Un comportement qui a besoin de quelque chose d'absent est sauté plutôt que laissé
activé et muet, et le journal dit quelle capacité manque.

## Ce que chaque simulateur sait faire

Les simulateurs publient des choses très différentes, et un comportement dont les
données manquent est **sauté avec une ligne dans le journal** plutôt que laissé
activé et muet.

| | Le Mans Ultimate | iRacing | Assetto Corsa / Competizione / Evo | Automobilista 2, Project CARS 2 / 3 |
| --- | --- | --- | --- | --- |
| Temps au tour | oui | oui | oui | dérivés |
| Nouveau meilleur tour | oui | oui | — | oui |
| Annonces de secteur | oui | — | oui | — |
| Où suis-je plus lent | tout pilote | tout pilote | votre propre meilleur | tout pilote |
| Qui est devant / en tête | oui | oui | — | oui |
| Spotter | géométrie | l'annonce du simulateur lui-même | Competizione seulement | géométrie |
| Mentions de pilotes, « P3 » | oui | oui | — | oui |
| Dégâts | oui | — | — | — |
| Coaching et diagramme de segment | oui | — | — | — |

Les trous sont les jeux, pas l'application :

- **iRacing** ne publie pas de temps par secteur et par voiture, donc les annonces
  de secteur n'ont rien pour travailler. Son spotter est le meilleur de tous —
  `CarLeftRight` vient des vraies carrosseries, il n'a donc besoin ni de réglage
  d'inversion ni d'estimation de largeur.
- **Assetto Corsa** ne publie les temps que pour votre voiture et aucun nom de
  pilote. C'est pourquoi il n'y a ni classement ni mentions, et pourquoi « où
  suis-je plus lent » poursuit votre propre meilleur tour — ce à quoi sert une
  séance d'essais de toute façon.

  Le jeu d'origine va plus loin : il ne publie **aucune autre voiture**, pas même une
  position. Vérifié contre une vraie course à huit voitures, le tableau de
  coordonnées contenait le joueur en case zéro et de la mémoire intacte partout
  ailleurs — des zéros, un NaN, un dénormal. Le spotter n'a donc rien non plus
  là-bas, et le plugin le dit par session et non par jeu : **Competizione publie**
  bien ce tableau, et le même plugin y rapporte des positions.
- **Automobilista 2 et Project CARS** portent des *comptes* de tours plutôt que des
  temps dans la partie de leur bloc digne de confiance, donc les temps sont mesurés
  ici au chronomètre. Un tour qui enjambe une pause ressort plus long qu'il ne l'a
  été ; cela échoue du bon côté, puisqu'un tour gonflé ne devient jamais la
  référence qu'une comparaison poursuit. Leur champ de secteur est un enum qui n'a
  pas pu être déterminé depuis l'extérieur des jeux, donc les annonces de secteur ne
  sont pas proposées.

Automobilista 2 a sa propre entrée plutôt que de partager celle de Project CARS,
pour que vous puissiez choisir le jeu que vous faites tourner et pour que les deux
gardent des réglages de spotter et de proximité distincts.

**Le Mans Ultimate est le seul vérifié contre le jeu en fonctionnement.** Tous les
autres lecteurs sont testés contre de la mémoire partagée construite à la main, ce
qui attrape une largeur de champ fausse, un nom mal décodé ou une erreur de
remplissage — et ne peut pas attraper une supposition fausse sur ce que le
simulateur met où. Lancez `--telemetry` avec le jeu en piste avant de faire
confiance à l'un d'eux, et surtout à Assetto Corsa Evo, encore en accès anticipé et
susceptible de déplacer sa disposition.

**iRacing est marqué expérimental**, et apparaît comme tel dans le sélecteur de
profils. Non parce que ce serait du moins bon code que les autres, mais parce que
personne travaillant sur SimPitRadio n'en possède un exemplaire — donc, contrairement
au reste, il ne sera pas vérifié contre la réalité à moins que quelqu'un qui l'a
lance `--telemetry` et dise ce qui est revenu. Si c'est vous, faites-le ; la note
dans la liste des plugins demande exactement cela.

## Réglages par simulateur

Trois des nombres de l'ingénieur vivent sur le **profil**, sous les réglages du
plugin du jeu, et non sur l'onglet Ingénieur — parce qu'ils décrivent le jeu plutôt
que votre goût :

- **Inverser les côtés du spotter** — si « gauche » désigne une voiture à votre
  droite
- **Chevauchement du spotter (mètres)** — quel écart le long de la piste compte
  encore comme côte à côte. Une Hypercar fait environ 5 m
- **Largeur du spotter (mètres)** — jusqu'où sur le côté cela compte, avant qu'elles
  soient simplement sur une autre partie du circuit

Les longueurs de voiture et les conventions d'axes diffèrent d'un simulateur à
l'autre, donc un nombre qui convient à un jeu est faux dans le suivant.

## Drapeaux et incidents

Un comportement à part entière, et séparé du spotter délibérément. Les dossiers de
sons de Crew Chief tracent la ligne et c'est la bonne : `car_left`, `still_there` et
`clear_all_round` sont dans `spotter/`, tandis que `stopped_car_in_turn_3`,
`slow_car_ahead` et `local_yellow_ahead` sont dans `flags/`. Le spotter répond « qui
est à côté de moi », qui est de la géométrie. Les drapeaux répondent « qu'est-il
arrivé à la piste », qui ne l'est pas.

Déduire le second du premier est ce qui produisait un avertissement dans chaque zone
de freinage : SimPitRadio avait une règle disant qu'une voiture beaucoup plus lente
que vous était un danger, et une zone de freinage est précisément l'endroit où la
voiture de devant est beaucoup plus lente que vous. Cette règle a disparu.

**Trois sources, pas également dignes de confiance.**

Le *drapeau jaune sur tout le circuit* et le *bleu* viennent du simulateur et sont
fiables — `mGamePhase`, `mYellowFlagState` et le `mFlag` par voiture de LMU se
lisent tous sensément contre une session en direct.

Les *jaunes locaux sont déduits*, parce que le `mSectorFlag` de LMU est
inutilisable. Il est documenté comme « s'il y a des jaunes locaux en ce moment dans
chaque secteur » et lit `[11, 11, 1]` sous drapeau vert, avec les champs de part et
d'autre corrects — ce n'est donc pas un décalage qui a glissé, LMU publie simplement
autre chose là. Lu comme des booléens, cela mettrait un jaune permanent sur tout le
circuit. Un incident signifie donc ici ce qu'un commissaire entend par là : une
voiture s'est arrêtée sur la route et y est depuis deux secondes. C'est une
déduction à partir de données que le simulateur publie honnêtement, dans le même
esprit que trouver les virages dans la trace de vitesse plutôt que livrer une carte
de circuit.

Le coût est que l'annonce ne peut pas précéder l'incident — un vrai jaune est sorti
dès que les commissaires le voient, et celui-ci attend d'être sûr. Le bénéfice est
qu'il ne se trompe jamais sur une piste verte, ce qui est la panne qui pousse les
gens à couper une fonction.

**Les incidents sont nommés par virage, pas par pilote.** À la vitesse où cela
compte, « virage six » est quelque chose sur quoi un pilote peut agir et un nom est
un compte de syllabes sur lequel il ne peut pas. La numérotation est celle du carnet
de tours, pour qu'un pilote entende un seul jeu de numéros de virage plutôt qu'une
fonction utilisant l'un et les drapeaux l'autre ; les virages sont trouvés une fois
par tour de référence et mis en cache, parce que `find_corners` rééchantillonne un
tour entier et que ceci tourne plusieurs fois par seconde. Sans tour de référence,
c'est le secteur qui est nommé.

**Quand l'incident, c'est vous, les annonces de côté s'arrêtent.** Décrire au pilote
d'une voiture en travers les voitures qui passent est du bruit ; la seule question
utile est de savoir s'il y a la place de repartir, et
[rejoin.py](../src/pitradio/engineer/rejoin.py) y répond — en comparant *le temps
pour être en sécurité* au *temps avant l'arrivée de la voiture suivante*, pas une
distance à une distance. Une voiture arrêtée doit récupérer toute son accélération
avant la première arrivée. C'est pourquoi la réponse naïve « trois secondes de piste
libre » fait ramasser les gens.

Deux garde-fous, tous deux appris et non supposés : rien n'est dit dans la voie des
stands, où être immobile est le but, et rien avant que la voiture ait jamais bougé —
être sur la grille avant les feux, c'est être immobile, sur la trajectoire, avec tout
le plateau derrière, ce qui est exactement ce que regarde le conseil de
réinsertion.

Voir [voicepacks.md](voicepacks.md) pour générer une voix.

## Questions

Distinctes des comportements, et la distinction n'est pas de la comptabilité. Un
comportement est quelque chose que l'ingénieur *continue de faire* — voir [Ce qu'il
vous dit](#ce-quil-vous-dit) — et il porte un intervalle de répétition, parce
qu'une voiture à côté cesse d'y être sans que rien ne se passe. Une question a une
réponse, et quand la réponse a été donnée, rien ne tourne. Modéliser l'une comme
l'autre mettrait « who has the fastest lap » dans la liste des Comportements, où
chaque entrée a un intervalle de répétition, et il n'existe pas de fait de répondre à
une question à nouveau toutes les 1,2 seconde.

Trois d'entre elles : le meilleur tour, le meilleur secteur, et votre propre
meilleur.

**Le paramètre suit le mot-clé et ne fait jamais partie de la formule.** Ce qu'un
pilote peut demander dépend du simulateur dans lequel il est — les catégories de
cette grille, les secteurs de ce circuit — et rien de tout cela n'a sa place dans une
formule que quelqu'un a tapée dans une boîte de réglages. « Who has the fastest
sector » est la formule ; « three in GT3 » est ce qui est venu après, analysé contre
la session. Une catégorie est reconnue via `mentions.class_aliases`, donc le
« LMGT3 » de LMU répond à « GT3 » exactement comme ailleurs, et « LMP2 » refuse
toujours de répondre à « P2 » parce que c'est une position.

**Un espace d'arguments fermé est la défense contre les faux positifs**, et une
meilleure que de compter les mots. `phrases.MIN_BARE_WORDS` protège les commandes
parlées en exigeant deux mots devant un paramètre ouvert ; ce n'est pas assez ici,
parce que « who has the fastest lap of my life that one » passe sans peine et serait
pris pour une question sur une catégorie appelée « of my life that one » — avalant le
message. Mais l'argument d'une question ne peut être qu'une catégorie de cette
grille, un secteur entre un et trois, ou rien. Tout le reste n'était pas une
question, quoi que cela ait commencé par être. Adressée par le nom, c'en est une quoi
qu'il arrive : quelqu'un qui a dit le nom de l'ingénieur lui parlait.

**Aucune catégorie nommée signifie votre propre catégorie**, parce que c'est ce que
veut dire quelqu'un dans une GT3 qui demande « who has the fastest lap ». Une
catégorie nommée où personne ne roule reçoit cette réponse plutôt que d'être
silencieusement servie avec le chiffre général — une réponse fausse assénée avec
assurance est la panne sans symptôme.

Chacune a une case à cocher sur l'onglet Ingénieur et rien d'autre. Ce sur quoi une
question peut porter est fixé par ce que publie le simulateur, donc une boîte de
formules éditable là-bas laisserait entendre que vous pouvez en inventer une.

L'interrupteur gagne sa place pour une autre raison : **chaque formule que
l'ingénieur écoute est une formule qui peut être extraite d'un message destiné à
toute la session**, et quelqu'un qui ne pose jamais ces questions n'a aucune raison
de porter ce risque. En couper une retire ses formules du matcher entièrement plutôt
que de la faire taire en aval — sinon « who has the fastest lap » serait toujours
extrait du message puis répondu par rien, ce qui est le pire des deux. Absent de la
configuration signifie activé, donc ajouter une question ne demande jamais de
migration.

## Le spotter, et d'où viennent ses nombres

Chaque seuil de `spotter.py` est celui de Crew Chief, lu dans une installation locale
plutôt que deviné — son `ui_text/en.txt` nomme chaque réglage et
`CrewChiefV4.exe.config` livre les valeurs par défaut :

| Le nôtre | Celui de Crew Chief | Défaut |
| --- | --- | --- |
| `DEFAULT_CAR_LENGTH` | `lmu_spotter_car_length` | 4,5 (5 pour pcars2/ACC, 4,4 pour AMS2) |
| `GAP_FOR_CLEAR` | `spotter_gap_for_clear` | 0,5 m |
| `OVERLAP_DELAY` | `spotter_overlap_delay` | 50 ms |
| `CLEAR_DELAY` | `spotter_clear_delay` | 150 ms |
| `MIN_SPEED` | `min_speed_for_spotter` | 10 m/s |
| `MAX_CLOSING_SPEED` | `max_closing_speed_for_spotter` | 12 m/s |
| l'intervalle de répétition | `spotter_hold_repeat_frequency` | 3 s |

Trois d'entre eux manquaient totalement ici et chacun causait un défaut que le pilote
pouvait ressentir :

**La limite de vitesse d'approche est ce qui attrape la voiture qui double.** Quelque
chose qui arrive 12 m/s plus vite traverse toute la fenêtre de chevauchement en bien
moins d'une seconde, si bien qu'au moment où l'annonce est dite elle est passée — et
le pilote tient une trajectoire pour une voiture qui n'est plus là.

**La vitesse minimale est ce qui arrête la voie des stands et la grille.** Sous
10 m/s les voitures autour de vous sont à l'arrêt ou passent au pas, et les annoncer
est la manière dont un spotter finit désactivé.

**Les deux délais de stabilisation sont ce qui arrête le bavardage.** Deux voitures
dans le même virage entrent et sortent du chevauchement au rythme de leur
respiration. Ils sont volontairement de longueurs différentes : le délai de
chevauchement est court parce qu'un avertissement en retard ne vaut rien, et le délai
de dégagement est plus long parce qu'il peut se permettre d'être sûr — un pilote qui
tient sa ligne un dixième de plus que nécessaire n'a rien perdu.

La portée de dégagement est `longueur de voiture + écart`, pas un second multiple de
la longueur. La distinction compte aux extrêmes : pour un kart, « une longueur de
voiture de plus » fait deux mètres d'hystérésis et l'annonce s'accroche bien trop
longtemps, alors qu'un demi-mètre de jour est un demi-mètre quoi que vous conduisiez.

**Le spotter est muet sous drapeau jaune sur tout le circuit** — le
`fcy_stop_spotter_immediately` de Crew Chief, activé par défaut. Le plateau est
groupé au pas et se chevauche en permanence, donc chaque annonce serait vraie et
inutile.

### Ce qu'il dit

Le vocabulaire est le dossier `Sounds/voice/spotter/` de Crew Chief, donc un pack de
voix construit pour Crew Chief le dit entièrement sans correspondance : `car_left`,
`car_right`, `still_there`, `hold_your_line`, `in_the_middle`, `clear_left`,
`clear_right`, `clear_all_round`, `three_wide_on_left`, `three_wide_on_right`.

Deux d'entre eux ont remplacé des annonces qui énonçaient le même fait par le chemin
le plus dur :

* **« Three wide, you're on the right »** était « two cars left ». Un pilote qui
  entend l'ancienne doit calculer où cela le laisse, pendant qu'il est occupé ; la
  nouvelle dit directement de quel côté il n'y a pas de place.
* **« In the middle »** était « three wide », pour une voiture de chaque côté.

Une répétition dit `still there` d'un côté et `hold your line` des deux, parce que ce
sont des instructions différentes — l'une veut dire ne va pas par là, l'autre veut
dire ne bouge pas. L'arrivée et ses répétitions partagent une clé dérivée des
*comptes*, pour que l'intervalle de répétition les gouverne ; une clé qui changerait
avec la formulation ferait de la relance une nouvelle annonce, due dès le tic
suivant.

**Le jeu ovale est délibérément absent** — `car_inside`, `clear_outside`,
`three_wide_on_inside`. Quel côté est l'intérieur est un fait sur le dévers, qu'aucun
des simulateurs ici ne publie et que Crew Chief tient par circuit. Le deviner, c'est
une annonce qui est fièrement à l'envers.

### Carburant

« How much fuel do I need to finish the race when I pit on the next lap », ou
« ...when I pit in five laps ». **La réponse est un pourcentage**, parce que c'est le
nombre qui figure sur l'écran de carburant du simulateur et que le pilote a environ
quatre secondes en allant vers l'entrée des stands pour le régler. Les litres sont le
calcul.

**La consommation est mesurée, jamais supposée.** Ce qu'une voiture consomme dépend du
circuit, de la cartographie moteur, du trafic et de la façon dont la personne la
conduit, donc les litres par tour ici sont ce que *cette* voiture a consommé sur *ces*
tours — une courte moyenne glissante, pour qu'elle suive un changement de cartographie
au lieu d'être tirée en arrière par tout un relais. Tant qu'un tour n'a pas été
bouclé, il n'y a pas de réponse et il le dit. Un chiffre de carburant inventé de rien
est la seule mauvaise réponse ici qui termine la course de quelqu'un.

Trois détails qui seraient sinon redécouverts :

* **Les tours avant l'arrêt ne sont pas ravitaillés.** Ce qui est dans le réservoir
  maintenant les couvre. Seuls ceux d'après sont la question, et c'est pourquoi ceci
  ne lit jamais le niveau actuel.
* **`mMaxLaps` vaut `INT_MAX` dans une session au temps.** Pris au pied de la lettre,
  il demande de quoi faire deux milliards de tours. `SessionInfo` porte `max_laps`
  *ou* `ends_at`, jamais les deux, et le plugin décide lequel — l'ingénieur ne devine
  jamais celui qui manque. Une course au temps divise l'horloge restante par le
  meilleur tour du pilote lui-même et arrondit **au-dessus**, parce que le drapeau
  tombe à la fin du tour où vous êtes quand le temps est écoulé.
* **Un plein au-dessus de la capacité du réservoir est signalé, pas rogné.** Cela veut
  dire que l'arrêt ne peut pas être le dernier, et un pilote à qui l'on dit « cent
  pour cent » sans le lui dire planifie une course qui ne marche pas.

Tout le reste arrondit vers plus de carburant : tomber en panne est un abandon, et
porter un litre de trop est un dixième au tour.

Le carburant atteint `Car` **pour la voiture du joueur seulement** — les simulateurs
publient la télémétrie du réservoir de la voiture que vous conduisez et de personne
d'autre — et il est attaché en faisant correspondre `mID`, parce que le tableau de
télémétrie de LMU est indexé par `playerVehicleIdx` alors que le tableau de classement
ne l'est pas. L'attacher par position mettrait votre réservoir sur la voiture qui se
trouvait classée dans cette case.

## Être loin du volant

L'ingénieur ne dit rien, et **n'enregistre rien**, quand le pilote ne conduit pas.
Trois états, et il leur faut trois signaux différents :

* **En pause** — l'horloge du simulateur s'arrête alors que celle de cette machine
  continue, et l'écart est le signal. Pas `mGamePhase` : il indiquait *drapeau vert*
  pendant toute une session passée en pause dans le garage, avec `mCurrentET` figé à
  2218.0. La phase dit quel genre de session c'est, pas si elle tourne.
* **Dans le garage** — ici l'horloge continue, l'horloge ne peut donc pas être le
  signal. `mInGarageStall` l'est. Distinct de `in_pits`, qui couvre toute la voie des
  stands : une voiture en train de purger un arrêt est en course.
* **Confiée à l'IA** — `mControl` vaut 1, ce à quoi ressemble le mode spectateur.

**Rien n'est observé non plus, pas seulement rien dit.** Un simulateur en pause
republie la même image à l'infini, et donner cela au carnet de tours enregistre une
voiture qui ne couvre aucune distance aussi longtemps que quelqu'un laisse le jeu
posé là — un tour de référence corrompu plutôt qu'un tour manquant. L'état du spotter
est jeté à l'entrée pour la même raison : une voiture qui était à côté avant la pause
est un fait sur un instant qui est passé.

**Mettre en pause une course en ligne n'est pas détecté, et ne peut pas l'être.**
L'horloge continue là-bas, parce que la course continue — le menu est ouvert sur cette
machine et les voitures roulent toujours. Rien dans la mémoire partagée ne distingue
cela d'une course ordinaire, et inventer un signal pour cela ferait taire l'ingénieur
pendant une vraie course. Ce qui est la pire erreur des deux.
