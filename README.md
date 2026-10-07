# Dr. Slump — Traducción al español

[![Invítame a un café en Ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/johanderohan)

Ficha del proyecto, capturas y más traducciones al castellano en **[Parches en Castellano](https://parchesencastellano.com/traducciones/playstation/dr-slump)**.

Traducción al **español de España**, realizada desde el japonés, de
*Dr. Slump* para **PlayStation**, edición **SLPS-01934**.

Se distribuye únicamente un **parche XDELTA**. Necesitas tu propia copia del
juego japonés, con sus dos pistas BIN y su archivo CUE.

## Estado

Última versión: **[v1.1 — Corrige la máquina de asignar botones](../../releases/tag/v1.1)**.

El guion se ha traducido y cotejado con el japonés mediante una segunda
revisión, con una biblia de voces, tratamientos, nombres y términos. El índice
contiene **5.125 cadenas distintas**, presentes en 80.324 registros físicos,
incluidos 87 identificadores técnicos conservados. No son 80.324 frases diferentes.

La traducción y las revisiones son asistidas por modelos; no se presentan como
una revisión humana independiente.

| Parte | Estado |
|---|---|
| Historia, diálogos, pistas y opciones del corpus | Traducción y revisión completas |
| Menús de inicio, ajustes, inventos, guardado y carga | Localizados |
| Caracteres españoles | Tildes, diéresis, ñ, ¡ y ¿ en los cuatro estilos de letra |
| Contraste de las fuentes | Paletas y sombras originales conservadas |
| Pista de la tienda de Suppaman | Inscripción traducida en sus cinco apariciones |
| Logotipos y grandes rótulos de marca | Conservados |
| Voces y pista de audio | Originales japoneses |
| Partida completa de principio a fin | Pendiente |

### Comprobaciones y límites

Probado con **Beetle PSX 0.9.44.1 (82d8e05)**: arranque, máquina de asignar botones, diálogos iniciales,
desplazamiento, opciones, creación y sobrescritura de partidas, reinicio real
y recuperación de la partida. Las pruebas dirigidas cubren fuentes, destinos,
cuestionario, tienda de Suppaman, pruebas sonoras y las tres salidas de GAME OVER.
Las pruebas dirigidas de escenas avanzadas emplean cambios de estado en memoria;
no equivalen a haber llegado a ellas en una partida completa.

Se comprueban las 80.324 entradas del BIN reconstruido, los recursos preservados,
las paletas, los punteros, los límites de memoria de las escenas y la integridad
de los sectores del disco. El parche
se ha reaplicado al original y su resultado coincide byte a byte con la imagen
probada. Las ventanas de selección se han ajustado cuando el castellano lo
necesita, sin acortar los nombres ni eliminar tildes.

El inventario detecta 859 grupos de opciones. Se excluyen del ajuste automático
241 grupos con referencias variables o ambiguas que requieren comprobaciones
específicas. Se han ejercitado guardado, inventos y sonido, sin afirmar cobertura
visual de todos esos grupos.

Queda por comprobar una partida completa con todas sus ramas y la compatibilidad
en consola física. No se ha realizado una auditoría auditiva completa ni una
comprobación física de la vibración. Los nombres internos de la partida en la
tarjeta de memoria conservan el formato japonés que usa el juego para leer el
capítulo; el listado dentro del juego aparece en castellano.

## Cómo aplicar el parche

1. Descarga **`dr-slump-es-v1.1.xdelta`** de **[Releases](../../releases/tag/v1.1)**.
2. Conserva una copia de los dos BIN y del CUE originales. Comprueba la pista
   de datos japonesa antes de aplicar el parche:

   | Dato | Valor |
   |---|---|
   | Archivo de entrada | `Dr. Slump (Japan) (Track 1).bin` |
   | Tamaño | 59.009.328 bytes |
   | MD5 | `70257810796c64b6b2b9b3778ac8bb8e` |
   | SHA-256 | `4a8949786660287ed4edf293f4b5ac456353ab226d5a74d992bcf51d42c7e043` |

   ```bash
   md5sum "Dr. Slump (Japan) (Track 1).bin"     # Linux
   md5 "Dr. Slump (Japan) (Track 1).bin"        # macOS
   CertUtil -hashfile "Dr. Slump (Japan) (Track 1).bin" MD5   # Windows
   ```

3. Aplica el parche **solo a Track 1**, guardando un archivo nuevo. Puedes usar
   [Delta Patcher](https://github.com/marco-calautti/DeltaPatcher/releases)
   o ejecutar:

   ```bash
   xdelta3 -d -s "Dr. Slump (Japan) (Track 1).bin" dr-slump-es-v1.1.xdelta "Dr. Slump (es-ES) (Track 1).bin"
   ```

4. Comprueba el resultado:

   | Dato | Valor |
   |---|---|
   | Tamaño del BIN castellano | 65.825.424 bytes |
   | SHA-256 del BIN castellano | `efc49a6b94badafc5e87456f5833a8b95d76a011cae1eb4f44520da18aa167b3` |
   | MD5 del BIN castellano | `985b7d86cd079365de7ddc4754a2e9ae` |
   | SHA-256 del parche | `b625c644542cfcfca5f8091cfeff672cb6e2248d470e07e749ffaadcbe2d52fd` |

5. Copia el CUE con un nombre nuevo y cambia **únicamente el primer `FILE`**
   para apuntar al BIN castellano. Mantén la segunda pista y los índices.
   Si usas los nombres indicados y guardas los archivos en la misma carpeta,
   el CUE debe contener:

   ```cue
   FILE "Dr. Slump (es-ES) (Track 1).bin" BINARY
     TRACK 01 MODE2/2352
       INDEX 01 00:00:00
   FILE "Dr. Slump (Japan) (Track 2).bin" BINARY
     TRACK 02 AUDIO
       INDEX 00 00:00:00
       INDEX 01 00:02:00
   ```

6. Abre el **CUE castellano** en el emulador. Se recomienda empezar una partida
   nueva para seguir toda la historia traducida. Se ha comprobado también la
   carga de una partida japonesa del comienzo del juego.

**No parches Track 2, no unas las pistas y no uses un BIN ya traducido.**
La pista de audio se conserva exacta: 37.396.800 bytes, SHA-256
`ce5509fad13f6210656c9d29fb536b47abe5f824467177652c91b5c500470c77`.
La comprobación de entrada del parche debe permanecer activada.

## Cambios

### v1.1 — 05-10-2026

- Corregida la máquina de asignar botones de la habitación de Arale: ahora se
  ven las cinco acciones con sus iconos y se puede salir con normalidad.
- La ventana de la máquina se ensancha para los nombres en castellano; antes
  «Puñetazo» se partía en dos líneas y desaparecían los demás iconos.
- Corregido un desbordamiento de memoria del mismo menú que podía colgar el
  juego al asignar botones con icono doble (L1, R1…).
- El resto de la traducción no cambia. Aplica el parche nuevo sobre el Track 1
  japonés original, no sobre un BIN ya parcheado con la v1.0.

### v1.0 — 24-09-2026

- Primera versión pública de la traducción al castellano.

## Créditos

Proyecto de traducción: **johanderohan**, con asistencia de Codex.
[HilltopTranslationScripts](https://github.com/HilltopWorks/HilltopTranslationScripts)
se consultó como referencia de los formatos de Dr. Slump. El texto castellano
parte del japonés del disco, no de la traducción inglesa. La extracción y la
reconstrucción se realizaron con herramientas propias. Las letras y sus
variantes españolas se basan en las fuentes originales del juego.

La verificación usa Beetle PSX y Unicorn; el parche se genera con xdelta3.

## Aviso

Traducción de aficionados, sin relación con los titulares de los derechos.
Aquí se distribuye el parche; el juego, sus personajes y sus marcas pertenecen
a sus respectivos titulares. Si eres titular de los derechos y necesitas
contactar, puedes abrir una incidencia en este repositorio.
