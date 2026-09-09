# Primeros pasos

Instálalo, dile qué tecla debe escuchar y di algo. Todo lo demás en estas
páginas es opcional.

![La ventana de SimPitRadio en la pestaña Estado](images/window.png)

## Instalación

Descarga el instalador desde la
[página de versiones](https://github.com/kidunot89/simpitradio/releases/latest) y
ejecútalo. Windows te avisará: las compilaciones no están firmadas, así que
SmartScreen muestra «Windows protegió su PC» y tienes que elegir **Más
información → Ejecutar de todas formas**. Así se ve un instalador sin firmar, y
firmar cuesta un dinero que este proyecto no gasta.

La instalación hace una sola pregunta — **qué idioma** — con el de tu Windows ya
elegido. Eso fija tres cosas a la vez: la ventana, el reconocimiento de voz y el
idioma en que el ingeniero de pista habla y escucha. Puedes cambiarlo después en
la pestaña Idioma.

**Se instala como administrador, a propósito.** Windows descarta las pulsaciones
inyectadas hacia un programa que corre con más privilegios que quien las envía, y
los simuladores suelen ir elevados. Sin esto, todo parece funcionar y nada llega
nunca al juego.

### El primer arranque descarga dos cosas

En el instalador no viaja nada grande, así que la primera vez que lo abres se te
pide traer:

- **el modelo de voz**, unos 250 MB, que es lo que convierte tu voz en texto
- **una voz grabada** para el ingeniero, unos 45 MB, si hay alguna publicada en
  tu idioma

Ambas cosas, una sola vez. El modelo vive fuera del directorio de instalación,
de modo que una actualización nunca vuelve a costarlo. Si dices «ahora no», las
pestañas Idioma y Ajustes hacen lo mismo cuando quieras.

El zip portable no tiene instalador y por tanto tampoco pregunta el idioma: lo
pregunta en el primer arranque.

## Elige una tecla

**Ajustes → Disparador.** Pulsa *Pulsa una tecla…* y luego la que quieras.

![La sección Disparador de la pestaña Ajustes](images/trigger.png)

La tecla se **traga al pasar**, así que el juego nunca la ve, lo que significa
que puedes usar una que el juego ya utilice. `F13` es la predeterminada porque
la mayoría de teclados no la tienen y nada más está escuchándola.

**Un botón del volante sirve.** Asígnalo a una tecla con
[JoyToKey](https://joytokey.net/) y vincula esa tecla aquí. SimPitRadio no lee
los volantes directamente, y el motivo está en
[las notas del ingeniero](engineer.md#ajustes-por-simulador): un aro Fanatec enumeró
79 entradas y no informó de una sola pulsación a través de ninguna de cuatro
bibliotecas distintas, y leer un Steam Controller siquiera significaba
quitárselo a Steam.

## Configura el micrófono

**Audio → Micrófono.** Elige la entrada, mantén el disparador y mira la barra de
nivel: muestra la señal *después* de la ganancia, que es lo que Whisper recibe
de verdad. Busca que llegue a unos tres cuartos.

![La pestaña Audio](images/audio.png)

**La salida no debería ser el dispositivo de tu simulador.** El ingeniero, el
entrenador y el aviso de grabación suenan todos aquí; apuntarla a la misma
salida que usa el juego mete el pitido dentro de la grabación.

Pulsa **Grabar 4 s y transcribir** para oír qué ha entendido. Durante una prueba
no se escribe nada en ninguna parte.

## Di algo

Mantén la tecla, di lo que quieras decir, suéltala.

1. La tecla se traga.
2. La grabación empieza **de inmediato**, antes de que se abra el chat, para que
   no se pierda nada de las primeras centésimas.
3. Las teclas de chat abren el chat del juego.
4. Al soltar, el clip va a Whisper, en tu propia CPU.
5. El texto se escribe y se disparan las teclas de envío.

La pestaña Estado muestra con qué está armado el hook y cuándo se vio el
disparador por última vez. Si *Último disparador* no se actualiza nunca, el
problema es la tecla o el hook, no la transcripción.

![La tarjeta de Estado](images/status.png)

## Y después, si quieres más

Nada de lo siguiente está activo por defecto.

| | |
| --- | --- |
| [Chat de texto](text-chat.md) | El dictado en sí: perfiles, revisar antes de enviar, qué hacer si no se escribe nada |
| [El ingeniero](engineer.md) | Una voz con nombre que lee tus vueltas, avisa de coches al costado y responde preguntas |
| [El entrenador](coaching.md) | Tu trazada frente a la de un rival tras cada curva, con qué cambiar |
| [Voz en la radio](voice-chat.md) | Oír a los demás pilotos de tu sesión, y solo a los que están cerca |
| [Packs de voz](voicepacks.md) | Grabar o instalar la voz con la que habla el ingeniero |

## Cuando algo va mal

**Mira primero la pestaña Estado.** Es el único sitio que muestra lo que la
aplicación cree: la tecla armada, el ejecutable en foco, el perfil en uso y un
registro en vivo.

![El registro en la pestaña Estado](images/log.png)

- **No se escribe nada** — ver [No se escribe nada](text-chat.md#no-se-escribe-nada).
- **No se habla** — ver [No se habla](engineer.md#no-se-habla).
- **No se dibuja nada** — ver [No se dibuja nada](coaching.md#no-se-dibuja-nada).

El registro también se guarda en un archivo. **Estado → Abrir carpeta de
registros** te lleva allí, y es lo primero que merece la pena adjuntar a un
informe.
