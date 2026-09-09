# Chat de texto

Aquello para lo que se construyó SimPitRadio. Mantén una tecla, di lo que quieras
decir, suéltala — y aparece en el chat del juego, escrito, sin que tus manos
dejen el volante.

Todo lo demás en la aplicación creció a partir de esto. El ingeniero, el
entrenador y el chat de voz comparten la misma tecla y la misma grabación; el
chat de texto es lo que ocurre con las palabras cuando nada más las ha
reclamado.

## Qué pasa mientras mantienes la tecla

1. **La tecla se traga.** El juego nunca ve el disparador, así que puede ser una
   tecla que el juego también use.
2. **La grabación empieza de inmediato**, antes de abrir el chat, no después.
   Abrirlo lleva unas centésimas y todo lo dicho durante ellas se perdería.
3. **Se disparan las teclas de chat** para abrir el chat del juego, y la
   aplicación espera `pre_delay_ms` a que tome el foco.
4. **Sueltas.** La grabación se detiene y el clip va a Whisper, en tu propia CPU.
5. **El texto se escribe** y luego se disparan las teclas de envío.

Si las palabras resultan ser una orden para el ingeniero o el entrenador, se
responden en su lugar y no se escribe nada. Esa decisión es deliberadamente
estrecha — ver [Hablar con él](engineer.md#hablar-con-él) — porque la misma tecla
manda mensajes a todos los de tu sesión, y una orden que la aplicación se invente
es un mensaje que en silencio nunca llega.

## Apagarlo

**Chat de texto → Enviar al juego** es el interruptor al que echar mano a mitad
de carrera cuando una sesión se vuelve pública. Apagado, el disparador queda solo
para la voz y el ingeniero: sin teclas de chat, sin escritura, sin nada enviado.

Hay un segundo interruptor por juego, en Perfiles. «¿Este juego tiene chat?» es
un hecho sobre el juego, no una decisión que tomes cada sesión — Assetto Corsa
sin conexión no tiene chat que abrir, así que cada pulsación mandaba al juego un
Enter que allí significaba otra cosa. Ponlo una vez y olvídate. El interruptor
general sigue mandando: apagado ahí es apagado en todas partes.

## Revisar un mensaje antes de que salga

Por defecto el mensaje se envía en cuanto se escribe. Whisper entiende mal cosas,
y en una sesión pública un error es problema de todos, así que cada perfil tiene
un conmutador **Enviar automáticamente**.

Con él apagado, el mensaje se escribe en el chat y se deja ahí. Tu disparador
decide entonces qué pasa con él, sin soltar el volante:

| Gesto | Qué hace |
| --- | --- |
| **Toque** | Enviarlo |
| **Dos toques** | Borrarlo |
| **Mantener** | Borrarlo y grabar otro |

La pestaña Estado muestra **esperando envío** mientras hay un mensaje ahí.

Si te sobran botones, **Ajustes → Disparador** también asigna teclas directas a
*Enviar mensaje en espera* y *Borrar mensaje en espera*. Actúan al instante, sin
ventana de doble toque que aguardar, y conviven con los gestos en vez de
sustituirlos.

**Un toque no puede atenderse enseguida**, porque hasta que se cierra la ventana
de doble toque podría ser la primera mitad de uno. Esa espera es
`review.double_tap_ms`, alrededor de un tercio de segundo. Ponla a `0` en la
configuración para enviar de inmediato y renunciar a borrar con doble toque.
`review.tap_ms` es la frontera entre un toque y un mantenido.

**Una pulsación con un mensaje pendiente empieza a grabar de inmediato**, antes
de saberse si será toque o mantenido. Esperar a averiguarlo se comería las
primeras palabras de la regrabación; el búfer se descarta si resulta ser un
toque.

## Perfiles

Qué perfil se aplica lo decide el ejecutable que tiene el foco, así que se pueden
configurar varios simuladores a la vez y se usa el correcto sin preguntar.

El ajuste que más importa es **Retardo de apertura del chat** (`pre_delay_ms`).
El chat necesita unos fotogramas para abrirse y tomar el foco, y escribir
demasiado pronto pierde los primeros caracteres. Empieza en 350 ms y súbelo si
los mensajes llegan cortados.

| Ajuste | Para qué sirve |
| --- | --- |
| **Retardo de apertura del chat** | Cuánto esperar tras abrir el chat antes de escribir. El que hay que subir si los mensajes llegan cortados |
| **Teclas de abrir chat** | Lo que abre el chat. Enter en la mayoría de simuladores |
| **Teclas de envío** | Lo que lo manda. Enter otra vez, normalmente |
| **Teclas de cancelar** | Lo que cierra el chat sin enviar, para borrar un mensaje en espera |
| **Retención de tecla** | Cuánto se mantiene cada tecla. Los juegos leen la entrada una vez por fotograma, así que una pulsación más corta que un fotograma es una pulsación que el juego nunca ve |
| **Retardo de escritura** | El hueco entre caracteres |
| **Máximo de caracteres** | Los mensajes más largos se cortan. La mayoría de simuladores tiene su propio límite |
| **Enviar automáticamente** | Apagado para revisar antes de enviar — ver arriba |
| **Plugin de sesión** | Lee quién está en la sesión para que los nombres se transcriban bien y se conviertan en menciones. Déjalo en *automático* |

### Unicode o códigos de exploración

**Modo de escritura** decide cómo llegan los caracteres al juego. *Unicode* envía
el carácter en sí y se lleva bien con cualquier distribución de teclado y
cualquier alfabeto. Algunos juegos lo ignoran porque leen códigos de exploración
del hardware; para esos, cambia a *scancode*, que escribe como si las teclas se
hubieran pulsado físicamente.

Los códigos de exploración se limitan a lo que puede producir un teclado
estadounidense, así que los caracteres acentuados y los alfabetos no latinos no
sobreviven. Prueba primero unicode; el ajuste existe porque «el juego ignora lo
que escribimos» tenía que ser un cambio de configuración y no de código.

Los dos también van con tiempos distintos, y por eso son modos separados. Las
teclas de scancode se mantienen `key_hold_ms` porque los juegos leen la entrada
una vez por fotograma. El texto escrito no: pasa por la cola de mensajes, y 40 ms
por carácter harían que un mensaje de 200 caracteres tardara ocho segundos.

## Nombres y vocabulario

Whisper transcribe lo que oye, y los nombres de pilotos son justo lo que peor se
le da. El plugin de sesión lee quién está realmente en tu sesión y le pasa esos
nombres, así que «Estre» sale como «Estre» y no como «Ester».

**Vocabulario** añade tus propias palabras encima: nombres de patrocinadores, el
nombre de un equipo, cómo se escriben de verdad los alias de tus amigos.
Cualquier cosa que te veas corrigiendo merece añadirse.

## No se escribe nada

**Mira primero la pestaña Estado.** Muestra con qué está armado el hook ahora
mismo y cuándo se vio el disparador por última vez. Si *Último disparador* no se
actualiza nunca, el problema es la tecla o el hook, no la transcripción.

**Tiene que ejecutarse como administrador.** Windows descarta la entrada
inyectada dirigida a un proceso con un nivel de integridad mayor que el del
remitente, y los simuladores suelen ir elevados. La versión instalada lo pide
automáticamente.

**Comprueba que el perfil coincide.** La pestaña Estado registra el nombre del
ejecutable con el foco; si no es uno de tus perfiles, se está usando el perfil
por defecto y sus teclas de chat puede que no sirvan para ese juego.

**Comprueba el retardo de apertura del chat.** Que los mensajes lleguen sin los
primeros caracteres es `pre_delay_ms` demasiado bajo, siempre.

**Comprueba que el juego no ignora unicode.** Si el chat se abre y no aparece
nada, prueba el modo de escritura *scancode*.
