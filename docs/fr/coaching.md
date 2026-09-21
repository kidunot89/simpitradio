# Le coach

Choisissez quelqu'un à étudier. Chaque fois que vous terminez un segment du
circuit, le panneau trace votre trajectoire face à la sienne, et le coach vous
dit quoi faire autrement.

> *Tosa, tu as perdu de la vitesse au milieu du virage parce que tu étais
> encore sur le frein à la corde, et il prend la corde plus tard, donc sa
> sortie se redresse plus tôt.*

Il lit vos pédales, votre volant et votre rapport, ainsi que le chronomètre,
donc ce qu'il dit est une cause et non une reformulation de l'écran des temps.
Bloquez une roue ou sortez de la piste et il le dit tout de suite, pendant que
vous sentez encore ce que vous avez fait.

Le coach n'est pas l'ingénieur. Il a sa voix, son volume et ses notifications,
et chaque annonce arrive dans cette voix pour que vous sachiez toujours lequel
des deux vous parle. **Coaching → Qui** le configure ; cocher *Utiliser
l'ingénieur comme coach* leur donne une seule voix si vous préférez.

## Démarrage rapide

1. Faites trois ou quatre tours. Le coach doit d'abord comprendre le circuit —
   voir [D'où viennent les segments](#doù-viennent-les-segments).
2. Maintenez le déclencheur et dites **« coache-moi »**.
3. Dites **« concentre-toi sur P3 »**, ou **« concentre-toi sur moi »** pour être mesuré face à
   votre propre meilleur tour.
4. Roulez. Après chaque virage le panneau le dessine et le coach parle.

Rien ici n'est une case à cocher avant une session. Le coaching se demande à
voix haute quand vous le voulez et se retire quand vous le dites, parce que
savoir si vous voulez qu'on vous parle dans un virage est une décision qui se
prend tour après tour.

## Lui parler

La plupart des formules ci-dessous font deux mots ou plus, le nom du coach
devant elles est donc facultatif. Les exceptions sont « étudie » et « regarde » :
ce sont deux mots isolés, et tout ce qui suit l'un des deux est pris pour le
nom du pilote, donc les deux ont besoin du nom du coach devant. *Chief, étudie
Estre.*

| Pour ceci | Dites |
| --- | --- |
| Démarrer le coaching | **coache-moi** · *guide-moi* · *montre-moi les trajectoires* · *démarre le coaching* |
| Arrêter | **arrête le coaching** · *termine le coaching* · *plus de trajectoires* |
| Choisir à qui vous comparer | **étudie Estre** · *concentre-toi sur P3* · *garde un œil sur le leader LMP2* |
| Vous comparer à votre meilleur | **concentre-toi sur moi** · *étudie mon meilleur* · *concentre-toi sur mon tour idéal* |
| Revenir au choix automatique | **cible par défaut** · *cible automatique* |
| Entendre ce qui tourne | **quel coaching est activé** |
| Redessiner le virage que vous venez de faire | **last corner** · *that corner* |

Un mot seul prenant un argument sans limite avalerait sinon un message destiné
à la session. « concentre-toi sur » et « garde un œil sur » sont assez longs pour être
sûrs tout seuls, c'est pourquoi ils sont là.

**Vous n'êtes pas obligé de choisir un rival.** Demandez-lui de se concentrer
sur *vous* et la seconde ligne devient votre propre tour idéal — non pas un
tour que vous avez roulé, mais le meilleur que vous ayez réussi dans chaque
virage, assemblé. Aucun tour que vous ayez roulé ne lui ressemble. Une séance
d'essais vide a quand même quelqu'un à battre, et c'est l'adversaire honnête
sur une piste vide.

## D'où viennent les segments

**Le circuit est déduit des tours roulés pendant la session, pas d'une base de
données.** Chaque tour roulé dans la session — le vôtre et celui de tous les
autres — est versé sur une grille au pas de cinq mètres, et la médiane de ce
qui est passé par chaque point est l'endroit où se trouve la route. Quatre
tours doivent croiser un point avant qu'on lui fasse confiance, et la moitié
du circuit doit être connue avant qu'une route soit construite.

C'est pourquoi cela fonctionne sur n'importe quel tracé dans n'importe quel
simulateur, y compris ceux que personne n'a jamais catalogués. Là où un
catalogue existe, vous avez des noms : « Tosa » plutôt que « virage sept ». Là
où il n'y en a pas, vous avez des numéros et tout le reste fonctionne
exactement pareil.

Le regroupement se fait deux fois. La première passe n'a pas de route à
laquelle se référer, elle utilise donc le cap de la voiture pour déterminer où
est le travers de la piste — et une voiture qui zigzague ne pointe jamais le
long de la route, l'erreur va donc dans le même sens à chaque tour. Une fois
qu'il y a une route, sa propre direction est la bonne référence et la seconde
passe corrige. Sur un cercle synthétique parcouru avec un zigzag de trois
mètres, la première passe a placé la route à deux mètres et demi de là où
elle était.

### Ce qui compte comme segment

Un segment est un virage plus l'entrée et la sortie, parce que c'est ce que
vous conduisez.

- **L'entrée** remonte jusqu'à l'endroit où vous avez freiné, plafonnée à
  250 m. Elle n'a pas de longueur fixe : freinez plus tard et le segment
  commence plus tard.
- **La sortie** va 50 m au-delà, assez pour montrer par où la voiture est
  ressortie et où elle pointait.
- **Deux virages pour lesquels vous freinez une fois font un segment.** Club
  et Vale sont une seule chose à conduire et une seule chose à regarder ; la
  paire d'épingles de Sebring aussi.
- **Les courbes prises à plat sont sautées.** Un virage tenu au-delà de 90 %
  d'accélérateur n'a pas de point de freinage à déplacer ni de vitesse
  d'entrée à emporter, il est donc traité comme une ligne droite. Il reste sur
  la carte et garde son nom — il n'est simplement jamais mis devant vous.
  Activez **Lignes droites et portions à fond** sous *Ce qui est coaché* pour
  les voir quand même.

La fusion et le saut demandent tous deux un tour de référence. Sans lui, le
coach n'a aucun motif de décider que deux virages n'en font qu'un, il les
laisse donc séparés.

## Ce qu'il dit

**Coaching → Ce qui est coaché → Niveau de pilote** décide de la quantité.
Les trois niveaux regardent le même virage et trouvent le même défaut ; ils
suppriment des propositions, pas des constats.

| Niveau | Ce que vous recevez |
| --- | --- |
| **débutant** | Tout — ce qui était mieux, ce qui était moins bien, la cause et quoi faire |
| **intermédiaire** | Sans la conséquence. Le défaut et le remède, en supposant que vous savez ce qu'un sous-virage à la corde fait à une sortie |
| **avancé** | Sans le remède non plus. Ce qui était bon et ce qui n'allait pas ; s'entendre dire « freine plus tôt » revient souvent à s'entendre dire ce qu'on sait déjà |

Une partie de ce qu'il mesure, et les seuils qu'il utilise, pour que vous
sachiez quand il se tait volontairement :

- Deux vitesses doivent différer d'un demi-mètre par seconde — moins de
  2 km/h — avant que cela vaille la peine d'être mentionné. En dessous, vous
  avez fait la même chose tous les deux, et l'écart tient à l'endroit où les
  tours ont été échantillonnés.
- Utiliser la route veut dire atteindre 85 % de sa demi-largeur, pas la
  totalité. Un pilote qui pose une roue exactement sur la ligne blanche à
  chaque tour est un pilote qui prend des track limits, et la trajectoire qui
  gagne est celle qui s'en approche.
- Une pédale compte comme enfoncée à 5 % de course, et le volant comme tourné
  à 5 % de braquage. Les pédales et volants de simulation reposent rarement
  exactement à zéro.

## Notifications

**Coaching → Notifications** active et coupe indépendamment les trois sortes
d'annonces du coach :

- **Analyse de segment** — le compte rendu après chaque virage.
- **Erreurs sur le moment** — une roue bloquée, une sortie de piste, annoncées
  immédiatement plutôt que mises de côté.
- **Où ils étaient plus rapides** — une fois par tour.

Elles sont séparées des Comportements de l'ingénieur exprès, pour que baisser
le coaching ne baisse pas le spotter avec lui. Les trois ont toujours besoin
du mode coach actif ; aucune ne dit rien tant que vous n'avez pas demandé à
être coaché.

## Le diagramme

![Curva Parabolica, votre trajectoire face à celle d'un rival](images/segment_parabolica.png)

La Parabolica de Monza, tirée d'une vraie session. Le tracé clair est le
freinage, le tracé sombre est sous l'accélérateur ; le cercle est l'endroit où
chaque voiture a freiné et le triangle celui où elle est revenue sur les gaz,
pointant dans le sens de la marche.

Le panneau tient trois diagrammes : un qui arrive, un dont on parle au
centre, un qui s'en va. La position, c'est l'avancement : un coup d'œil vous
dit où en est le coach. Les diagrammes flottent au-dessus du jeu, sans rien
derrière eux.

Votre trajectoire est tracée en **orange vers rouge**, celle d'un rival en
**indigo vers cyan**. La teinte dit à qui est la ligne. **La clarté dit ce que
faisaient les pieds** — la plus claire sur les freins, la plus sombre sur les
gaz. Les deux lignes sont en pointillés, et les deux motifs sont décalés d'une
demi-période, si bien que là où les voitures prennent exactement la même
trajectoire chacune transparaît dans les trous de l'autre au lieu que l'une
cache l'autre. Le nom de chaque pilote est inscrit dans le coin le plus vide
du diagramme, dans la couleur de ce pilote, pour que vous n'ayez jamais à
retenir quelle rampe est à qui.

La route est un ruban sombre entre deux lignes blanches, pris de la lecture du
bord de piste du simulateur lui-même plutôt que deviné à partir de la
trajectoire — une roue posée hors de la ligne est donc dessinée hors de la
ligne.

![La file de diagrammes](images/diagram_queue.png)

Trois diagrammes : un qui arrive, celui dont on parle au centre, un qui s'en
va. Celui du milieu est celui dont le coach est en train de parler.

### Ce que cela donne depuis le baquet

![Tosa et le virage d'avant, dessinés par-dessus le cockpit à Imola](images/incar_tosa.jpg)

Imola, en pleine session. Deux diagrammes sont affichés en même temps — le
virage qui vient de finir et celui d'avant — et tous deux se nomment depuis le
catalogue du circuit plutôt que par numéro. Les diagrammes se posent sur le
jeu sans rien derrière, si bien que la seule chose ajoutée à l'écran est le
dessin.

![Un virage à Daytona avec les deux trajectoires et leurs vitesses](images/incar_daytona.jpg)

La même chose sur un circuit que personne n'a catalogué : le virage s'appelle
`T5` au lieu d'être nommé, et tout le reste fonctionne à l'identique — la
route depuis la lecture du bord de piste du simulateur, les deux lignes en
pointillés et décalées pour qu'aucune ne cache l'autre, et les vitesses à
l'entrée, au point de corde et à la sortie.

**Coaching → Schéma de segment** le place, le dimensionne, règle son opacité
et choisit dans quel sens la file avance. **Afficher le panneau** met trois
virages d'exemple pour que vous puissiez le glisser où vous voulez et le
dimensionner face au vrai.

Il dessine par-dessus un jeu en sans-bordure ou en fenêtre. Rien ne dessine
par-dessus le plein écran exclusif — c'est une propriété du mode d'affichage,
pas un réglage.

## L'entraîneur au freinage dégressif

Une note de piano à chaque fois qu'un pneu atteint la limite d'adhérence au
freinage, pour que le relâchement devienne quelque chose qui s'entend plutôt
que quelque chose qu'on déduit d'un temps au tour après coup.

Relâcher le frein est ce qui s'apprend le plus difficilement au toucher : la
pédale ne renvoie presque rien, la cible bouge à mesure que la voiture ralentit
et que le braquage arrive, et un pilote peut passer une saison loin sous la
limite sans jamais s'en apercevoir. Une note par palier de relâchement, pas un
son continu — un son qui suivrait le glissement serait un buzzer qu'on
apprend à ignorer, et il dirait « vous êtes ici » au lieu de « agissez
maintenant ».

| Ce que vous entendez | Ce que cela veut dire |
| --- | --- |
| Trois à six notes descendantes | Un relâchement propre |
| Une note, puis le silence | Vous avez lâché le frein trop vite |
| Aucune note | La limite n'a jamais été trouvée |
| Une note grave hors de la gamme | Un pneu a bloqué |

| Pour ceci | Dites |
| --- | --- |
| Démarrer | **travaille le freinage** · *on va travailler le freinage* · *entraînement au freinage* |
| Arrêter | **termine l'entraînement au freinage** · *arrête de travailler le freinage* |

Il apprend le rayon de roulement de votre voiture sur les premières zones de
freinage, il fonctionne donc dans n'importe quelle catégorie et avec la
répartition de freinage où vous voulez. **Coaching → Entraîneur au freinage
dégressif** règle s'il s'arme avec la session et le volume des notes. Son
volume est distinct de celui du coach parce que les deux sont mélangés plutôt
que mis en file — une note sonne par-dessus ce qui est en train d'être dit, et
une note n'a qu'à être remarquée là où la parole doit être comprise.

## Rien n'est dessiné

**Laissez-lui quelques tours.** Sous quatre tours à travers une portion de
circuit, il n'y a pas de route là ; et avec moins de la moitié du circuit
connue, il n'y a pas de route du tout. C'est la réponse habituelle.

**Vérifiez que le simulateur publie une position.** Les lignes sont tracées à
partir de coordonnées X/Z et du bord de piste. Un simulateur qui ne les
publie pas vous donne quand même les temps au tour, les erreurs et l'analyse
parlée ; il ne peut pas vous donner une image. Voir
[Ce que chaque simulateur sait faire](engineer.md#ce-que-chaque-simulateur-sait-faire).

**Vérifiez que ce n'est pas du plein écran exclusif.** Sans-bordure ou
fenêtré seulement.

**Vérifiez que vous l'avez bien demandé.** Le coaching est coupé jusqu'à ce
que vous le disiez. Quand il démarre, il répond « coaching », puis contre qui
il vous mesure, et soit combien de segments il a, soit « j'apprends le
circuit ».
