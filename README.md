# Mapples Radio (GitHub Pages)

Sitio estático de la radio **Mapples** listo para publicar gratis con **GitHub Pages**.

> Resultado final: `https://TU_USUARIO.github.io/mapples` (cambia el nombre del repo si quieres).

---

## 1) Estructura
Solo necesitas estos archivos:
```
mapples/
├── index.html
├── .nojekyll
└── README.md
```

- `index.html` contiene todo el reproductor.
- `.nojekyll` evita que GitHub Pages aplique Jekyll (importante si luego agregas carpetas que empiecen con guión bajo).

---

## 2) Configura tu stream
Edita `index.html` y cambia estas líneas al inicio del `<script>`:

```js
const STREAM_URL   = "https://your-stream.example.com/stream.mp3"; // <<— REEMPLAZAR
const METADATA_URL = ""; // (opcional Icecast) p.ej. "https://tu-icecast/status-json.xsl"
```

**Requisitos:**
- **HTTPS obligatorio**: si tu sitio carga por HTTPS y el stream es HTTP, el navegador lo bloqueará por *mixed content*.
- Si usas **Icecast**, el `status-json.xsl` te permite mostrar el “Ahora suena” (título de la emisora o pista).

---

## 3) Publicar en GitHub Pages (GUI web)
1. Crea un repositorio en GitHub, por ejemplo: `mapples`.
2. Sube los archivos (`index.html`, `.nojekyll`, `README.md`) desde la web (Add file → Upload files) o con Git.
3. Ve a **Settings → Pages**.
4. En **Source**, elige **Deploy from a branch**.
5. Selecciona la rama (normalmente `main`) y la carpeta **/** (root). Guarda.
6. Espera a que aparezca la URL (`https://TU_USUARIO.github.io/mapples`) y pruébalo.

> Cambios futuros: cada vez que edites y hagas *commit/push*, GitHub Pages se re‑publica automáticamente.

---

## 4) Publicar con Git (línea de comandos)

```bash
# 1) Clonar repo vacío (o inicia git en tu carpeta actual)
git init
git branch -M main

# 2) Añadir archivos
git add index.html .nojekyll README.md
git commit -m "Primera versión de Mapples Radio"

# 3) Conecta tu repositorio remoto (cambia TU_USUARIO)
git remote add origin https://github.com/TU_USUARIO/mapples.git
git push -u origin main
```

Luego activa **Settings → Pages** como arriba.

---

## 5) Problemas comunes

- **Suena en PC pero no en móvil** → revisa que el formato/codec del stream sea compatible (MP3/AAC suelen ir bien).
- **No suena** → verifica que la URL existe, sirve por **HTTPS** y permite ser consumida desde otros orígenes (CORS del servidor).
- **No muestra “Ahora suena”** → asegúrate de poner `METADATA_URL` de Icecast; algunos hostings limitan ese endpoint.

---

© 2025 Mapples Radio
