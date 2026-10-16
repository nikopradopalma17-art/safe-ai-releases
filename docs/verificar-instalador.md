# Verificar el instalador (para TI y usuarios avanzados)

El instalador todavía **no tiene firma digital**, así que Windows puede mostrar el aviso SmartScreen. Para confirmar que el archivo no fue alterado, compara su huella SHA-256 con la publicada en la misma versión.

## Pasos

1. Entra a <https://github.com/nikopradopalma17-art/safe-ai-releases/releases/latest>.
2. Descarga los dos archivos de la misma versión:
   - `SafeAI-Setup-X.Y.Z.exe`
   - `SafeAI-Setup-X.Y.Z.exe.sha256`
3. Abre PowerShell en la carpeta de descarga y calcula la huella:

   ```powershell
   Get-FileHash .\SafeAI-Setup-X.Y.Z.exe -Algorithm SHA256
   ```

4. Abre el archivo `.sha256` con el Bloc de notas. Contiene una línea con este formato: `<huella>  SafeAI-Setup-X.Y.Z.exe`.
5. Compara las dos huellas. Deben ser **idénticas** (PowerShell las muestra en mayúsculas; la comparación no distingue mayúsculas).

Opcional, para comparar automáticamente:

```powershell
$esperado = (Get-Content .\SafeAI-Setup-X.Y.Z.exe.sha256).Split(' ')[0]
$real = (Get-FileHash .\SafeAI-Setup-X.Y.Z.exe -Algorithm SHA256).Hash
$esperado -ieq $real
```

Debe responder `True`.

## Resultado

- **Coinciden:** el archivo es el publicado. Se puede ejecutar. Si aparece SmartScreen, pulsa **Más información** y **Ejecutar de todas formas**.
- **No coinciden:** no lo ejecutes. Bórralo, vuelve a descargarlo desde la página oficial y repite. Si sigue distinto, avisa al equipo de desarrollo.

## Límite de esta verificación

La huella publicada está en el mismo sitio que el instalador. Confirma que la descarga no se dañó ni cambió en el camino, pero no prueba quién lo publicó. La firma digital sí lo probaría (pendiente; la decisión está en manos del equipo de desarrollo).
