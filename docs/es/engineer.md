# El ingeniero

Una voz con nombre que observa el simulador y te habla: tus tiempos por vuelta,
coches al costado y respuestas cuando le preguntas algo.

Comparte el disparador con todo lo demás que hace SimPitRadio. Mantén el
disparador, di «Chief, focus on P3», suelta. Eso va al ingeniero en vez de al
chat, y el ingeniero responde.

**Está apagado hasta que lo enciendes.** No se dice nada hasta que hayas ido a
Ajustes → Ingeniero y marcado la casilla.

---

## Inicio rápido

1. Abre **Ajustes → Ingeniero** y marca **Ingeniero activo**.
2. Elige uno de los cuatro ingenieros. Eso fija su nombre, su voz y cuánto habla.
3. Pulsa **Probar**. Deberías oírle decir su nombre.
4. Pon el **Dispositivo de salida** en tus auriculares. Usa el mismo que llevas
   para el chat de voz y no la salida del simulador.
5. Conduce. Te leerá el tiempo por vuelta en la línea.
6. Mantén el disparador y di **«Chief, focus on P3»** para medirte contra quien
   vaya tercero.

Si Probar no dice nada, ver [No se habla](#no-se-habla) al final.

---

## Hablar con él

Dos maneras de que una frase se convierta en orden, y las dos son
deliberadamente estrechas. La misma tecla manda mensajes a todos los de tu
sesión, así que una orden que el ingeniero *se invente* es un mensaje que en
silencio nunca llega.

**Di primero su nombre.** «Chief, focus on P3.» El nombre va delante, la
expresión justo detrás. Se permiten `hey`, `ok` y `right` delante del nombre.

**O di una expresión sola**, siempre que tenga dos palabras y no lleve piloto.
«coach me» funciona sin nada delante. «study» es una sola palabra, podría
abrir una frase corriente y todo lo que va después de ella es el nombre del
piloto, así que necesita primero el nombre del ingeniero. Dicho a secas, *study
P2* fue al chat ocho veces en una sesión, resuelto como una mención a un piloto
y enviado a todo el mundo.

Decir solo el nombre te da «go ahead», como haría una radio de verdad, y
mantiene un *Chief* suelto fuera de un mensaje a otras veinte personas.

**«stop»** funciona siempre, sea lo que sea que esté en marcha y sea lo que sea
que lo arrancó. También «stand down», «cancel», «that's enough» y «forget it».

Todo lo que el ingeniero no reconozca es un mensaje, y va al chat exactamente
como antes.

---

## Elegir ingeniero

Cuatro vienen con la aplicación:

| | Voz | Estilo |
| --- | --- | --- |
| **Chief** | masculina | Firme y completo. «Turn four, Tandy was faster on the exit, two tenths.» |
| **Ada** | femenina | Escueta. Se salta el número de curva: «Tandy, faster exit, two tenths.» |
| **Marshall** | masculina | Más lento y más lleno, si los otros te parecen acelerados. |
| **Vic** | femenina | Rápida y corta. La que menos habla de los cuatro. |

Cada uno es un preajuste: un nombre, una voz de Windows preferida, un ritmo y
cuánto dice. Ninguno es una grabación. Un pack de voz generado ocupa uno o dos
gigabytes, así que cuatro conjuntos de audio serían una descarga de ocho
gigabytes para sustituir algo que ya está gratis en cualquier máquina con
Windows.

Cada uno elige la mejor voz de Windows instalada que encaje con su preferencia
y tu idioma. Una instalación normal de Windows 11 suele tener dos o tres, así
que dos ingenieros pueden compartir voz y diferenciarse por ritmo y forma de
decir las cosas. Pon **Voz de Windows** para anular el preajuste.

**Se le llama** es a lo que responde. Ponle lo que quieras. El nombre solo se
usa para dirigirse a él, y «Bob, focus on P3» funciona igual de bien.

---

## Qué te cuenta

### Tiempos por vuelta

Lee tu vuelta al cruzar la línea y dice cuándo ha sido tu mejor. Activado por
defecto.

### Spotter

Avisa de coches al costado: «car left», «car right», «in the middle» con uno a
cada lado, y luego «clear» cuando se han ido. Apagado por defecto, y hay una
cosa que conviene saber.

**Cuál lado es cuál no se pudo verificar sin un coche en pista.** Las
posiciones salen de las coordenadas del mundo del propio simulador, y que las
cuentas den izquierda o derecha depende de un convenio de mano que este
proyecto no pudo comprobar desde una máquina de desarrollo. Si canta a la
izquierda un coche que está a tu derecha, activa **Intercambiar lados del
spotter** en Perfiles, bajo los ajustes del plugin de sesión del juego. Es una
marca, una vez.

Todo lo demás del spotter es exacto. Usa posiciones del juego, descarta la
altura, así que un puente o las eses de Le Mans no te ponen a alguien en la
puerta, y no canta coches en una recta contigua.

### Daños

Dice qué se ha roto y si hay que entrar por ello. Activado por defecto, y
necesita un simulador que publique el estado del coche. Hoy es Le Mans
Ultimate.

> *Has perdido carrocería. Boxes esta vuelta.*

**Habla en el momento en que el coche empeora, y luego se calla.** Quien lleva
media hora con la trasera izquierda abollada no necesita que se lo recuerden
cada vuelta. Se vigila cada parte de la lectura en vez de solo la peor, así que
que se caiga una segunda cosa de un coche ya abollado es noticia aunque la
gravedad no se haya movido.

**Lo que dice es dónde, y luego si.** Ya sabes que has golpeado algo. Lo que no
ves desde el asiento es cuán grave es y si hay tiempo para arreglarlo, así que
nombra el sitio: el morro, la cola, todo el lado izquierdo. Luego da una de
tres respuestas.

| | |
| --- | --- |
| **Boxes esta vuelta** | el coche no se puede correr, solo traer con cuidado: una pieza colgando, un pinchazo, una rueda perdida o un morro roto. El tiempo que quede no cambia esto: la alternativa es bandera negra o muro |
| **Boxes cuando puedas** | vale la pena arreglarlo. Siempre en entrenamientos y clasificación, donde una parada no cuesta nada y el sentido de estar fuera es tener un coche que funcione |
| **Sigue fuera, lo aguantamos** | una carrera a la que le queda menos de una quinta parte. A tres vueltas del final te conviene más llevar un coche tocado hasta la bandera que devolver un minuto |

Los daños leves reciben la primera mitad y ningún consejo. Que te hagan sopesar
una parada por un cuarto trasero rozado es peor que no decirte nada.

Nunca habla por encima del entrenador. Los daños son urgentes, y quieres saber
que el alerón se ha ido antes de la siguiente curva y no después. Una crítica
que has pedido sigue sin merecer que se corte por un coche que va a quedar
igual de roto dentro de cuatro segundos. El spotter es el único aviso que
habla por encima de cualquier cosa.

---

## A quién vigila

El ingeniero mantiene un **foco**: un piloto contra el que te mide. No hace
falta que lo pongas. Por defecto es **el coche que va delante en tu clase**, o
el de detrás cuando la lideras. Ahí no hay nadie delante a quien perseguir, y
la pregunta ha pasado a ser si los mantienes detrás.

Solo sigue un cambio cuando la posición se ha **mantenido ocho segundos**. Las
posiciones se agitan. Medido en una salida de carrera real, quince pilotos
distintos fueron el coche de delante en noventa segundos, cada cambio tiraba
las vueltas que el observador había reunido, y nunca tenía suficiente para
decir nada en absoluto.

Dilo si quieres a otro:

- `focus on {piloto}`, o «keep an eye on», «keep tabs on», «study», «watch»
- `default focus`, vuelta a elegir por su cuenta
- `stop focusing`, apagado hasta que se lo pidas

Un piloto que nombras nunca se anula. Volver dos curvas después a quien vaya
delante es la aplicación llevándote la contraria.

La pestaña Estado muestra a quién se vigila, y `what are we watching` lo
pregunta.

---

## Preguntarle cosas

Cada pregunta tiene una caja de expresiones en Ajustes → Ingeniero, una por
línea, y lo que escribas sustituye a las de fábrica. Cada una se puede apagar.
Una pregunta apagada no aporta ninguna expresión, así que sus palabras llegan
al chat como cualquier otra en vez de ser tomadas y respondidas con nada.

- **Tu coche**: `what's my best lap`, `how are the tyres`, `what's the damage`,
  `how's the fuel`, `how much fuel do I need to finish the race when I pit on
  the next lap`
- **La sesión**: `who has the fastest lap`, `who's fastest`,
  `who has the fastest sector`, `who's in the lead`, `who's ahead`
- **Dónde se va el tiempo**: `where am I slower`, `where am I faster`,
  cualquiera de las dos con `than {piloto}` al final

**Las preguntas se saltan la cola.** Una pregunta hecha mientras el ingeniero
estaba a media frase antes esperaba detrás o se descartaba directamente, porque
la cola guarda seis y una vuelta ajetreada la llena. Preguntabas, le oías
hablar de otra cosa y no obtenías respuesta. Ahora una respuesta despeja el
tráfico ordinario, corta lo que se está diciendo y no puede ser expulsada.
Sigue cediendo ante el spotter, porque un coche al lado va de no chocar.

**Una pregunta que no puede responder se queda fuera del chat.** *Who's
faster?* no es una expresión que conozca, y antes se colaba y salía a la
sesión. Cualquier cosa que se lea como pregunta, por acabar en interrogación o
por abrir con un interrogativo, se responde con «say again». Hay una casilla en
la pestaña Chat de texto si prefieres el comportamiento antiguo. Una pregunta
que has apagado expresamente sí llega al chat, porque apagarla es tu manera de
decir que esas palabras son tuyas.

Puedes poner el nombre del ingeniero en cualquiera de los dos extremos: «Bono,
how are the tyres» y «how are the tyres, Bono» funcionan igual. La coma es lo
que lo marca como nombre, así que `focus on Bono` sigue enfocando a un piloto
llamado Bono.

### Dónde soy más lento

La que merece conocerse. Te compara con tu foco **curva a curva, promediando
cada vuelta de esta sesión** en vez de leerlo de una sola. Una vuelta suelta
dice lo que pasó en esa vuelta, y la pregunta va de lo que sigue pasando.

> Chief, where am I slower
>
> *Curva tres, eres más lento en entrada, dos décimas.*
>
> *Curva siete, tienen mejor salida, una décima.*

Dice *cómo* además de dónde: entrada, salida, frenar más tarde o ser más lento
en toda la curva. Donde existe un catálogo para el circuito usa el nombre,
*Eau Rouge* en vez de *curva tres*.

**Cómo encuentra las curvas.** No hay mapa del trazado y no lo va a haber. Un
mapa necesitaría un archivo por circuito, se quedaría viejo con cada cambio de
trazado y funcionaría en los cuatro circuitos a los que alguien le hubiera
dado tiempo. Una curva es un sitio donde la vuelta de referencia frenó y volvió
a acelerar, y eso es cierto en cualquier circuito de cualquier simulador. Las
chicanes cuentan como una curva.

**Describe lo que midió.** *Tienen mejor salida* es lo que la aplicación sabe.
No tiene forma de saber si fue trazada, neumáticos o rebufo, y *frena más
tarde* sería una conjetura vestida de entrenamiento.

**Si faltan vueltas dice de quién.** Tuyas o suyas, porque «no hay vueltas que
comparar» por sí solo te deja adivinando cuáles.

### Lo que no usará como referencia

- Una vuelta con cualquier parte en el pit lane. Una vuelta rápida que en
  realidad fue un atajo por boxes se convertiría en el objetivo contra el que
  se mide todo el mundo, y nada en ella parecería mal.
- Una vuelta a la que te incorporaste a medias.
- Una vuelta a la que el simulador no dio tiempo, como una vuelta de salida o
  un coche recién llegado.
- Cualquier cosa de otro circuito. Cambiar de trazado lo borra todo.

También se calla mientras espectas. Comentar una vuelta que estás mirando en
vez de conduciendo no tendría sentido.

---

## Cuando tu simulador no puede responder

Los simuladores publican cosas distintas, y el ingeniero lo dice en vez de
adivinar. El Assetto Corsa original publica **tu propio coche y nada de nadie
más**: ni nombre, ni posición, ni tiempo de otro piloto. Cualquier cosa que te
compare con la parrilla no tiene datos ahí por ninguna vía.

Pregunta «who's leading» y responde **«este juego no lo dice»**. Es una
respuesta distinta de «no hay a quién vigilar», que significa que la parrilla
está de verdad vacía. Decirle a un piloto que va séptimo que no tiene a nadie
delante es decirle algo falso.

Los comportamientos que necesitan datos que tu simulador no da se omiten con
una línea en el registro en vez de dejarse encendidos y mudos:

```
Spotter is on but this sim does not publish positions or spotter; it will stay quiet
```

`--telemetry` imprime lo que tu simulador está mandando de verdad. Ver la
última sección.

---

## Otros idiomas

El ingeniero habla el idioma que tengas puesto para la **transcripción**, salvo
que lo fijes en la pestaña Ingeniero. Tus órdenes llegan a través de Whisper,
así que un ingeniero que escucha expresiones en inglés mientras Whisper
produce español no oirá ni una.

Todo lo que dice pasa por los mismos catálogos de traducción que la ventana, y
también las expresiones que escucha. Añadir un idioma es un archivo JSON en
`src/pitradio/locale/`; ver el README principal.

**Los números se escriben con letra en inglés y se leen como dígitos en todo lo
demás.** La gramática de los números es propia de cada idioma. El alemán
invierte decenas y unidades, el español funde los veinte, y una implementación
a medias produciría disparates dichos con seguridad en el idioma de alguien.
Los dígitos le pasan el problema a la voz de ese idioma, que ya lo resuelve.
Una consecuencia: un pack de voz no inglés no puede cubrir los números, y
salen sintetizados.

---

## Packs de voz

**De qué pack habla este ingeniero se ajusta aquí, en la pestaña Ingeniero**, y
el entrenador elige el suyo en la pestaña Entrenamiento. Son trabajos
distintos, y un piloto puede querer razonablemente oír cuál de los dos está
hablando.

**Instalar, grabar y quitar packs es Ajustes → Voz.** Un pack es algo que
guarda la aplicación. De cuál habla una voz es un ajuste de esa voz.

Vienen dos packs, **Norman** y **Claudia**, los dos generados con Piper. Ver
[voicepacks.md](voicepacks.md). Cualquiera puede sustituirse por uno tuyo.

Un pack de voz pone audio grabado en lugar de la voz de Windows: una carpeta
de archivos WAV, una carpeta por frase, varias tomas cada una. El ingeniero
elige una toma al azar, que es la mayor parte de por qué un pack suena a
persona.

**La disposición es la de Crew Chief**, a propósito:

```
%APPDATA%\pitradio\voices\
  Ada\
    voice\
      corners\
        two_tenths\
          a.wav
          b.wav
```

Una disposición plana `<pack>/<frase>/*.wav` también vale, y es lo que sale de
grabar tú mismo.

Así que un pack generado por
[crew-chief-autovoicepack](https://github.com/cktlco/crew-chief-autovoicepack)
puede entrar directamente. Para generar uno con las frases de SimPitRadio en
vez de las de Crew Chief:

1. Ajustes → **Voz** → **Escribir lista de frases**. Escribe
   `phrase_inventory.csv` en la carpeta de voces, en el idioma del ingeniero.
2. Dale ese inventario al generador en lugar del suyo.
3. Pon la carpeta de salida bajo `voices\` y elígela en la pestaña Ingeniero (o
   usa **Ajustes → Voz → Abrir carpeta de packs de voz** para llegar).

**Los nombres y los números nunca están en un pack** y siempre los dice la voz
de Windows. Ningún pack puede contener todos los nombres de pilotos ni todos
los tiempos por vuelta, así que un aviso como *curva cuatro, Tandy fue más
rápido a la salida* es en parte grabado y en parte sintetizado. Esa costura se
oye. Sigue siendo el trato correcto, porque la alternativa es un pack que
queda sin usar en cuanto se nombra a un piloto, que es la mayoría de los
avisos.

Los packs se guardan junto a tu configuración en vez de en el directorio de
instalación, para que una actualización no borre un gigabyte de audio que
decidiste instalar.

---

## Cómo encaja todo

El ingeniero corre en **su propio hilo**, aparte de los cuatro que SimPitRadio
ya tiene, y hablar recibe un hilo por debajo. Ninguno puede retener el hook de
teclado, el trabajador ni la ventana.

Todo lo que hace puede fallar. Que el ingeniero se calle nunca debe costarte un
disparo, una transcripción ni un mensaje en el chat. Si algo aquí dentro se
rompe, las palabras van al chat como siempre y el problema es una línea en el
registro.

Lee el simulador diez veces por segundo mediante el mismo plugin que suministra
nombres de pilotos para las menciones. No hay una segunda ruta de datos ni una
conexión extra al juego.

---

## No se habla

**Probar no hace nada.** El sintetizador corre en un host de PowerShell usando
`System.Speech`, que forma parte del .NET Framework en cualquier máquina con
Windows 10 y 11. Busca `no speech host` en el registro. Una máquina restringida
con PowerShell bloqueado es la causa habitual.

**Lo oyes, pero no en los auriculares.** Ajusta el dispositivo de salida en la
pestaña Audio. Por defecto es el del sistema, que durante una carrera suele ser
el altavoz del volante.

**Lee tiempos por vuelta y nunca entrena.** El entrenador necesita una vuelta
de referencia, y hasta que tu foco haya completado una limpia, sin ninguna
parte en el pit lane, no hay nada contra qué comparar.

**Entrena y no dice nada en algunas curvas.** Esas curvas cuestan menos tiempo
que el umbral, que es el diseño. `engineer.coach_threshold`, en `config.json`,
es cuánto tiempo en media curva merece la pena interrumpir por él, en
segundos. Bájalo para más avisos. No hay control para esto en la ventana.

**No responde a nada de lo que dices.** Comprueba el nombre en la pestaña
Ingeniero, y recuerda que cualquier expresión que lleve piloto necesita el
nombre delante. Di *Chief* a secas. Si te contesta «go ahead», está escuchando
y el problema es la expresión.

**Se ha comido un mensaje.** No debería. Si el ingeniero tomó algo que querías
enviar, la línea del registro dice `that was for the engineer` junto con lo que
coincidió. Por favor, abre una incidencia con esa línea: que el emparejador sea
demasiado ansioso es el único fallo de esta función que cuesta algo real.

---

## Comprobar qué está mandando de verdad tu simulador

La mayoría de las veces que el ingeniero no dice nada, el ingeniero no es el
problema. Arranca el juego, ponte **en pista y en movimiento**, y entonces:

```bash
python -m pitradio --telemetry
```

Imprime cada coche tal como lo ve el ingeniero: distancia de vuelta, velocidad,
número de vuelta, sector, tiempos, bandera de boxes, posición en el mundo.
Luego compara lecturas consecutivas y te dice si algo está cambiando.

Esa segunda parte es la que hay que leer. Un simulador en pausa o parado en un
menú sigue publicando un bloque que parece perfectamente sano, con coches,
posiciones y velocidades plausibles. Nada se mueve, así que el ingeniero no
tiene nada que decir, y ninguna instantánea suelta lo muestra. Si informa

> Nothing changed across 4 reads, including the sim's own clock.

entonces el juego está en pausa, en un menú, o la sesión ha terminado. No está
roto.

Qué mirar cuando *sí* está vivo:

| Columna | Alimenta |
| --- | --- |
| `lapdist`, `speed` | detección de curvas, y dónde se va el tiempo |
| `lap`, `last lap`, `best lap` | avisos de tiempo por vuelta y vuelta rápida |
| `sec` — cambia tres veces por vuelta | todos los avisos de sector |
| `world x/y/z` — distinto por coche | el spotter |

La línea `provides:` de arriba dice cuáles de esos afirma suministrar el
plugin de sesión. Un comportamiento que necesita algo ausente se omite en vez
de quedarse encendido y mudo, y el registro nombra qué falta.

## Qué puede hacer cada simulador

Los simuladores publican cosas muy distintas, y un comportamiento cuyos datos
faltan se **omite con una línea en el registro** en vez de quedarse encendido y
mudo.

| | Le Mans Ultimate | iRacing | Assetto Corsa / Competizione / Evo | Automobilista 2, Project CARS 2 / 3 |
| --- | --- | --- | --- | --- |
| Tiempos por vuelta | sí | sí | sí | derivados |
| Nueva vuelta rápida | sí | sí | — | sí |
| Avisos de sector | sí | — | sí | — |
| Dónde soy más lento | cualquier piloto | cualquier piloto | tu propia mejor | cualquier piloto |
| Quién va delante / lidera | sí | sí | — | sí |
| Spotter | geometría | el aviso del propio simulador | solo Competizione | geometría |
| Menciones de pilotos, «P3» | sí | sí | — | sí |
| Daños | sí | — | — | — |
| Entrenamiento y diagrama de segmento | sí | — | — | — |

Cada hueco de esa tabla es del juego:

- **iRacing** no publica parciales por coche, así que los avisos de sector no
  tienen con qué trabajar. Su spotter es el mejor de todos: `CarLeftRight`
  viene de las carrocerías reales, así que no necesita ajuste de intercambio
  ni estimación de anchura.
- **Assetto Corsa** publica tiempos solo de tu coche y ningún nombre de
  piloto. Ahí no hay clasificación ni menciones, y «dónde soy más lento»
  persigue tu propia mejor vuelta, que es para lo que sirve una sesión de
  entrenamiento de todos modos.

  El juego original va más allá y publica **ningún otro coche en absoluto**,
  ni siquiera la posición. Comprobado contra una carrera real de ocho coches,
  el array de coordenadas tenía al jugador en la ranura cero y memoria intacta
  en todas las demás: ceros, un NaN, un denormal. El spotter tampoco tiene ahí
  con qué trabajar. El plugin de sesión decide esto por sesión y no por juego,
  porque **Competizione sí** publica el array, y el mismo plugin informa de
  posiciones para él.
- **Automobilista 2 y Project CARS** llevan *cuentas* de vueltas en vez de
  tiempos en la parte de su bloque en la que se puede confiar, así que los
  tiempos se miden aquí con cronómetro. Una vuelta que abarca una pausa sale
  más larga de lo que fue, lo que falla de forma segura: una vuelta inflada
  nunca llega a ser la referencia que persigue una comparación. Su campo de
  sector es un enum que no se pudo fijar desde fuera de los juegos, así que no
  se ofrecen avisos de sector.

Automobilista 2 tiene su propia entrada en vez de compartir la de Project
CARS, para que puedas elegir el juego que realmente estás corriendo y para que
los dos mantengan ajustes de spotter y proximidad separados.

**Le Mans Ultimate es el único verificado contra el juego en marcha.** Todos
los demás lectores están sin verificar: probados contra memoria compartida
construida a mano, lo que detecta un ancho de campo equivocado, un nombre mal
decodificado o un error de relleno, y no puede detectar una suposición
equivocada sobre qué pone el simulador y dónde. Ejecuta `--telemetry` con el
juego en pista antes de fiarte de cualquiera de ellos, y especialmente de
Assetto Corsa Evo, que sigue en acceso anticipado y puede mover su
disposición.

**iRacing está marcado como experimental**, y así aparece en el selector de
perfiles. El código no es peor que el resto. Nadie que trabaje en SimPitRadio
tiene una copia, así que es el único plugin de sesión que no se comprobará
contra lo real a menos que alguien que lo tenga ejecute `--telemetry` y cuente
qué salió. Si eres tú, hazlo por favor; la nota en la lista de plugins pide
exactamente eso.

## Ajustes por simulador

Tres de los números del ingeniero viven en el **perfil**, bajo los ajustes del
plugin de sesión del juego, porque describen el juego y no tu gusto:

- **Intercambiar lados del spotter**, para cuando un coche a tu derecha se
  canta a tu izquierda
- **Solape del spotter (metros)**: cuánta distancia a lo largo de la pista
  sigue contando como ir a la par. Un Hypercar mide unos 5 m
- **Anchura del spotter (metros)**: cuánto a los lados cuenta, antes de que
  simplemente estén en otra parte del circuito

Las longitudes de coche y los convenios de ejes difieren entre simuladores,
así que un número que va bien en un juego está mal en el siguiente.

## Banderas e incidentes

Un comportamiento propio, mantenido aparte del spotter a propósito. Las
propias carpetas de sonido de Crew Chief trazan la línea en el sitio correcto:
`car_left`, `still_there` y `clear_all_round` están en `spotter/`, mientras que
`stopped_car_in_turn_3`, `slow_car_ahead` y `local_yellow_ahead` están en
`flags/`. El spotter responde quién está a tu lado, que es geometría. Las
banderas responden qué le ha pasado a la pista, que es otra cosa.

Derivar lo segundo de lo primero producía un aviso en cada zona de frenada.
SimPitRadio tenía una regla que decía que un coche mucho más lento que tú era
un peligro, y una zona de frenada es precisamente donde el coche de delante es
mucho más lento que tú. Esa regla ya no está.

**Tres fuentes, no igual de fiables.**

*Amarilla en toda la pista* y *azul* vienen del simulador y son fiables. El
`mGamePhase`, el `mYellowFlagState` y el `mFlag` por coche de LMU se leen con
sensatez contra una sesión en vivo.

*Las amarillas locales se derivan*, porque el `mSectorFlag` de LMU no sirve.
Está documentado como «si hay amarillas locales en este momento en cada
sector» y lee `[11, 11, 1]` bajo bandera verde, con los campos de al lado
correctos. No es un desplazamiento que se haya movido. LMU sencillamente
publica otra cosa ahí. Leído como booleanos pondría una amarilla permanente en
todo el circuito. Así que un incidente aquí significa lo que un comisario
entiende por uno: un coche se ha parado en la carretera y lleva dos segundos
ahí. Es una derivación a partir de datos que el simulador sí publica con
honestidad, en el mismo espíritu que buscar las curvas en la traza de
velocidad en vez de enviar un mapa del trazado.

El coste es que el aviso no puede preceder al incidente. Una amarilla real
sale en cuanto los comisarios la ven, y esta espera a estar segura. El
beneficio es que nunca se equivoca sobre una pista verde, que es el fallo que
hace que la gente apague una función.

**Los incidentes se nombran por curva en vez de por piloto.** A la velocidad a
la que esto importa, *curva seis* es algo sobre lo que un piloto puede actuar
y un nombre es un recuento de sílabas que no se puede permitir. La numeración
es la del libro de vueltas, para que un piloto oiga un único juego de números
de curva en toda función. Las curvas se buscan una vez por vuelta de
referencia y se cachean, porque `find_corners` remuestrea una vuelta entera y
esto corre varias veces por segundo. Sin vuelta de referencia todavía, se
nombra el sector.

**Cuando el incidente eres tú, los avisos de costado paran.** Describirle a
quien ha trompeado los coches que le pasan es ruido. La única pregunta útil es
si hay hueco para salir, y `rejoin.py` la responde comparando *tiempo para
estar a salvo* contra *tiempo hasta que llega el siguiente coche*. Un coche
parado necesita recuperar toda su aceleración antes de la primera llegada, que
es por lo que una respuesta construida sobre tres segundos de pista libre hace
que a la gente se la lleven por delante.

Dos salvaguardas, ambas aprendidas y no supuestas. No se dice nada en el pit
lane, donde estar parado es el objetivo. Tampoco se dice nada antes de que el
coche se haya movido alguna vez: estar en la parrilla antes de las luces es
estar parado, en la trazada, con todo el pelotón detrás, que es exactamente lo
que mira el consejo de reincorporación.

Ver [voicepacks.md](voicepacks.md) para generar una voz.

## Preguntas

Los comportamientos y las preguntas son cosas distintas, y la diferencia se ve
en la pestaña. Un comportamiento es algo que el ingeniero *sigue haciendo*,
listado en [Qué te cuenta](#qué-te-cuenta), y lleva un intervalo de
repetición, porque un coche al costado deja de estar ahí sin que pase nada.
Una pregunta tiene una respuesta, y una vez dada no queda nada en marcha.
Modelar una como la otra pondría «who has the fastest lap» en la lista de
Comportamientos, donde cada entrada se repite. No existe eso de volver a
responder una pregunta cada 1,2 segundos.

Tres: la vuelta rápida, el sector rápido y tu propia mejor.

**El parámetro sigue a la palabra clave y nunca es parte de la expresión.**
Sobre qué puede preguntar un piloto depende del simulador en el que esté: las
clases de esta parrilla, los sectores que tiene este circuito. Nada de eso
pertenece a una expresión que alguien escribió en una caja de ajustes. «who
has the fastest sector» es la expresión, y *three in GT3* es lo que vino
después, analizado contra la sesión. Una clase se empareja mediante
`mentions.class_aliases`, así que el *LMGT3* de LMU responde a *GT3*
exactamente igual que en todas partes, y *LMP2* sigue negándose a responder a
*P2* porque eso es una posición.

**Un espacio de argumentos cerrado es la defensa contra falsos positivos**, y
supera a contar palabras. `phrases.MIN_BARE_WORDS` protege las órdenes
habladas exigiendo dos palabras delante de un parámetro abierto. Eso no basta
aquí: *who has the fastest lap of my life that one* lo supera fácilmente y se
tomaría como una pregunta sobre una clase llamada *of my life that one*,
comiéndose el mensaje. El argumento de una pregunta solo puede ser una clase
de esta parrilla, un sector entre uno y tres, o nada en absoluto. Cualquier
otra cosa nunca fue una pregunta, empezara como empezara. Dirigida por su
nombre lo es igualmente, porque quien dijo el nombre del ingeniero le estaba
hablando.

**Ninguna clase nombrada significa tu propia clase**, que es lo que quiere
decir alguien en un GT3 al preguntar «who has the fastest lap». Una clase
nombrada en la que no hay nadie recibe esa respuesta en vez de que se le dé
calladamente la cifra global. Una respuesta equivocada dicha con seguridad es
el fallo sin síntoma.

Cada una tiene una casilla en la pestaña Ingeniero y nada más. Sobre qué se
puede preguntar lo fija lo que publica el simulador, así que una caja de
expresiones editable ahí daría a entender que puedes inventarte una.

El interruptor se gana su sitio en otro sitio. **Cada expresión que el
ingeniero escucha es una expresión que puede sacarse de un mensaje destinado a
toda la sesión**, y quien nunca pregunta estas cosas no tiene motivo para
cargar con ese riesgo. Apagar una elimina sus expresiones del emparejador por
completo en vez de silenciarla después. Silenciarla después sacaría igual «who
has the fastest lap» del mensaje y luego respondería con nada, que es lo peor
de ambos mundos. Ausente de la configuración significa encendida, así que
añadir una pregunta nunca requiere una migración.

## El spotter, y de dónde salen sus números

Cada umbral de `spotter.py` es el de Crew Chief, leído de una instalación
local en vez de adivinado. Su `ui_text/en.txt` nombra cada ajuste y
`CrewChiefV4.exe.config` trae los valores por defecto:

| El nuestro | El de Crew Chief | Por defecto |
| --- | --- | --- |
| `DEFAULT_CAR_LENGTH` | `lmu_spotter_car_length` | 4,5 (5 para pcars2/ACC, 4,4 para AMS2) |
| `GAP_FOR_CLEAR` | `spotter_gap_for_clear` | 0,5 m |
| `OVERLAP_DELAY` | `spotter_overlap_delay` | 50 ms |
| `CLEAR_DELAY` | `spotter_clear_delay` | 150 ms |
| `MIN_SPEED` | `min_speed_for_spotter` | 10 m/s |
| `MAX_CLOSING_SPEED` | `max_closing_speed_for_spotter` | 12 m/s |
| el intervalo de repetición | `spotter_hold_repeat_frequency` | 3 s |

Tres de ellos faltaban aquí por completo y cada uno causaba un fallo que el
piloto podía notar:

**El límite de velocidad de aproximación es lo que caza al coche que dobla.**
Algo que llega 12 m/s más rápido cruza toda la ventana de solape en bastante
menos de un segundo, así que para cuando se ha dicho el aviso ya se ha ido, y
el piloto mantiene la línea por un coche que ya no está.

**La velocidad mínima es lo que frena el pit lane y la parrilla.** Por debajo
de 10 m/s los coches a tu alrededor están parados o pasan al paso, y cantar
eso es como acaba apagado un spotter.

**Los dos retardos de asentamiento son lo que corta la cháchara.** Dos coches
en la misma curva entran y salen del solape según respiran. Los retardos son
deliberadamente de distinta duración: el de solape es corto porque un aviso
tarde no vale nada, y el de despeje es más largo porque puede permitirse estar
seguro. Quien mantiene su línea una décima más de lo necesario no ha perdido
nada.

El rango de despeje es `longitud de coche + hueco`, no un segundo múltiplo de
la longitud. Esto importa en los extremos: para un kart, «otra longitud de
coche» son dos metros de histéresis y el aviso se alarga muchísimo, mientras
que medio metro de luz es medio metro conduzcas lo que conduzcas.

**El spotter calla bajo bandera amarilla en toda la pista**, que es el
`fcy_stop_spotter_immediately` de Crew Chief y está activado por defecto. El
pelotón va apiñado al paso y permanentemente solapado, así que cada aviso
sería cierto e inútil.

### Qué dice

El vocabulario es la carpeta `Sounds/voice/spotter/` de Crew Chief, así que un
pack de voz hecho para Crew Chief lo dice todo sin mapeo: `car_left`,
`car_right`, `still_there`, `hold_your_line`, `in_the_middle`, `clear_left`,
`clear_right`, `clear_all_round`, `three_wide_on_left`, `three_wide_on_right`.

Dos de ellos sustituyeron avisos que decían el mismo hecho por el camino
difícil:

* **«three wide you're on the right»** era *two cars left*. Quien oye el
  viejo tiene que deducir dónde le deja eso, y está ocupado. El nuevo dice
  directamente hacia qué lado no hay hueco.
* **«in the middle»** era *three wide*, para un coche a cada lado.

Una repetición dice `still there` en un lado y `hold your line` en ambos,
porque son instrucciones distintas: una significa no te muevas hacia ahí, la
otra significa no te muevas. La llegada y sus repeticiones comparten una clave
derivada de los *recuentos*, así que el intervalo de repetición las gobierna.
Una clave que cambiara con la redacción convertiría el seguimiento en un aviso
nuevo, debido en el siguiente tic.

**El juego de óvalo falta a propósito**: `car_inside`, `clear_outside`,
`three_wide_on_inside`. Cuál lado es el interior es un hecho sobre el peralte,
que ninguno de estos simuladores publica y que Crew Chief mantiene por
circuito. Adivinarlo es un aviso que está confiadamente del revés.

### Combustible

«how much fuel do I need to finish the race when I pit» toma la parada como su
argumento: *on the next lap*, o *in five laps*. **La respuesta es un
porcentaje**, porque ese es el número de la propia pantalla de combustible del
simulador y el piloto tiene unos cuatro segundos camino de la entrada a boxes
para marcarlo. Los litros son el desarrollo.

**El consumo se mide.** Lo que usa un coche depende del circuito, del mapa
motor, del tráfico y de cómo lo esté conduciendo la persona, así que los
litros por vuelta aquí son lo que *este* coche ha estado gastando en *estas*
vueltas. Es una media móvil corta, para que siga un cambio de mapa en vez de
quedar lastrada por un stint entero. Hasta que no se completa una vuelta no
hay respuesta y lo dice. Un número de combustible inventado de la nada es la
única respuesta equivocada aquí que termina la carrera de alguien.

Tres detalles que conviene anotar:

* **Las vueltas anteriores a la parada no se reponen.** Lo que hay ahora en el
  depósito las cubre. Solo las de después son la pregunta, y por eso esto
  nunca lee el nivel actual.
* **`mMaxLaps` es `INT_MAX` en una sesión a tiempo.** Tomado al pie de la
  letra pide combustible para dos mil millones de vueltas. `SessionInfo` lleva
  `max_laps` *o* `ends_at`, nunca ambos, y el plugin de sesión decide cuál. El
  ingeniero nunca adivina el que falta. Una carrera a tiempo divide el reloj
  restante entre la mejor vuelta del propio piloto y redondea **hacia
  arriba**, porque la bandera cae al final de la vuelta en la que estás cuando
  se acaba el tiempo.
* **Un llenado por encima de la capacidad del depósito se informa en vez de
  recortarse.** Significa que la parada no puede ser la última, y a un piloto
  al que se le dice que el depósito llega al cien por cien sin decírselo le
  planifica una carrera que no funciona.

Todo lo demás redondea hacia más combustible: quedarse sin es un abandono, y
llevar un litro de más es una décima por vuelta.

El combustible llega a `Car` **solo para el coche del jugador**, porque los
simuladores publican telemetría del depósito del coche que conduces y de
nadie más. Se adjunta emparejando `mID`, porque el array de telemetría de LMU
se indexa por `playerVehicleIdx` mientras que el de clasificación no.
Adjuntarlo por posición pondría tu depósito en el coche que casualmente
estuviera clasificado en esa ranura.

## Estar lejos del volante

El ingeniero no dice nada, y **no registra nada**, cuando el piloto no está
conduciendo. Tres estados, y necesitan tres señales distintas:

* **En pausa.** El reloj del simulador se detiene mientras el de esta máquina
  no, y la diferencia es la señal. El `mGamePhase` leía *bandera verde*
  durante toda una sesión en pausa en el garaje, con `mCurrentET` congelado en
  2218.0. La fase dice qué tipo de sesión es. No dice nada sobre si está
  corriendo.
* **En el garaje.** Aquí el reloj sigue corriendo, así que el reloj no puede
  ser la señal. `mInGarageStall` lo es. Cubre menos terreno que `in_pits`, que
  es todo el pit lane: un coche cumpliendo una parada está compitiendo.
* **Entregado a la IA.** `mControl` es 1, que es lo que parece espectar.

**Tampoco se observa nada.** Un simulador en pausa republica el mismo
fotograma para siempre, y darle eso al libro de vueltas registra un coche sin
avanzar durante todo el tiempo que alguien deje el juego ahí parado. Eso es
una vuelta de referencia corrupta en vez de una ausente. El estado del spotter
se descarta a la entrada por la misma razón: un coche que estaba al costado
antes de la pausa es un hecho sobre un momento que ya pasó.

**Pausar una carrera en línea no se detecta, y no puede detectarse.** Ahí el
reloj sigue corriendo, porque la carrera sigue corriendo. El menú está abierto
en esta máquina y los coches siguen dando vueltas. Nada en la memoria
compartida separa eso de correr con normalidad, e inventar una señal para
ello silenciaría al ingeniero durante una carrera de verdad, que es el peor
error de los dos.
