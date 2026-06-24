# Estación 68 — Tienda de Bebidas (La Plata)

Sitio web de catálogo para **Estación 68**. Muestra vinos, destilados, cervezas y
chocolates, con un **carrito que arma el pedido y lo envía por WhatsApp** listo para coordinar.

Es una página **autocontenida** (un solo `index.html` + carpeta `img/`). No usa frameworks
ni build: se puede abrir directo en el navegador.

---

## Cómo verla

**Opción rápida:** doble clic en `index.html` (se abre en el navegador).

**Opción servidor local** (recomendada, evita problemas de rutas en algunos navegadores):

```bash
# Requiere Node.js instalado (https://nodejs.org)
npx serve -l 3000 .
```

Después abrir http://localhost:3000

---

## Estructura

```
.
├── index.html          ← TODO el sitio (HTML + estilos + lógica del carrito)
├── img/                ← Fotos de productos, logo e imágenes del hero
│   ├── logo.png
│   ├── hero-*.png       ← Fotos apaisadas del hero (fondo completo)
│   └── *.jpeg           ← Fotos de productos del catálogo
└── README.md
```

---

## Cómo editar lo más común

Todo se edita dentro de `index.html`. Buscá estas secciones:

### 1. Número de WhatsApp
Arriba del `<script>` (buscá `const WHATSAPP`):
```js
const WHATSAPP = "5492216617353"; // formato: 54 9 + área + número, sin + ni espacios
```

### 2. Umbral de envío gratis
```js
const ENVIO_GRATIS = 25000;
```

### 3. Productos del catálogo
Buscá `const PRODUCTS = [`. Cada producto es una línea:
```js
{id:'g1', name:'Bombay Sapphire & Bramble', cat:'gin', desc:'...', price:23900, img:'img/bombay-duo.jpeg'},
```
- `price`: precio en pesos (sin puntos).
- `old`: precio tachado (opcional, para ofertas).
- `cat`: categoría para el filtro (`combos`, `regalos`, `gin`, `vodka`, `licores`, `aperitivos`).
- `img`: ruta a la foto.
- `oferta:true`: lo muestra en la sección "Combos & Ofertas".

### 4. Destacados del hero (la fila de abajo que cambia el fondo)
Buscá `const FEATURED = [`. Cada uno apunta a un producto por `pid`:
```js
{pid:'a1', title:'Jägermeister', lead:'...', bg:'img/download.webp'},
```
- `bg`: foto **apaisada** (horizontal) → el hero se ve a pantalla completa.
- Sin `bg`: muestra la botella "flotante" (foto sobre fondo negro).

### 5. Agregar una foto nueva
1. Guardá la imagen en la carpeta `img/`.
2. Referenciala en el producto o destacado con `img:'img/tu-foto.png'`.
3. Para el hero usá fotos **apaisadas** (formato ~16:9, fondo oscuro).

---

## Pendientes / próximos pasos

- [ ] Cargar **precios reales** (los actuales son de ejemplo).
- [ ] Sumar fotos y productos de **vinos, cervezas y chocolates**.
- [ ] (Opcional) Comprar un dominio y publicar el sitio (Netlify / Vercel / GitHub Pages).

---

*Hecho con un solo HTML, sin dependencias. Beber con moderación · Prohibida la venta a menores de 18 años.*
