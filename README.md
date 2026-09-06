# Galería de perfiles de VirtualDeck

Perfiles listos para importar en [VirtualDeck](https://github.com/AndyVillatoro/virtualdeck).

## Cómo usarlos

En VirtualDeck: **⚙ → Galería de perfiles**, y pegue esta dirección:

```
https://raw.githubusercontent.com/AndyVillatoro/virtualdeck-gallery/main/manifest.json
```

Saldrá la lista. Al elegir uno, **antes de importarlo** verá qué va a ejecutar:
cuántos botones trae, cada programa que abre, cada script completo y los atajos
globales que registraría en todo el sistema. Léalo. Un perfil no son datos: es
código que se ejecutará cuando pulse un botón.

Se importa **como perfil**, no como configuración: su deck actual no se toca.

## Los perfiles

| Perfil | Botones | Necesita |
|---|---|---|
| **Esencial** | 16 | Nada. Funciona recién instalado. |
| **Trabajo** | 12 | Nada. |
| **Streaming** | 12 | OBS, y asignar los atajos en Ajustes → Atajos. |
| **RGB** | 8 | OpenRGB con el servidor SDK encendido. |

**Streaming** no controla OBS directamente: manda pulsaciones de teclado. Los
atajos que espera (`Ctrl+Shift+F1` a `F4`, `Ctrl+Shift+R`, `Ctrl+Shift+S`,
`Ctrl+Shift+M`) hay que asignarlos primero en OBS, o los botones no harán nada.

## Aportar un perfil

Abra un *pull request* con su `.json` en `profiles/` y su entrada en
`manifest.json`. Antes de enviarlo, compruébelo contra la versión actual de la
aplicación — desde una copia del repositorio principal:

```bash
node scripts/check-perfiles.mjs ruta/a/su-perfil.json
```

Comprueba que los tipos de acción, los widgets, los presets RGB y las posiciones
de ventana **existan de verdad**. Un tipo inventado no es un fallo visible: el
perfil se importa y el botón no hace nada al pulsarlo.

Además:

- Nada de rutas absolutas de su equipo (`C:\Users\suNombre\...`).
- Nada de datos personales: ni tokens, ni direcciones de webhook privadas, ni
  correos.
- `accent` y `wallpaper` neutros, para no pisar la preferencia de quien lo importe.
- Si el perfil necesita algo instalado, dígalo en `description`. Quien lo importa
  no puede adivinarlo.
- Nada de base64 grande en `imageData`; use `brandIcon` o `customGlyph57`.
