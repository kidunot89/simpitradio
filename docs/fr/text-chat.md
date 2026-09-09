# Chat texte

Ce pour quoi SimPitRadio a été construit. Maintenez une touche, dites ce que vous
voulez dire, relâchez — et cela apparaît dans la fenêtre de chat du jeu, tapé,
sans que vos mains quittent le volant.

Tout le reste de l'application a poussé à partir de là. L'ingénieur, le coach et
le chat vocal partagent la même touche et le même enregistrement ; le chat texte
est ce qu'il advient des mots quand rien d'autre ne les a réclamés.

## Ce qui se passe pendant que vous maintenez la touche

1. **La touche est avalée.** Le jeu ne voit jamais le déclencheur, elle peut donc
   être une touche que le jeu utilise aussi.
2. **L'enregistrement démarre immédiatement** — avant l'ouverture de la fenêtre
   de chat, pas après. L'ouvrir prend quelques centaines de millisecondes, et
   tout ce qui serait dit pendant ce temps serait perdu.
3. **Les touches de chat sont envoyées** pour ouvrir la fenêtre de chat du jeu,
   et l'application attend `pre_delay_ms` qu'elle prenne le focus.
4. **Vous relâchez.** L'enregistrement s'arrête et le clip part vers Whisper, sur
   votre propre processeur.
5. **Le texte est saisi**, puis les touches d'envoi sont déclenchées.

Si les mots s'avèrent être une commande pour l'ingénieur ou le coach, on y répond
à la place et rien n'est tapé. Cette décision est volontairement étroite — voir
[Lui parler](engineer.md#lui-parler) — parce que la même touche envoie des
messages à tout le monde dans votre session, et une commande que l'application
invente est un message qui n'arrive jamais, en silence.

## L'éteindre

**Chat texte → Envoyer au jeu** est l'interrupteur vers lequel se tourner en
pleine course quand une session devient publique. Éteint, le déclencheur ne sert
plus qu'à la voix et à l'ingénieur : pas de touches de chat, pas de saisie, rien
d'envoyé.

Il existe un second interrupteur par jeu, sous Profils. « Ce jeu a-t-il une
fenêtre de chat » est un fait sur le jeu plutôt qu'une décision à prendre à chaque
session — Assetto Corsa hors ligne n'a pas de chat à ouvrir, donc chaque pression
envoyait au jeu un Entrée qui y voulait dire autre chose. Réglez-le une fois et
oubliez-le. L'interrupteur global l'emporte toujours : éteint là, éteint partout.

## Vérifier un message avant qu'il parte

Par défaut le message est envoyé dès qu'il est tapé. Whisper se trompe parfois, et
dans une session publique une erreur est le problème de tout le monde — chaque
profil a donc une bascule **Envoyer automatiquement**.

Désactivée, le message est saisi dans la fenêtre de chat et y reste. Votre
déclencheur décide alors de son sort, sans lâcher le volant :

| Geste | Ce qu'il fait |
| --- | --- |
| **Appui bref** | L'envoyer |
| **Deux appuis brefs** | L'effacer |
| **Maintien** | L'effacer et enregistrer un remplaçant |

L'onglet État affiche **en attente d'envoi** tant qu'un message y patiente.

Si vous avez des boutons en trop, **Réglages → Déclencheur** associe aussi des
touches directement à *Envoyer le message en attente* et *Effacer le message en
attente*. Elles agissent immédiatement, sans fenêtre de double appui à patienter,
et coexistent avec les gestes plutôt que de les remplacer.

**Un appui bref ne peut pas être traité tout de suite**, car tant que la fenêtre
de double appui n'est pas close, il pourrait en être la première moitié. Cette
attente est `review.double_tap_ms`, environ un tiers de seconde. Mettez-la à `0`
dans la configuration pour envoyer immédiatement et renoncer à l'effacement par
double appui. `review.tap_ms` est la limite entre un appui bref et un maintien.

**Une pression alors qu'un message est en attente lance l'enregistrement tout de
suite**, avant de savoir si ce sera un appui bref ou un maintien. Attendre de le
savoir avalerait les premiers mots d'un nouvel enregistrement ; le tampon est
jeté si c'était finalement un appui bref.

## Profils

Le profil qui s'applique est décidé par l'exécutable qui a le focus, plusieurs
simulateurs peuvent donc être configurés en même temps et le bon est utilisé sans
qu'on vous demande rien.

Le réglage qui compte le plus est **Délai d'ouverture du chat**
(`pre_delay_ms`). La fenêtre de chat a besoin de quelques images pour s'ouvrir et
prendre le focus, et taper trop tôt perd les premiers caractères. Commencez à
350 ms et augmentez si les messages arrivent tronqués.

| Réglage | À quoi il sert |
| --- | --- |
| **Délai d'ouverture du chat** | Combien de temps attendre après l'ouverture avant de taper. Celui à augmenter si les messages arrivent tronqués |
| **Touches d'ouverture du chat** | Ce qui ouvre le chat. Entrée sur la plupart des simulateurs |
| **Touches d'envoi** | Ce qui l'envoie. Entrée à nouveau, en général |
| **Touches d'annulation** | Ce qui ferme la fenêtre sans envoyer, pour effacer un message en attente |
| **Maintien des touches** | Combien de temps chaque touche est tenue. Les jeux lisent l'entrée une fois par image, donc une pression plus courte qu'une image est une pression que le jeu ne voit jamais |
| **Délai de frappe** | L'écart entre les caractères |
| **Nombre maximal de caractères** | Les messages plus longs sont coupés. La plupart des simulateurs ont leur propre limite |
| **Envoyer automatiquement** | Désactivé pour relire avant d'envoyer — voir ci-dessus |
| **Plugin de session** | Lit qui est dans la session pour que les noms se transcrivent correctement et deviennent des mentions. Laissez sur *automatique* |

### Unicode ou codes de balayage

**Mode de frappe** décide comment les caractères parviennent au jeu. *Unicode*
envoie le caractère lui-même et gère n'importe quelle disposition de clavier et
n'importe quel alphabet. Certains jeux l'ignorent parce qu'ils lisent des codes de
balayage matériels à la place ; pour ceux-là, passez en *scancode*, qui tape comme
si les touches avaient été enfoncées physiquement.

Les codes de balayage se limitent à ce qu'un clavier américain peut produire, donc
les caractères accentués et les alphabets non latins n'y survivent pas. Essayez
unicode d'abord ; ce réglage existe parce que « le jeu ignore ce que nous tapons »
devait être un changement de configuration et non de code.

Les deux ont aussi une temporisation différente, et c'est pourquoi ce sont des
modes distincts. Les touches en scancode sont tenues `key_hold_ms` parce que les
jeux lisent l'entrée une fois par image. Le texte tapé, non : il passe par la file
de messages, et 40 ms par caractère ferait durer huit secondes un message de 200
caractères.

## Noms et vocabulaire

Whisper transcrit ce qu'il entend, et les noms de pilotes sont exactement ce qu'il
réussit le moins bien. Le plugin de session lit qui est réellement dans votre
session et lui fournit ces noms, si bien que « Estre » ressort en « Estre » et non
en « Ester ».

**Vocabulaire** ajoute vos propres mots par-dessus : noms de sponsors, un nom
d'équipe, l'orthographe réelle des pseudos de vos amis. Tout ce que vous vous
surprenez à corriger mérite d'y être.

## Rien n'est saisi

**Regardez d'abord l'onglet État.** Il montre ce sur quoi le hook est armé en ce
moment et quand le déclencheur a été vu pour la dernière fois. Si *Dernier
déclenchement* ne bouge jamais, le problème vient de la touche ou du hook, pas de
la transcription.

**Il doit tourner en administrateur.** Windows jette l'entrée injectée visant un
processus dont le niveau d'intégrité est plus élevé que celui de l'émetteur, et
les simulateurs tournent souvent élevés. La version installée le demande
automatiquement.

**Vérifiez que le profil correspond.** L'onglet État journalise le nom de
l'exécutable au premier plan ; s'il ne fait partie d'aucun de vos profils, c'est
le profil par défaut qui sert, et ses touches de chat ne conviennent peut-être pas
à ce jeu.

**Vérifiez le délai d'ouverture du chat.** Des messages arrivant amputés de leurs
premiers caractères, c'est un `pre_delay_ms` trop bas, à chaque fois.

**Vérifiez que le jeu n'ignore pas l'unicode.** Si la fenêtre de chat s'ouvre et
que rien n'y apparaît, essayez le mode de frappe *scancode*.
