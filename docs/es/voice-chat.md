# Voz en la radio

SimPitRadio escribe lo que dijiste en el chat del juego. Esto añade la otra mitad:
la gente contra la que corres te manda también el *audio*, y lo oyes.

Deliberadamente no es Discord. Discord ya existe, funciona y todo el mundo está ya
en uno. Lo que Discord no puede hacer es meterte en una sala con **quien esté en
esta sesión**, sin haberlo organizado antes, y callar a los que están a cuatro
kilómetros.

## Qué viaja

**El clip de pulsar-para-hablar, al soltar. No una transmisión en directo.**

El ciclo del disparador ya graba un clip mientras se mantiene la tecla y se lo pasa
a Whisper al soltar. La voz reutiliza exactamente ese clip: al soltar va a Whisper *y*
al relé, y los demás lo reproducen. Nada de la ruta de grabación cambia.

Una transmisión en directo sería otra aplicación. Necesita tramas de 20 ms, un búfer
de fluctuación, un mezclador y un reloj de reproducción, todo en la ruta de audio, y
el premio es que la gente te oye 1,5 segundos antes. El clip es lo que una radio de
boxes es de todos modos: mantienes el botón, dices una cosa, llega.

La consecuencia que conviene conocer: **un clip es atómico.** No se puede
interrumpir, llega entero o no llega, y dos personas hablando a la vez producen dos
clips que hacen cola en lugar de pisarse. Eso es mejor que una carrera, no peor.

## Quién lo oye

El relé es tonto. Reparte un clip a todos los de la sala y no decide quién debería
recibirlo, porque no puede: no tiene ni idea de dónde está nadie en la pista, y darle
esa información sería peor que inútil.

**La proximidad se decide en la máquina del oyente.** La memoria compartida de LMU
lleva la posición mundial de *cada* coche, no solo el tuyo, así que cada cliente ya
sabe exactamente a qué distancia está cada otro piloto. Nada posicional se publica
nunca al relé, y la función funciona incluso si quien opera el relé es hostil.

**Gana la visión que el oyente tiene de dónde está quien habla.** Un clip llega
después de que su emisor dejara de hablar, así que la posición que lleva tiene un
segundo o dos — a ritmo de carrera, cien metros, lo que frente a un radio de 200 m
decide la respuesta. El bloque de clasificación tiene cada coche tal como está
*ahora*, y la pregunta es quién está cerca del coche objetivo cuando suena el
mensaje.

El clip lleva de todos modos la posición del emisor, como recurso para alguien a
quien el bloque del oyente no ha alcanzado: un piloto que acaba de entrar, o cuya
entrada ha desaparecido. Una posición vieja es mejor que ninguna.

Preferir la vista local también significa que un clip no puede colarse por el filtro
hablando. Un cliente que afirma estar a tu lado cuando está a un kilómetro se mide
sencillamente donde está de verdad. Eso es consecuencia de usar el número más fresco,
no un mecanismo de seguridad: alguien a quien no se puede situar en absoluto sigue
siendo audible, porque un silencio que nadie puede explicar es el peor fallo.

`proximity_only` en el plugin de LMU lo activa; `proximity_metres` fija el radio.
Apagado oyes toda la sesión, que es lo que quieres en entrenamientos y en una vuelta
de formación.

### Espectar

La proximidad debería medirse desde el coche que hay en pantalla: seguir una pelea en
mitad de la cual estás, mientras oyes la radio desde cuatro kilómetros más allá donde
tu propio coche está aparcado, no es proximidad en ningún sentido que un espectador
reconocería.

Tiene que **detectarse**. Quien está corriendo no puede llegar a un desplegable, y
quien espectra no debería tener que hacerlo.

**El bloque de memoria compartida no lo dice**, y se comprobaron tres fuentes
plausibles contra una sesión espectada en vivo y se descartaron: cada una parece la
correcta y ninguna lo es.

- `telemetry.playerVehicleIdx` es el vehículo del *jugador*. Mientras se espectaba a
  otro, seguía apuntando al coche aparcado del que miraba.
- `appInfo.mOptionsLocation` marcó 0 todo el rato.
- `$rFactor2SMMP_Graphics$` se publica y llevaría tanto una posición de cámara como
  el id de la plaza observada, pero LMU nunca lo rellena. El búfer es enteramente
  ceros salvo su contador de versión, porque el juego no llama a la retrollamada de
  gráficos de la que el plugin de rF2 lo rellena. El bloque Extended vecino estaba
  vivo en ese mismo momento, así que es una decisión de LMU y no una instalación
  rota.

**La propia API HTTP de LMU sí lo dice.**
`http://127.0.0.1:6397/rest/watch/standings` es lo que leen los overlays del propio
juego, y cada entrada lleva `hasFocus`, marcado en el coche que se está viendo y
distinto de `player`, que se queda en el tuyo. Su `slotID` es el mismo número que
`mID` en la memoria compartida, así que los dos se unen directamente. Forma parte del
juego y no de ningún plugin, así que no necesita instalar nada.

Se lee con un tiempo de espera corto y se cachea un segundo: esto corre en el ciclo
del disparador, la respuesta ronda los 16 KB, y una aplicación de dictado nunca debe
esperar a un juego que está a mitad de carga. **Los fallos también se cachean**; si
no, un juego cerrado cuesta un tiempo de espera en cada pulsación.

Todo fallo devuelve None, y `SessionInfo.listener()` recae entonces en el coche
conducido y finalmente en None, que `audible` lee como audible. Mantener en silencio
un coche aparcado como referencia filtraría la sesión por un lugar que nadie está
mirando, y ningún oyente podría distinguir eso de una función rota.

**«Proximidad» significa en la pista y en ningún otro sitio.** Son metros entre dos
coches en el juego, leídos del simulador, calculados localmente. No tiene nada que ver
con dónde vive nadie, y no se lee, deriva ni transmite ninguna ubicación física. El
*alojamiento* de relés, más abajo, también habla de distancia, en sentido de red: eso
es una cuestión de enrutado sobre servidores y no guarda relación con a quién puedes
oír.

## Qué sala

El id de sesión se deriva, nunca se anuncia:

    sha256("pitradio/1:{mServerPublicIP}:{mServerPort}")[:32]

Todos los del mismo servidor de juego calculan el mismo id sin que nadie publique cuál
es ese servidor: el relé aprende un hash y nada más. Sin conexión y un jugador no
tienen servidor, así que no producen id ni sala, que es el comportamiento correcto y no
un caso especial.

El circuito está deliberadamente *fuera* de la clave. Cambia entre sesiones en el
mismo servidor, y una sala que se disuelve cuando el evento pasa al siguiente trazado
es una sala peor.

La identidad dentro de una sala es el nombre del piloto del bloque de clasificación.
`mSteamID` es cero en la práctica, así que no hay nada mejor disponible.

## El relé

**El código y la configuración del relé no están en este repositorio.** SimPitRadio es
público; el servidor, su Terraform y su Ansible son privados, junto con el secreto de
cliente OAuth que necesitan. Terraform y Ansible existen allí para un trabajo: levantar
de forma reproducible, desde una imagen limpia, un host de voz **aportado por un
piloto**.

La dirección del relé base tampoco está en este repositorio. Se escribe en
[endpoints.py](../src/pitradio/endpoints.py) **en tiempo de compilación**, así que una
copia del código —o un fork— no tiene dirección ninguna y la voz sencillamente no está
disponible. Ese es un estado que funciona, no uno roto: mejor que cada clon del código
apuntando un micrófono a un servidor cuyo dueño nunca aceptó soportarlo.

Nada más en la aplicación puede fijar una dirección en el código. Un sitio que
sobrescribir, un sitio donde mirar cuando está mal.

    wss://<relé>/chat/{id-de-sesión}

Un WebSocket por cliente, TLS, clips como tramas binarias con una cabecera pequeña. Ese
es todo el protocolo. TLS porque un relé es la máquina de un desconocido y el audio de
tu voz no debería cruzarla en claro; WebSocket porque sobrevive a todo NAT y cortafuegos
corporativo que el UDP en crudo no, y el ancho de banda de audio para veinte pilotos que
pulsan un botón de vez en cuando no es nada.

**No es literalmente peer-to-peer.** El P2P de verdad necesita ICE, STUN y un repliegue
a TURN — y TURN es un relé, así que la ruta de repliegue es este diseño de todos modos,
alcanzada tras meter una pila WebRTC en una compilación de Nuitka que ya pelea con
dependencias nativas. El relé es una caja pequeña y es honesto al respecto.

### Hosts de la comunidad

Los relés existen para estar *cerca de quien habla*. Una parrilla sacada de tres
continentes enrutada por una caja en Fráncfort paga el Atlántico dos veces en cada clip;
un relé elegido para el grupo no. Esa es toda la razón por la que los pilotos pueden
alojar: no el coste, ni la descentralización por sí misma, sino la geografía.

Terraform hace la máquina; Ansible instala el relé, la unidad de systemd y el
certificado TLS, así que un host es reproducible desde una imagen limpia de Ubuntu sin
pasos manuales.

Primero OAuth de DigitalOcean, porque es lo que hay hoy. Linode tiene un flujo real de
aplicación OAuth y puede seguir. **AWS no puede**: no tiene OAuth de consumidor para
aprovisionar —son claves IAM o SSO de Identity Center—, así que necesita su propio
camino y no es cuestión de añadir un botón.

#### Elegir uno es una decisión de grupo, no personal

**Todos los clientes de una sesión deben elegir el mismo relé, o no eligen ninguno.**
Dejados a su aire, cada uno elegiría el host más cercano a *sí mismo*, lo que para una
parrilla transatlántica significa dos relés, dos salas y las dos mitades de la sesión
sentadas en algo que parece exactamente una función que funciona pero sin nadie más
dentro. Es el mismo fallo silencioso que una clave de sesión que no coincide, alcanzado
por otro camino.

Así que hay un coordinador, en el host base fijo, y decide:

1. Los clientes entran en la sala en el relé configurado de la compilación e informan
   de su ida y vuelta medida a cada relé candidato.
2. El coordinador elige el que tiene el mejor peor caso de toda la sala: minimiza la
   latencia del piloto *más lento*, no la media, porque de lo que se trata es de que
   nadie quede varado.
3. Les dice a todos que migren, y se reconectan allí juntos.

El host base es también el relé de repliegue, y eso es lo que lo hace asequible: el
coordinador tiene que estar siempre encendido de todas formas, así que bien puede llevar
el audio de las sesiones demasiado pequeñas o demasiado locales como para que valga la
pena moverlas.

#### Por qué no unir todos los hosts entre sí

La alternativa obvia: dejar que cada cliente se conecte al relé que le quede más cerca
*a él*, y que los relés se reenvíen los clips entre ellos. Es un diseño real —Mumble
enlaza servidores así— y es genuinamente más elegante en un aspecto, porque borra la
decisión de grupo de arriba. No hay nada que acordar si la sala abarca todos los relés,
así que el fallo de la sala partida no puede darse siquiera.

Aun así es el trato equivocado aquí, por una razón: **enviamos clips, no una transmisión
en directo.** Un clip se despacha después de que el emisor haya dejado de hablar, así
que la diferencia entre 90 ms y 250 ms de enrutado no es algo que nadie pueda percibir,
y eso es la mayor parte del argumento a favor de la geografía y todo el argumento para
pagar dos saltos extra por mejorarla.

Lo que cuesta el puenteo no son saltos, es estado. Los relés tendrían que cotillear la
pertenencia a salas, autenticarse entre sí y protegerse de bucles y entregas duplicadas,
y un relé alojado por un piloto que se una a ese tejido puede ver tráfico de salas en
las que no tiene miembros. Eso es un proyecto de sistemas distribuidos atornillado al
costado de una aplicación de dictado, al servicio de un presupuesto de latencia que este
diseño no tiene.

Si SimPitRadio llega alguna vez a la transmisión en directo, esto se invierte y el
puenteo pasa a ser la respuesta correcta. La forma a construir entonces: una malla
completa con un secreto compartido, la pertenencia a salas difundida por cotilleo, y cada
clip llevando un id con un límite de **un salto** entre relés: sin reenvío transitivo, lo
que mata los bucles de enrutado de raíz y acota el reparto en vez de fiarse de él.

#### Cuando un host desaparece

Un relé que desaparece no debe terminar la conversación. El coordinador conserva la sala,
nota que el relé deja de responder, vuelve a ejecutar la elección sobre lo que queda y
migra a los pilotos restantes: el mismo mecanismo que la elección inicial, así que no hay
una ruta de conmutación por error aparte que se pueda equivocar. Los clientes mantienen
abierta la conexión con el coordinador exactamente por eso: es lo que sobrevive.

Un piloto que abandona la sesión no se lleva su relé a mitad de carrera. Su máquina no es
el relé —lo es un droplet que aprovisionó— y quitárselo de debajo a quienes siguen
conduciendo sería el peor momento posible para hacerlo.

#### Cuando la sesión termina

Las salas se desmontan, no se dejan corriendo. LMU informa de su fase de juego, así que un
cliente que ve terminar la sesión lo dice; cuando el último cliente se va, o la sala queda
en silencio más allá de un tiempo de inactividad, el coordinador la cierra. Un relé sin
salas es candidato a `terraform destroy`, y esa es la diferencia entre que esto le cueste
a un piloto unos céntimos por evento o le cueste un droplet para siempre.

El tiempo de inactividad importa tanto como la señal explícita. Un cliente que se cuelga,
se va a otra ventana para siempre o pierde la red no envía nada nunca, así que nada puede
depender de que lo haga.

## Consentimiento

La voz está **apagada hasta que se enciende**, por perfil, y la ventana dice quién puede
oírte antes de decir cualquier otra cosa. Una aplicación de dictado que abriera en
silencio el micrófono a veinte desconocidos sería una traición, por buena que fuera la
función.

Solo pulsar para hablar. No hay modo de micrófono abierto y no debería haberlo: la tecla
es el consentimiento.
