# La voix à la radio

SimPitRadio tape ce que vous avez dit dans le chat du jeu. Ceci ajoute l'autre
moitié : les pilotes contre qui vous roulez vous envoient aussi l'*audio*, et
vous l'entendez.

Discord existe déjà et tout le monde y est déjà. Ce que Discord ne sait pas
faire, c'est vous mettre dans une salle avec **qui que ce soit qui est dans
cette session**, sans l'avoir organisé à l'avance, et faire taire ceux qui
sont à quatre kilomètres.

## Ce qui voyage

**Le clip du push-to-talk, au relâchement. Pas un flux en direct.**

Le cycle du déclencheur enregistre déjà un clip pendant que la touche est
tenue et le remet à Whisper au relâchement. La voix réutilise exactement ce
clip : au relâchement il part vers Whisper *et* vers le relais, et les pairs
le rejouent. Rien du chemin d'enregistrement ne change.

Un flux en direct serait une autre application. Il lui faut des trames de
20 ms, un tampon de gigue, un mélangeur et une horloge de lecture, le tout sur
le chemin audio, et la récompense est que les gens vous entendent 1,5 seconde
plus tôt. Le clip est de toute façon ce qu'est une radio de stand : vous
tenez le bouton, vous dites une chose, elle arrive.

La conséquence à connaître : **un clip est atomique.** Il ne peut pas être
interrompu, il arrive entier ou pas du tout, et deux pilotes qui parlent en
même temps produisent deux clips qui font la queue plutôt que de se couper la
parole. Un week-end de course, c'est le meilleur des deux.

## Qui l'entend

Le relais est bête. Il diffuse un clip à tout le monde dans la salle et ne
décide pas qui devrait le recevoir, parce qu'il ne le peut pas — il n'a aucune
idée d'où est chacun sur la piste, et lui donner cette information serait pire
qu'inutile.

**La proximité est décidée sur la machine de l'auditeur.** La mémoire
partagée de LMU porte la position dans le monde de *chaque* voiture, pas
seulement la vôtre, donc chaque client sait déjà exactement à quelle distance
se trouve chaque autre pilote. Rien de positionnel n'est jamais publié au
relais, et la fonction marche même si l'exploitant du relais est hostile.

**C'est la vision qu'a l'auditeur de la position de celui qui parle qui
l'emporte.** Un clip arrive après que son émetteur a cessé de parler, donc la
position qu'il porte date d'une seconde ou deux. À vitesse de course, cela
représente cent mètres, et face à un rayon de 200 m, cent mètres tranchent la
question. Le bloc de classement contient chaque voiture telle qu'elle est
*maintenant*, et la question est de savoir qui est près de la voiture cible
quand le message est joué.

Le clip porte quand même la position de l'émetteur, en secours pour quelqu'un
que le bloc de l'auditeur n'a pas rattrapé : un pilote qui vient d'arriver, ou
dont l'entrée a disparu. Une position périmée vaut mieux qu'aucune.

Préférer la vue locale signifie aussi qu'un clip ne peut pas négocier son
passage à travers le filtre. Un client qui prétend être à côté de vous alors
qu'il est à un kilomètre est simplement mesuré là où il se trouve réellement.
C'est une conséquence de l'utilisation du chiffre le plus frais, et non un
mécanisme de sécurité — un locuteur que personne ne peut situer reste
audible, parce qu'un silence que personne ne peut expliquer est la pire
panne.

`proximity_only` sur le plugin LMU l'active ; `proximity_metres` fixe le
rayon. Désactivé, vous entendez toute la session, ce qui est ce que vous
voulez aux essais et dans un tour de formation.

### Spectateur

La proximité devrait se mesurer depuis la voiture à l'écran : suivre une
bagarre au milieu de laquelle on est, tout en entendant la radio depuis
quatre kilomètres plus loin où sa propre voiture est garée, n'est de la
proximité dans aucun sens qu'un spectateur reconnaîtrait.

Cela doit être **détecté**. Quelqu'un qui roule ne peut pas atteindre un menu
déroulant, et quelqu'un qui regarde ne devrait pas avoir à le faire.

**Le bloc de mémoire partagée ne le dit pas.** Trois sources plausibles ont
été vérifiées contre une session réellement regardée et écartées. Chacune a
l'air d'être la bonne, et aucune ne l'est :

- `telemetry.playerVehicleIdx` est le véhicule du *joueur*. Pendant qu'on
  regardait quelqu'un d'autre, il restait pointé sur la voiture garée de
  celui qui regardait.
- `appInfo.mOptionsLocation` a lu 0 du début à la fin.
- `$rFactor2SMMP_Graphics$` est publié et porterait à la fois une position de
  caméra et l'id de la place regardée, mais LMU ne le remplit jamais. Le
  tampon est entièrement à zéro à part son compteur de version, parce que le
  jeu n'appelle pas le rappel graphique à partir duquel le plugin rF2 le
  remplit. Le bloc Extended voisin était vivant au même moment, c'est donc un
  choix de LMU et non une installation cassée.

**L'API HTTP de LMU, elle, le dit.** `http://127.0.0.1:6397/rest/watch/standings`
est ce que lisent les overlays du jeu lui-même. Chaque entrée porte
`hasFocus`, posé sur la voiture regardée et distinct de `player`, qui reste
sur la vôtre. Son `slotID` est le même nombre que `mID` en mémoire partagée,
les deux se joignent donc directement. Cela fait partie du jeu et non d'un
plugin, il n'y a donc rien à installer.

Lu avec un délai court et mis en cache une seconde : cela tourne sur le cycle
du déclencheur, la réponse fait ~16 Ko, et l'application ne doit jamais
attendre un jeu en plein chargement. **Les échecs sont mis en cache aussi** —
sinon un jeu fermé coûte un délai d'attente à chaque pression.

Chaque échec donne None, et `SessionInfo.listener()` retombe alors sur la
voiture conduite puis sur None, que `audible` lit comme audible. Garder
silencieusement une voiture garée comme référence filtrerait la session par
un endroit que personne ne regarde, et aucun auditeur ne pourrait distinguer
cela d'une fonction cassée.

**« Proximité » veut dire sur la piste et nulle part ailleurs.** Ce sont des
mètres entre deux voitures dans le jeu, lus du simulateur, calculés
localement. Cela n'a rien à voir avec l'endroit où quiconque habite, et
aucune localisation physique n'est lue, déduite ni transmise. L'*hébergement*
de relais plus bas parle aussi de distance, au sens réseau — c'est une
question de routage entre serveurs, sans rapport avec qui vous pouvez
entendre.

## Quelle salle

L'identifiant de session est dérivé, jamais annoncé :

    sha256("pitradio/1:{mServerPublicIP}:{mServerPort}")[:32]

Tout le monde sur le même serveur de jeu calcule le même identifiant sans que
personne publie de quel serveur il s'agit — le relais apprend un hachage et
rien d'autre. Hors ligne et solo n'ont pas de serveur, donc ne produisent ni
identifiant ni salle, ce qui est le comportement correct et non un cas
particulier.

Le circuit est délibérément *absent* de la clé. Il change entre sessions sur
le même serveur, et une salle qui se dissout quand l'événement passe au
tracé suivant est une moins bonne salle.

L'identité dans une salle est le nom du pilote issu du bloc de classement.
`mSteamID` vaut zéro en pratique, il n'y a donc rien de mieux à disposition.

## Le relais

**Le code et la configuration du relais ne sont pas dans ce dépôt.**
SimPitRadio est public ; le serveur, son Terraform et son Ansible sont
privés, avec le secret client OAuth dont ils ont besoin. Terraform et Ansible
existent là-bas pour une seule tâche : monter de façon reproductible, depuis
une image propre, un hôte vocal **fourni par un pilote**.

L'adresse du relais de base n'est pas non plus dans ce dépôt. Elle est écrite
dans `endpoints.py` **au moment de la compilation**, donc une copie du code —
ou un fork — n'a aucune adresse et la voix est simplement indisponible. C'est
un état qui fonctionne, pas un état cassé : mieux vaut cela que chaque clone
des sources pointant un micro vers un serveur dont le propriétaire n'a jamais
accepté de le porter.

Rien d'autre dans l'application ne doit coder une adresse en dur. Un endroit
à écraser, un endroit où regarder quand elle est fausse.

    wss://<relais>/chat/{id-de-session}

Un WebSocket par client, TLS, les clips en trames binaires avec un petit
en-tête. C'est tout le protocole. TLS parce qu'un relais est la machine d'un
inconnu et que l'audio de votre voix ne devrait pas la traverser en clair ;
WebSocket parce qu'il survit à tous les NAT et pare-feu d'entreprise que
l'UDP brut ne franchit pas, et parce que la bande passante audio de vingt
pilotes appuyant sur un bouton de temps en temps n'est rien.

**Pas littéralement du pair-à-pair.** Le vrai P2P demande ICE, STUN et un
repli TURN — et TURN est un relais, donc le chemin de repli est de toute
façon cette conception, atteinte après avoir tiré une pile WebRTC dans une
compilation Nuitka qui se bat déjà avec des dépendances natives. Le relais
est une petite boîte, et il est honnête sur le fait d'en être une.

### Hôtes communautaires

Les relais existent pour être *près de ceux qui parlent*. Une grille tirée de
trois continents routée par une boîte à Francfort paie l'Atlantique deux fois
sur chaque clip ; un relais choisi pour le groupe, non. C'est toute la
raison pour laquelle des pilotes peuvent héberger : ni le coût, ni la
décentralisation pour elle-même — la géographie.

Terraform fabrique la machine ; Ansible installe le relais, l'unité systemd
et le certificat TLS, de sorte qu'un hôte est reproductible depuis une image
Ubuntu propre sans aucune étape manuelle.

DigitalOcean OAuth d'abord, puisque c'est ce qui existe aujourd'hui. Linode a
un vrai flux d'application OAuth et peut suivre. **AWS ne peut pas** : il n'a
pas d'OAuth grand public pour le provisionnement — ce sont des clés IAM ou le
SSO d'Identity Center — il lui faut donc son propre chemin plutôt qu'un
bouton.

#### En choisir un est une décision de groupe, pas une décision personnelle

**Tous les clients d'une session doivent choisir le même relais, ou ils n'en
choisissent aucun.** Livrés à eux-mêmes, chacun choisirait l'hôte le plus
proche de *lui*, ce qui pour une grille transatlantique donne deux relais,
deux salles, et les deux moitiés de la session assises dans ce qui ressemble
exactement à une fonction qui marche, sans personne d'autre dedans. C'est la
même panne silencieuse qu'une clé de session qui ne correspond pas, atteinte
par un autre chemin.

Il y a donc un coordinateur, sur l'hôte de base fixe, et il décide :

1. Les clients rejoignent la salle sur le relais configuré dans la
   compilation et rapportent leur aller-retour mesuré vers chaque relais
   candidat.
2. Le coordinateur choisit celui qui a le meilleur pire cas sur toute la
   salle — il minimise la latence du pilote le *plus lent*, pas la moyenne,
   parce que l'idée est que personne ne soit laissé de côté.
3. Il dit à tout le monde de migrer, et ils s'y reconnectent ensemble.

L'hôte de base est aussi le relais de repli, et c'est ce qui rend la chose
abordable : le coordinateur doit de toute façon être toujours allumé, autant
qu'il porte l'audio des sessions trop petites ou trop locales pour valoir un
déménagement.

#### Pourquoi ne pas relier tous les hôtes entre eux

L'alternative évidente : laisser chaque client se connecter au relais le
plus proche de *lui*, et faire que les relais se transmettent les clips.
C'est une vraie conception — Mumble relie ses serveurs ainsi — et elle est
réellement plus élégante sur un point, parce qu'elle supprime la décision de
groupe ci-dessus. Il n'y a rien à convenir si la salle s'étend sur tous les
relais, la panne de salle scindée ne peut donc pas se produire du tout.

C'est quand même le mauvais compromis ici, pour une raison : **nous envoyons
des clips, pas un flux en direct.** Un clip est expédié après que le
locuteur a cessé de parler, donc personne ne peut percevoir la différence
entre 90 ms et 250 ms de routage. Cette différence est l'essentiel de
l'argument en faveur de la géographie, et la totalité de l'argument pour
payer deux sauts de plus afin de l'améliorer.

Ce que coûte le pontage, ce ne sont pas des sauts, c'est de l'état. Les
relais devraient se transmettre l'appartenance aux salles, s'authentifier
mutuellement et se prémunir contre les boucles et les livraisons en double,
et un relais hébergé par un pilote qui rejoint ce tissu peut voir le trafic
de salles où il n'a aucun membre. C'est un projet de systèmes distribués
boulonné au flanc d'une application de dictée, au service d'un budget de
latence que cette conception n'a pas.

Si SimPitRadio passe un jour au direct, cela s'inverse et le pontage devient
la bonne réponse. La forme à construire alors : un maillage complet avec un
secret partagé, l'appartenance aux salles propagée de proche en proche, et
chaque clip portant un identifiant avec une limite d'**un saut** entre
relais — pas de retransmission transitive, ce qui tue net les boucles de
routage et borne l'éventail au lieu de lui faire confiance.

#### Quand un hôte disparaît

Un relais qui disparaît ne doit pas mettre fin à la conversation. Le
coordinateur tient la salle, remarque que le relais ne répond plus, refait
le choix sur ce qui reste et fait migrer les pilotes restants — le même
mécanisme que le choix initial, il n'y a donc pas de chemin de bascule
séparé à rater. Les clients gardent la connexion au coordinateur ouverte
exactement pour cela : c'est ce qui survit.

Un pilote qui quitte la session n'emporte pas son relais en pleine course.
Sa machine n'est pas le relais — c'est un droplet qu'il a provisionné — et
le retirer sous les pieds de ceux qui roulent encore serait le pire moment
possible.

#### Quand la session se termine

Les salles sont démontées, pas laissées en marche. LMU rapporte sa phase de
jeu, donc un client qui voit la session se terminer le dit ; quand le
dernier client part, ou que la salle reste silencieuse au-delà d'un délai
d'inactivité, le coordinateur la ferme. Un relais sans salle restante est
candidat à `terraform destroy`, et c'est la différence entre coûter à un
pilote quelques centimes par événement ou un droplet pour toujours.

Le délai d'inactivité compte autant que le signal explicite. Un client qui
plante, bascule dans le néant ou perd son réseau n'envoie jamais rien — rien
ne doit donc dépendre de ce qu'il le fasse.

## Consentement

Le chat vocal est **désactivé jusqu'à ce que vous l'activiez**, et l'onglet
Voix dit qui peut vous entendre avant de dire quoi que ce soit d'autre. Une
application qui ouvrirait discrètement le micro à vingt inconnus serait une
trahison, aussi bonne soit la fonction.

Push-to-talk uniquement. Il n'y a pas de mode micro ouvert et il ne devrait
pas y en avoir : le déclencheur est le consentement.
