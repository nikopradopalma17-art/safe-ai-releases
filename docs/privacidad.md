# Aviso de privacidad: Safe AI

## En resumen

Todo ocurre en tu computador. Safe AI no sube tus documentos a ningún lado y no guarda su contenido.

## Qué hace con tus documentos

- Los procesa en la memoria del computador y los olvida al terminar.
- No guarda una tabla que una etiqueta (`Sujeto_01`) con una persona real. Por eso el resultado busca ser **anonimizado**, no "seudonimizado" (que sí permitiría volver atrás con una clave).
- Cada documento usa etiquetas nuevas. No se pueden cruzar entre documentos.
- El archivo descargado no usa el nombre del original.

## Qué conexión a internet usa

Solo una, y es opcional: la **consulta de nuevas versiones**.

- Pide a GitHub cuál es la última versión publicada.
- Envía únicamente esa petición y un identificador fijo del programa (`SafeAI-Updater/<versión>`). No envía nada sobre ti, tu computador ni tus documentos.
- Si no hay internet, falla en silencio.

**Para apagarla:** desmarca **Buscar actualizaciones** en el panel lateral. TI también puede definir la variable de entorno `SAFE_AI_DISABLE_UPDATE_CHECK=1`.

La telemetría de Streamlit (el motor de la pantalla del programa) está desactivada.

## Qué se guarda en el computador

En `%LOCALAPPDATA%\SafeAI` hay un registro de actividad local (`audit.jsonl`). Por cada documento anota: fecha y hora, número (`Documento_NN`), tipo de archivo, tamaño, cuántos datos se taparon por tipo, y si hubo error. **No** guarda nombres, valores detectados ni el contenido. Puedes borrarlo cuando quieras.

## Marco legal

En Chile, la **Ley 21.719** de protección de datos personales trata los datos de salud como **datos sensibles**. Safe AI ayuda a cumplir, pero **no lo garantiza**. El área legal o de cumplimiento de tu organización debe validar su uso antes de aplicarlo a documentos reales.

## Riesgo que queda: identificar por pistas

Aunque se taparan todos los nombres, una persona puede ser reconocible por **datos indirectos**: un cargo único, más un lugar, más una fecha. Por ejemplo, "el único jefe de bodega de la obra X, accidentado el 3 de marzo".

**Qué hacer:** antes de compartir, quita o generaliza esas pistas a mano ("un trabajador de la obra" en vez de un cargo único; "marzo" en vez de la fecha exacta).

## Límites de la detección

El programa no detecta el 100% de los datos. Revisa siempre el resultado. Detalles en la [guía de usuario](guia-usuario.md#límites-léelos-antes-de-usar-el-resultado).
