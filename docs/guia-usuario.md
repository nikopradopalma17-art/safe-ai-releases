# Guía de usuario: Safe AI

Safe AI es un programa para Windows que **borra los datos personales de tus documentos** (nombres, RUT, teléfonos, correos, direcciones, fechas de nacimiento y diagnósticos) y los reemplaza por etiquetas como `Sujeto_01`. Funciona en tu computador, sin internet, y no guarda tus documentos.

> **Importante:** el programa se equivoca a veces. **Revisa siempre el resultado antes de compartirlo.** Ver [Límites](#límites-léelos-antes-de-usar-el-resultado).

## Instalar

1. Entra a la página de descargas: <https://github.com/nikopradopalma17-art/safe-ai-releases/releases/latest>
2. Descarga el archivo `SafeAI-Setup-X.Y.Z.exe` (X.Y.Z es el número de versión).
3. Haz doble clic en el archivo y sigue los pasos. No pide clave de administrador.

**Si Windows muestra "Windows protegió su PC" (SmartScreen):** el instalador aún no tiene firma digital, por eso aparece este aviso. No lo ignores sin más.

1. Pide a TI que confirme el archivo. Ellos usan la [guía de verificación](verificar-instalador.md) (compara la "huella" del archivo con la publicada en la misma página de descargas).
2. Solo si TI confirma que es el archivo correcto: pulsa **Más información** y luego **Ejecutar de todas formas**.

## Abrir el programa

1. Abre el menú Inicio y busca **Safe AI**.
2. Se abre una pestaña en tu navegador. Es normal: el programa corre en tu computador, no en internet.
3. Funciona sin conexión a internet.

Si no se abre sola, escribe en tu navegador: `http://localhost:8501`

## Usar el programa

1. En la pestaña **Anonimizar y Exportar Documento**, sube tu archivo. Puedes usar Excel, CSV, Word, PDF, TXT o MD.
2. Revisa la vista previa del resultado.
3. Descarga el archivo. Se llama `Documento_01_ANONIMIZADO...`.
4. **Lee el archivo descargado** y busca datos que hayan quedado sin tapar.
5. Solo entonces compártelo.

El nombre del archivo nuevo nunca incluye el nombre del original. Cada documento recibe el siguiente número (`Documento_02`, `Documento_03`...). La numeración vuelve a empezar cuando cierras y abres el programa.

## Qué se anonimiza

| Dato | Ejemplo de etiqueta |
| --- | --- |
| Nombres de personas | `Sujeto_01` |
| RUT | `RUT_01` |
| Teléfonos | `Telefono_01` |
| Correos | `usuario_01@privado.local` |
| Diagnósticos y códigos CIE-10 | `Diagnostico_01` |
| Direcciones y fechas de nacimiento | etiqueta según el tipo |

La misma persona recibe la misma etiqueta dentro de un documento. **En otro documento, las etiquetas empiezan de nuevo.** No existe una lista que diga quién es `Sujeto_01`: el resultado no se puede revertir.

## Límites (léelos antes de usar el resultado)

**El programa no es 100% exacto.** Lo probamos con documentos de ejemplo inventados, parecidos a los de SST:

- En el primer examen con documentos que no había visto antes, tapó cerca de **92 de cada 100** datos.
- Después de mejorarlo, tapa cerca de **98 de cada 100** en nuestros documentos de prueba. Con documentos reales el resultado puede ser menor.

Donde más falla:

- **Nombres de pila solos** (por ejemplo, "Juan" sin apellido ni contexto).
- **RUT sin contexto**, por ejemplo un número suelto sin la palabra "RUT" cerca.
- Teléfonos fijos de regiones escritos sin espacios ni guiones.

También puede tapar de más (por ejemplo, un nombre de comuna). Eso es preferible a dejar pasar un dato.

**Qué hacer:** lee el resultado completo. Si ves un dato personal, bórralo a mano. Aunque se tapen los nombres, un cargo poco común más lugar y fecha puede identificar a alguien. Mira la [nota de privacidad](privacidad.md).

## Actualizaciones

1. Cuando hay una versión nueva, arriba aparece el aviso **"Hay una nueva versión"**.
2. Pulsa **Descargar** y baja el nuevo `SafeAI-Setup-X.Y.Z.exe`.
3. Ábrelo e instálalo encima de la versión anterior. No hace falta desinstalar. Tus datos se mantienen.

El programa no se actualiza solo. Para saber si hay versión nueva consulta GitHub (no envía datos tuyos ni de tus documentos). Para apagar esta consulta, desmarca **Buscar actualizaciones** en el panel lateral.

## Dónde se guardan los datos

En `%LOCALAPPDATA%\SafeAI` (pega esa ruta en el Explorador de archivos). Ahí solo hay:

- Un registro de actividad con cantidades (número de documento, tipo de archivo, cuántos datos se taparon). **Nunca** nombres ni contenido de documentos.
- Tu configuración y los archivos de registro del programa (carpeta `logs`).

Tus documentos no se guardan.

## Desinstalar

1. Abre **Configuración**, luego **Aplicaciones**.
2. Busca **Safe AI** y pulsa **Desinstalar**.

La carpeta `%LOCALAPPDATA%\SafeAI` no se borra sola. Puedes borrarla a mano si quieres.

## Si algo falla

- **No se abre:** vuelve a abrir **Safe AI** desde Inicio y espera unos segundos.
- **El navegador no se abrió solo:** escribe `http://localhost:8501`.
- **El puerto está ocupado:** otro programa usa esa dirección. Safe AI elige otra libre; si el navegador no la muestra, cierra Safe AI y ábrelo de nuevo. Si sigue igual, avisa a TI.
- **Sigue sin funcionar:** envía a TI los archivos de la carpeta `logs` dentro de `%LOCALAPPDATA%\SafeAI`.

## Ollama (opcional)

Ollama es otro programa que sirve para análisis con IA en tu propio computador. Safe AI funciona perfecto sin él. Si lo tienes instalado, el panel lateral lo mostrará como conectado.
