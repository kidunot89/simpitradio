# Packs de voz

El ingeniero suena como una persona solo si tiene grabaciones de una. Un pack de
voz es exactamente eso: una carpeta de archivos WAV, uno por frase, que el
ingeniero reproduce en lugar de hablar por el sintetizador de Windows.

Todo lo que diga y no esté en el pack — tu nombre, un tiempo por vuelta, un
piloto del que nunca ha oído hablar — lo sigue diciendo la voz de Windows. Un
pack no tiene que estar completo para merecer la pena.

## Tres maneras de conseguir uno

**Instalar uno publicado.** *Ajustes → Voz* lista los packs publicados para
descarga e instala uno cuando se lo pides, comprobando su suma de verificación
antes de descomprimir nada. Esta es la vía para un idioma que no sea el tuyo.

**Grabarlo tú**, en la ventana. Es la vía sin techo y aquella sobre la que está
construida la aplicación: *Ajustes → Voz → Crear un modelo de voz*.

**Generar una base con Piper**, sin conexión, y volver a grabar las partes que te
importen. Útil si quieres algo correcto y agradable de inmediato, o si prefieres
no leer 171 frases antes de conducir.

No son excluyentes. Un pack de Piper es un pack corriente, así que cualquier
frase suya puede sustituirse más tarde por tu propia toma.

### Por qué no clonación de voz

Se probó primero y se abandonó, y vale la pena conocer el motivo antes de salir a
buscarla.

Para este proyecto se generó una voz clonada a partir de casi tres minutos de
audio de referencia limpio. Devuelta al propio reconocedor de voz de la
aplicación, cada toma de «five» volvía como «bye», «four» como «boy» y «zero»
como «yo».

El inventario es la razón. **141 de sus 171 frases son de una o dos palabras**, y
el texto corto es justamente donde un modelo de clonación está peor: XTTS genera
de forma autorregresiva y decide por sí mismo cuándo parar, y con una frase de
dos palabras casi nada limita esa decisión. Piper es un modelo de estilo VITS —
una sola pasada de fonemas a forma de onda, sin bucle de muestreo que se
desvíe—. No puede decir otra palabra, y en este inventario eso importa más que el
timbre.

Crew Chief resuelve el mismo problema del mismo modo: sus packs están
*grabados*, y sus 11 176 nombres de pilotos y 1 052 clips de números los leyó una
persona.

## Grabar el tuyo

*Ajustes → Voz → Crear un modelo de voz* abre un grabador: una frase que leer,
una cuenta atrás, una toma y la reproducción para comprobarla.

Es menos trabajo de lo que parece. El inventario entero son **unos cuarenta
minutos a tres tomas por frase**, y se reanuda — así que puede hacerse por
sesiones, y un pack que cubra la mitad de las frases funciona desde el momento en
que lo guardas.

Unas pocas cosas deciden si el resultado sirve:

- **A un lado de la boca**, a un par de dedos de distancia, no delante. Un
  micrófono de diadema directamente en el flujo de aire satura en cada *p* y cada
  *b*, y la saturación no se deshace después.
- **Una habitación silenciosa.** Un ventilador o un PC bajo la mesa acaba en cada
  clip, y cada clip se te reproduce a mitad de carrera por unos auriculares.
- **Distancia constante.** No te muevas entre tomas. Clips grabados a cuatro
  distancias distintas suenan a cuatro personas distintas.
- **Desactiva el refuerzo de micrófono de Windows.** Es un compresor, y sube el
  ruido de sala entre palabra y palabra.

Léelas como las diría un ingeniero por la radio: planas, sin prisa, ligeramente
aburridas. El ingeniero no está actuando.

## Generar una base con Piper

Piper se ejecuta sin conexión, desde los scripts de empaquetado y no dentro de la
aplicación:

```
pip install -r packaging/requirements-voices.txt
python -m piper.download_voices --download-dir models/piper en_GB-alan-medium
python packaging/make_piper_pack.py --name Piper
```

Para compilar con un modelo concreto:

```
python packaging/make_piper_pack.py --name Piper --model models/piper/en_GB-alan-medium.onnx
```

**Sin conexión y fuera de la aplicación, a propósito.** Piper es lo bastante
rápido en una CPU como para tentar a llamarlo en el momento de hablar. Eso
metería un modelo de 63 MB y un runtime ONNX dentro de una compilación cuyas
últimas cuatro versiones rotas fueron todas dependencias nativas que no se
recogieron. Un pack es una carpeta de WAV; generarlo aquí no le cuesta nada a la
aplicación y no puede romper una compilación.

No es *tu* voz, y nada pretende lo contrario. Es una base correcta y agradable
sobre la que cualquier frase puede volver a grabarse en la ventana.

**El japonés necesita un paquete más y falla de forma confusa sin él.** El
modelo japonés le pide a Piper `pyopenjtalk` para convertir texto en fonemas, y
sin él cada frase no produce audio alguno — se informa como
`wave.Error: # channels not specified`, que es el archivo de salida vacío y no
la causa real. El `pyopenjtalk` original solo publica código fuente y exige
CMake y un compilador de C++; `pyopenjtalk-plus` es un fork que publica wheels
con el mismo nombre de importación, y está en el archivo de requisitos de
arriba.

## Cómo es un pack

Un pack es una carpeta con una subcarpeta `voice` dentro que contiene los WAV —el
mismo diseño que escribe `crew-chief-autovoicepack`, así que **un pack de Crew
Chief entra directamente**—. La carpeta exterior está separada para que un pack
pueda llevar una licencia y sus grabaciones originales sin que se confundan con
frases.

```
voices/
  Norman/
    voice/
      go_ahead.wav
      box_this_lap.wav
      ...
```

Solo WAV. Es lo que emite cualquier generador, lo que lee la biblioteca estándar,
y no necesita decodificador en una compilación que ya pelea con dependencias
nativas.

Los nombres de archivo salen de la frase, en minúsculas, con la puntuación
**eliminada** en vez de sustituida — así «that's enough» y «thats enough» son el
mismo clip—. Convertir un apóstrofo en separador daría `that_s_enough`, y un pack
grabado contra una de las dos grafías fallaría la otra en silencio.

## Dónde viven los packs

**Ajustes → Voz** es donde están todos listados: lo instalado, lo incluido y lo
descargable. Los packs viven junto a tu configuración, en `voices/`, no bajo el
directorio de instalación: una actualización reemplaza ese directorio por
completo, y un pack es mucho audio que decidiste poner ahí. **Ajustes → Voz →
Abrir carpeta de packs de voz** la abre.

Deja una carpeta dentro, vuelve a abrir la pestaña, y aparece en el selector.

## La lista de frases

**Ajustes → Voz → Escribir lista de frases** exporta todas las frases que el
ingeniero puede decir, en CSV, en el idioma del propio ingeniero — porque un pack
se graba en el idioma en que se va a hablar.

Se genera desde la aplicación en vez de mantenerse a mano, así que no puede
desviarse de lo que el ingeniero dice de verdad. Úsala si grabas fuera de la
aplicación o si te programas un generador propio.

## No suena nada

**Comprueba que hay un pack seleccionado.** *Ingeniero → Voz → Voz* tiene que
apuntar al pack y no a *(sin pack)*.

**Comprueba el dispositivo de salida.** *Audio → Salida* debería ser tus
auriculares, los mismos que usas para el chat de voz, no la salida del simulador.

**Que falte una frase no es un fallo.** Todo lo que no esté en el pack recae en
la voz de Windows, así que un pack a medio grabar suena a dos personas en vez de
fallar. Es intencionado: es lo que hace que un pack sirva antes de estar
terminado.
