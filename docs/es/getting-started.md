# Primeros pasos

Instálalo, dile qué tecla debe escuchar y di algo. Todo lo demás después de
eso es opcional.

![La ventana de SimPitRadio en la pestaña Estado](images/window.png)

## Instalación

Descarga el instalador desde la
[página de versiones](https://github.com/kidunot89/simpitradio/releases/latest)
y ejecútalo. Windows te avisará: las compilaciones no están firmadas, así que
SmartScreen muestra «Windows protegió su PC» y tienes que elegir **Más
información → Ejecutar de todas formas**. Así se ve un instalador sin firmar,
y firmar cuesta un dinero que el proyecto no gasta.

La instalación hace una sola pregunta: **qué idioma**, con el de tu Windows ya
elegido. Fija tres cosas a la vez: la ventana, el modelo de voz y el idioma en
el que el ingeniero habla y escucha. La pestaña Idioma lo cambia después.

**Se instala como administrador, a propósito.** Windows descarta las
pulsaciones inyectadas hacia un programa que corre con más privilegios que
quien las envía, y los simuladores suelen ir elevados. Sin esto, todo parece
funcionar y nada llega nunca al juego.

### El primer arranque descarga dos cosas

En el instalador no viaja nada grande, así que la primera vez que lo abres se
te pide traer:

- **el modelo de voz**, unos 250 MB, que es lo que convierte tu voz en texto
- **un pack de voz** para el ingeniero, unos 45 MB, si hay uno publicado en tu
  idioma

Ambas cosas, una sola vez. El modelo vive fuera del directorio de instalación,
así que una actualización nunca vuelve a costarlo. Di «ahora no» y las
pestañas Idioma y Ajustes los traen cuando quieras.

La versión portable no tiene instalador ni pregunta de idioma, así que la hace
en el primer arranque.

## Elige una tecla

**Ajustes → Disparador.** Pulsa *Pulsa una tecla…* y luego pulsa la que
quieras.

![La sección Disparador de la pestaña Ajustes](images/trigger.png)

La tecla se **traga al pasar**, así que el juego nunca la ve. Puedes vincular
una que el juego ya use y no se rompe nada. `F13` es la predeterminada porque
la mayoría de teclados no la tienen y nada más está escuchándola.

**Un botón del volante también sirve.** En la fila **Botón del volante**,
pulsa *Pulsa un botón…* y pulsa el botón que quieras. SimPitRadio abre el
volante sin quitárselo al juego, así que el simulador sigue leyendo todos los
botones, incluido ese. Mantenlo pulsado para hablar exactamente igual que con
la tecla. Ambos quedan armados a la vez, así que puedes vincular los dos y
usar el que tengas más cerca.

La otra vía es el software propio de tu volante, o
[JoyToKey](https://joytokey.net/): pon `F13` en un botón y vincula `F13` aquí.
Recurre a esto si el volante ya usa un software de confianza, o si SimPitRadio
no puede abrir el dispositivo.

## Configura el micrófono

**Audio → Micrófono.** Elige la entrada, mantén el disparador y mira la barra
de nivel. Muestra la señal *después* de la ganancia, que es lo que recibe el
modelo de voz. Busca que llegue a unos tres cuartos.

![La pestaña Audio](images/audio.png)

**La salida no debería ser el dispositivo de tu simulador.** El ingeniero, el
entrenador y el aviso de grabación suenan todos aquí, y apuntarla a la misma
salida que usa el juego mete el pitido dentro de la grabación.

Pulsa **Grabar 4 s y transcribir** para oír qué ha entendido. Durante una
prueba no se escribe nada en ninguna parte.

## Di algo

Mantén el disparador, dilo, suéltalo.

1. La tecla se traga.
2. La grabación empieza **de inmediato**, antes de que se abra el chat del
   juego. No se pierde nada de lo dicho en las primeras centésimas.
3. Las teclas de chat abren el chat del juego.
4. Al soltar, el clip va al modelo de voz, en tu propia CPU.
5. El texto se escribe y se disparan las teclas de envío.

La pestaña Estado muestra con qué está armado el hook y cuándo se vio el
disparador por última vez. Si *Último disparo* no se actualiza nunca, el
problema es la tecla o el hook, no la transcripción.

![La tarjeta de Estado](images/status.png)

## Y después, si quieres más

El ingeniero, el entrenador y el chat de voz están todos apagados hasta que
los enciendes.

| | |
| --- | --- |
| [Chat de texto](text-chat.md) | El chat de texto en sí: perfiles, revisar antes de enviar, qué hacer si no se escribe nada |
| [El ingeniero](engineer.md) | Una voz con nombre que lee tus vueltas, avisa de coches al costado y responde preguntas |
| [El entrenador](coaching.md) | Tu trazada frente a la de un rival tras cada curva, con qué cambiar |
| [Voz en la radio](voice-chat.md) | Oír a los demás pilotos de tu sesión, y solo a los que están cerca |
| [Packs de voz](voicepacks.md) | Grabar o instalar la voz con la que habla el ingeniero |

## Cuando algo va mal

**Mira primero la pestaña Estado.** Es el único sitio que muestra lo que la
aplicación cree: la tecla armada, el ejecutable en foco, el perfil en uso y un
registro en vivo.

![El registro en la pestaña Estado](images/log.png)

- **No se escribe nada.** Ver [No se escribe nada](text-chat.md#no-se-escribe-nada).
- **No se habla.** Ver [No se habla](engineer.md#no-se-habla).
- **No se dibuja nada.** Ver [No se dibuja nada](coaching.md#no-se-dibuja-nada).

El registro también se guarda en un archivo. **Estado → Abrir carpeta de
registros** te lleva allí, y es lo primero que merece la pena adjuntar a un
informe.
