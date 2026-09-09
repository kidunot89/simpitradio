# Prise en main

Installez-le, dites-lui quelle touche écouter, et parlez. Tout le reste dans ces
pages est facultatif.

![La fenêtre SimPitRadio sur l'onglet État](images/window.png)

## Installation

Téléchargez l'installateur depuis la
[page des versions](https://github.com/kidunot89/simpitradio/releases/latest) et
lancez-le. Windows vous avertira : les binaires ne sont pas signés, donc
SmartScreen affiche « Windows a protégé votre ordinateur » et il faut choisir
**Informations complémentaires → Exécuter quand même**. C'est à quoi ressemble un
installateur non signé, et signer coûte de l'argent que ce projet ne dépense pas.

L'installation pose une seule question — **quelle langue** — avec celle de votre
Windows déjà sélectionnée. Cela fixe trois choses d'un coup : la fenêtre, la
reconnaissance vocale, et la langue dans laquelle l'ingénieur de course parle et
écoute. Vous pourrez en changer plus tard dans l'onglet Langue.

**Il s'installe en administrateur, volontairement.** Windows jette les frappes
injectées vers un programme tournant avec plus de privilèges que l'émetteur, et
les simulateurs tournent souvent élevés. Sans cela, tout a l'air de fonctionner
et rien n'atteint jamais le jeu.

### Le premier lancement télécharge deux choses

Rien de volumineux ne voyage dans l'installateur, donc à la première ouverture on
vous propose de récupérer :

- **le modèle vocal**, environ 250 Mo, qui transforme votre voix en texte
- **une voix enregistrée** pour l'ingénieur, environ 45 Mo, s'il en existe une
  publiée dans votre langue

Les deux, une seule fois. Le modèle vit hors du dossier d'installation, pour
qu'une mise à jour ne le coûte jamais deux fois. Si vous dites « pas
maintenant », les onglets Langue et Réglages font la même chose quand vous
voulez.

Le zip portable n'a pas d'installateur, donc pas de question sur la langue : il
la pose au premier lancement à la place.

## Choisissez une touche

**Réglages → Déclencheur.** Appuyez sur *Appuyez sur une touche…* puis sur celle
que vous voulez.

![La section Déclencheur de l'onglet Réglages](images/trigger.png)

La touche est **avalée au passage**, le jeu ne la voit donc jamais — ce qui veut
dire que vous pouvez en prendre une que le jeu utilise déjà. `F13` est la valeur
par défaut parce que la plupart des claviers n'en ont pas et que rien d'autre ne
l'écoute.

**Un bouton de volant fonctionne.** Associez-le à une touche clavier avec
[JoyToKey](https://joytokey.net/) et affectez cette touche ici. SimPitRadio ne
lit pas les volants directement, et la raison est dans
[les notes de l'ingénieur](engineer.md#réglages-par-simulateur) : une jante Fanatec a
énuméré 79 entrées sans jamais signaler un appui via aucune de quatre
bibliothèques différentes, et lire une manette Steam impliquait de la retirer à
Steam.

## Réglez votre micro

**Audio → Microphone.** Choisissez l'entrée, maintenez le déclencheur et
regardez la barre de niveau : elle montre le signal *après* le gain, c'est-à-dire
ce que Whisper reçoit réellement. Visez des crêtes aux trois quarts environ.

![L'onglet Audio](images/audio.png)

**La sortie ne devrait pas être le périphérique de votre simulateur.**
L'ingénieur, le coach et le bip d'enregistrement passent tous par ici ; la
pointer vers la même sortie que le jeu met le bip dans l'enregistrement.

Appuyez sur **Enregistrer 4 s et transcrire** pour entendre ce qui a été compris.
Rien n'est saisi nulle part pendant un test.

## Dites quelque chose

Maintenez la touche, dites ce que vous voulez dire, relâchez.

1. La touche est avalée.
2. L'enregistrement démarre **immédiatement** — avant l'ouverture de la fenêtre
   de chat, pour que rien des premières centaines de millisecondes ne soit perdu.
3. Les touches de chat ouvrent la fenêtre de chat du jeu.
4. Au relâchement, le clip part vers Whisper, sur votre propre processeur.
5. Le texte est saisi et les touches d'envoi sont déclenchées.

L'onglet État montre ce sur quoi le hook est armé et quand le déclencheur a été
vu pour la dernière fois. Si *Dernier déclenchement* ne bouge jamais, le problème
vient de la touche ou du hook, pas de la transcription.

![La carte État](images/status.png)

## Ensuite, si vous en voulez plus

Rien de ce qui suit n'est actif par défaut.

| | |
| --- | --- |
| [Chat texte](text-chat.md) | La dictée elle-même : profils, relecture avant envoi, que faire quand rien n'est saisi |
| [L'ingénieur](engineer.md) | Une voix nommée qui lit vos temps au tour, annonce les voitures à côté et répond aux questions |
| [Le coach](coaching.md) | Votre trajectoire face à celle d'un rival après chaque virage, avec ce qu'il faut changer |
| [La voix à la radio](voice-chat.md) | Entendre les autres pilotes de votre session, et seulement ceux qui sont proches |
| [Packs de voix](voicepacks.md) | Enregistrer ou installer la voix de l'ingénieur |

## Quand quelque chose ne va pas

**Regardez d'abord l'onglet État.** C'est le seul endroit qui montre ce que
l'application croit : la touche armée, l'exécutable au premier plan, le profil
utilisé et un journal en direct.

![Le journal sur l'onglet État](images/log.png)

- **Rien n'est saisi** — voir [Rien n'est saisi](text-chat.md#rien-nest-saisi).
- **Rien n'est dit** — voir [Rien n'est dit](engineer.md#rien-nest-dit).
- **Rien n'est dessiné** — voir [Rien n'est dessiné](coaching.md#rien-nest-dessiné).

Le journal est aussi écrit dans un fichier. **État → Ouvrir le dossier des
journaux** vous y emmène, et c'est la première chose à joindre à un signalement.
