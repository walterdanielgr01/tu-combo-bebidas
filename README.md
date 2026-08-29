# Tu Combo Bebidas — Carta Online (PWA)

Carta digital con carrito de compras, cálculo de total, forma de pago (transferencia o efectivo) y envío del pedido por WhatsApp. Funciona como **PWA**: se puede instalar en el celular como una app, y funciona sin conexión gracias al Service Worker.

## Estructura del proyecto

```
/
├── index.html              → Carta + carrito + lógica del pedido
├── manifest.json            → Configuración de la PWA (nombre, ícono, colores)
├── service-worker.js        → Cacheo offline
├── icon-192.png              → Ícono de la app (192x192)
├── icon-512.png               → Ícono de la app (512x512)
└── icon-512-maskable.png       → Ícono adaptable (Android)
```

## Publicar en GitHub Pages (gratis)

1. Creá un repositorio nuevo en GitHub (por ejemplo `tucombo-carta`).
2. Subí **todos los archivos de esta carpeta** a la raíz del repositorio (no dentro de una subcarpeta), manteniendo los nombres tal cual.
3. En el repositorio, andá a **Settings → Pages**.
4. En "Source", elegí la rama `main` (o `master`) y la carpeta `/ (root)`.
5. Guardá. GitHub te va a dar una URL del estilo:
   `https://tu-usuario.github.io/tucombo-carta/`
6. Esperá 1-2 minutos y entrá a esa URL. Ya debería funcionar.

### Subida rápida por terminal

```bash
git init
git add .
git commit -m "Carta online con carrito y WhatsApp"
git branch -M main
git remote add origin https://github.com/TU-USUARIO/tucombo-carta.git
git push -u origin main
```

Después activás GitHub Pages como se explicó arriba (paso 3 al 5).

## Instalar como app (PWA)

- **Android (Chrome):** entrar al link → menú (⋮) → "Instalar app" o "Agregar a pantalla de inicio".
- **iPhone (Safari):** entrar al link → botón compartir (□↑) → "Agregar a pantalla de inicio".

Una vez instalada, abre en pantalla completa como una app nativa, sin la barra del navegador.

## Configurar el número de WhatsApp

Dentro de `index.html`, buscá esta línea:

```js
var WHATSAPP_NUMBER = "5491139521822";
```

Y reemplazá el número por el que corresponda (código de país + número, sin `+` ni espacios).

## Notas

- Los precios y productos se leen directamente del texto del HTML (no hay base de datos), así que para modificar el menú alcanza con editar el HTML de cada producto.
- El Service Worker cachea el sitio la primera vez que se visita, para que después ande sin conexión. Si actualizás el contenido y no ves los cambios reflejados, subí la versión del cache en `service-worker.js` (`CACHE_NAME = "tucombo-cache-v2"`, etc.) para forzar la actualización.
