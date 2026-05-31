# Mapa Gagné — Cuadro Sinóptico

Página estática que publica el cuadro sinóptico de la **Teoría del Aprendizaje de Robert Gagné** (Actividad 3.2, Unidad 3).

## Estructura

```
web/
├── index.html      ← contenido + SVG del mapa (autocontenido)
├── package.json    ← define el script "start" para Railway
├── railway.json    ← configuración de despliegue
└── README.md
```

Todo el contenido (HTML, CSS y el SVG del mapa) está en **`index.html`**.

---

## Probar localmente

```bash
npx serve -s . -l 3000
```

Abre <http://localhost:3000>.

---

## Publicar en GitHub

```bash
cd web
git init
git add .
git commit -m "Mapa sinóptico Gagné — Actividad 3.2"
git branch -M main
git remote add origin https://github.com/<TU-USUARIO>/mapa-gagne.git
git push -u origin main
```

> Si solo quieres GitHub Pages (sin Railway), activa Pages en
> **Settings → Pages → Branch: main / root** y listo.

---

## Desplegar en Railway

1. Entra a <https://railway.app> y elige **New Project → Deploy from GitHub repo**.
2. Selecciona el repositorio recién creado.
3. Railway detecta `package.json`, instala `serve` y ejecuta `npm start`.
4. En **Settings → Networking → Generate Domain** obtienes la URL pública.

La variable `PORT` la inyecta Railway automáticamente; el script de `start` la lee.

### Cómo funciona el despliegue

- `package.json` declara la dependencia `serve` (servidor de estáticos).
- El script `start` ejecuta `serve -s . -l $PORT` apuntando al directorio actual.
- `railway.json` indica al builder Nixpacks que use ese comando.

---

## Editar el contenido

Todo el texto y el mapa están en `index.html`. Para cambiar:

- **Texto**: edita las `<section>` (intro, conclusiones, referencias).
- **Mapa**: edita los elementos `<rect>` y `<text>` dentro de los `<svg>`.
- **Colores**: cambia las variables CSS en `:root` (`--root`, `--l1`, etc.).
- **Estilos**: el bloque `<style>` al inicio de `index.html`.

Tras editar, haz `git push` y Railway redepliega solo.
