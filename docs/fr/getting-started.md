# Prise en main

Installez-le, dites-lui quelle touche écouter, et parlez. Tout le reste dans ces
pages est facultatif.

![La fenêtre SimPitRadio sur l'onglet État](images/window.png)

## Installation

Téléchargez l'installateur depuis la
[page des versions](https://github.com/kidunot89/simpitradio/releases/latest) et
lancez-le. Windows vous avertira : les builds ne sont pas signés, donc
SmartScreen affiche « Windows a protégé votre ordinateur » et il faut choisir
**Informations complémentaires → Exécuter quand même**. C'est à quoi ressemble un
installateur non signé, et signer coûte de l'argent que ce projet ne dépense pas.

L'installation pose une seule question — **quelle langue** — avec celle de votre
Windows déjà sélectionnée. Cela fixe trois choses d'un coup : la fenêtre, le
modèle vocal, et la langue dans laquelle l'ingénieur parle et écoute. Vous
pourrez en changer plus tard dans l'onglet Langue.

**Il s'installe en administrateur, volontairement.** Windows jette les frappes
injectées vers un programme tournant avec plus de privilèges que l'émetteur, et
les simulateurs tournent souvent élevés. Sans cela, tout a l'air de fonctionner
et rien n'atteint jamais le jeu.

### Le premier lancement télécharge deux choses

Rien de volumineux ne voyage dans l'installateur, donc à la première ouverture on
vous propose de récupérer :

- **le modèle vocal**, environ 250 Mo, qui transforme votre voix en texte
- **un pack de voix** pour l'ingénieur, environ 45 Mo, s'il en existe un publié
  dans votre langue

Les deux, une seule fois. Le modèle vit hors du dossier d'installation, pour
qu'une mise à jour ne le coûte jamais deux fois. Dites « pas maintenant » et les
onglets Langue et Réglages les récupèrent quand vous voulez.

La version portable n'a pas d'installateur ni de question sur la langue, donc
elle la pose au premier lancement à la place.

## Choisissez une touche

**Réglages → Déclencheur.** Appuyez sur *Appuyez sur une touche…* puis sur celle
que vous voulez.

![La section Déclencheur de l'onglet Réglages](images/trigger.png)

La touche est **avalée au passage**, le jeu ne la voit donc jamais. Assignez-en
une que le jeu utilise déjà et rien ne casse. `F13` est la valeur par défaut
parce que la plupart des claviers n'en ont pas et que rien d'autre ne l'écoute.

**Un bouton de volant fonctionne aussi.** Sur la ligne **Bouton du volant**,
appuyez sur *Appuyez sur un bouton…* puis sur le bouton que vous voulez.
SimPitRadio ouvre le volant sans le retirer au jeu, le simulateur continue donc
de lire tous les boutons, y compris celui-là. Maintenez-le pour parler,
exactement comme la touche. Les deux restent actifs en même temps, vous pouvez
donc assigner les deux et utiliser celui qui est le plus proche.

L'autre solution est le logiciel propre à votre volant, ou
[JoyToKey](https://joytokey.net/) : mettez `F13` sur un bouton et assignez `F13`
ici. À privilégier si votre volant fait déjà tourner un logiciel auquel vous
faites confiance, ou si SimPitRadio n'arrive pas à ouvrir le périphérique.

## Réglez votre micro

**Audio → Microphone.** Choisissez l'entrée, maintenez le déclencheur et
regardez la barre de niveau. Elle montre le signal *après* le gain, ce que
reçoit le modèle vocal. Visez une crête aux alentours des trois quarts.

![L'onglet Audio](images/audio.png)

**La sortie ne devrait pas être le périphérique de votre simulateur.**
L'ingénieur, le coach et le bip d'enregistrement passent tous par ici ; la
pointer vers la même sortie que le jeu met le bip dans l'enregistrement.

Appuyez sur **Enregistrer 4 s et transcrire** pour entendre ce qui a été compris.
Rien n'est saisi nulle part pendant un test.

## Dites quelque chose

Maintenez le déclencheur, dites-le, relâchez.

1. La touche est avalée.
2. L'enregistrement démarre **immédiatement**, avant l'ouverture du chat du jeu.
   Rien de ce qui est dit dans les premières centaines de millisecondes n'est
   perdu.
3. Les touches de chat ouvrent le chat du jeu.
4. Au relâchement, le clip part vers le modèle vocal, sur votre propre
   processeur.
5. Le texte est saisi et les touches d'envoi sont déclenchées.

L'onglet État montre ce sur quoi le hook est armé et quand le déclencheur a été
vu pour la dernière fois. Si *Dernier déclenchement* ne bouge jamais, le problème
vient de la touche ou du hook, pas de la transcription.

![La carte État](images/status.png)

## Ensuite, si vous en voulez plus

L'ingénieur, le coach et le chat vocal sont tous désactivés tant que vous ne les
activez pas.

| | |
| --- | --- |
| [Chat texte](text-chat.md) | Le chat texte lui-même : profils, relecture avant envoi, que faire quand rien n'est saisi |
| [L'ingénieur](engineer.md) | Une voix nommée qui lit vos temps au tour, annonce les voitures à côté et répond aux questions |
| [Le coach](coaching.md) | Votre trajectoire face à celle d'un rival après chaque virage, avec ce qu'il faut changer |
| [La voix à la radio](voice-chat.md) | Entendre les autres pilotes de votre session, et seulement ceux qui sont proches |
| [Packs de voix](voicepacks.md) | Enregistrer ou installer la voix de l'ingénieur |

## Quand quelque chose ne va pas

**Regardez d'abord l'onglet État.** C'est le seul endroit qui montre ce que
l'application croit : la touche armée, l'exécutable au premier plan, le profil
utilisé et un journal en direct.

![Le journal sur l'onglet État](images/log.png)

- **Rien n'est saisi.** Voir [Rien n'est saisi](text-chat.md#rien-nest-saisi).
- **Rien n'est dit.** Voir [Rien n'est dit](engineer.md#rien-nest-dit).
- **Rien n'est dessiné.** Voir [Rien n'est dessiné](coaching.md#rien-nest-dessiné).

Le journal est aussi écrit dans un fichier. **État → Ouvrir le dossier des
journaux** vous y emmène, et c'est la première chose à joindre à un signalement.
