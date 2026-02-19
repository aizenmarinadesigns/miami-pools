# Guía: Agregar una nueva card al slider Antes & Después

## Pasos manuales (si lo hacés vos)

### Paso 1 — Preparar la imagen

1. Guardá tu foto en `img/antes-despues/`
2. Nombre de archivo: sin espacios ni acentos, todo minúscula.
   Ejemplo: `renovacion-miami-beach.png`

### Paso 2 — Abrir index.html

Buscá esta línea (está justo antes del cierre del slider):

```html
                    </div><!-- /ba-track -->
```

### Paso 3 — Copiar y pegar el bloque de una card existente

Tomá el bloque completo de una card (desde `<!-- Card N -->` hasta `</article>`).
Pegalo justo **antes** de `</div><!-- /ba-track -->`.

### Paso 4 — Editar los datos de tu nueva card

Cambiá únicamente estos valores:

| Campo | Qué cambiar |
|---|---|
| `src="img/antes-despues/..."` | El nombre de tu imagen nueva |
| `alt="..."` | Descripción breve de la imagen |
| `Kendall` / `Key Biscayne` / etc. | Tu ubicación nueva |
| `6 horas` / `3 días` / etc. | El tiempo que llevó el trabajo |
| `Limpieza profunda` / etc. | El nombre del servicio |
| `$350` / `$4,200` / etc. | El precio cobrado |

### Paso 5 — Listo. No toques nada más.

El JS detecta automáticamente cuántas cards hay y actualiza:
- Los **dots** indicadores
- Las **flechas** (activa/desactiva según cuántas páginas hay)
- El comportamiento en **mobile/tablet/desktop**

No hay nada más que configurar.

---

## Plantilla de card para copiar y pegar

```html
<!-- ══════════════════════════════════════════
     CARD N — [Escribí la ubicación acá]
     Duplicar este bloque para agregar otra card.
     ══════════════════════════════════════════ -->
<article class="ba-card group">
    <div class="rounded-2xl overflow-hidden border border-gray-100 shadow-md bg-white">
        <div class="relative overflow-hidden">
            <img src="img/antes-despues/TU-IMAGEN.png"
                 alt="Descripción de la imagen — Ubicación"
                 class="w-full object-cover group-hover:scale-105 transition-transform"
                 style="height: 240px; transition-duration: 600ms; object-position: center;">
            <span class="ba-badge ba-badge-before lang-es">ANTES</span>
            <span class="ba-badge ba-badge-before lang-en">BEFORE</span>
            <span class="ba-badge ba-badge-after lang-es">DESPUÉS</span>
            <span class="ba-badge ba-badge-after lang-en">AFTER</span>
        </div>
        <div class="ba-meta">
            <div class="ba-meta-cell">
                <p class="ba-meta-label"><span class="lang-es">Ubicación</span><span class="lang-en">Location</span></p>
                <p class="ba-meta-value">TU CIUDAD</p>
            </div>
            <div class="ba-meta-cell">
                <p class="ba-meta-label"><span class="lang-es">Tiempo</span><span class="lang-en">Time</span></p>
                <p class="ba-meta-value"><span class="lang-es">X horas</span><span class="lang-en">X hours</span></p>
            </div>
            <div class="ba-meta-cell">
                <p class="ba-meta-label"><span class="lang-es">Servicio</span><span class="lang-en">Service</span></p>
                <p class="ba-meta-value"><span class="lang-es">NOMBRE DEL SERVICIO</span><span class="lang-en">SERVICE NAME</span></p>
            </div>
            <div class="ba-meta-cell">
                <p class="ba-meta-label"><span class="lang-es">Inversión</span><span class="lang-en">Investment</span></p>
                <p class="ba-meta-value price">$XXX</p>
            </div>
        </div>
    </div>
</article>
```

---

## Prompt para pedirle a Claude que agregue la card

```
En el archivo index.html, agregá una nueva card al slider "Antes & Después"
(sección id="transformaciones"). Usá la plantilla de card que ya existe
en el HTML y agregala justo antes del comentario </div><!-- /ba-track -->.

Datos de la nueva card:
- Imagen: img/antes-despues/[NOMBRE-DE-TU-IMAGEN.png]
- Alt: [descripción breve]
- Ubicación: [ciudad/zona]
- Tiempo: [ej. 2 días]
- Servicio (ES): [nombre en español]
- Servicio (EN): [nombre en inglés]
- Precio: [ej. $780]

No toques el JavaScript ni el CSS del slider. Solo agregá el HTML de la card.
```

---

## Preguntas frecuentes

**¿Cuántas cards puedo tener?**
Las que quieras. El slider funciona igual con 3, 6, 10 o más cards.

**¿Tengo que editar el JS cuando agrego una card?**
No. El JS cuenta las cards automáticamente al cargar la página.

**¿Puedo cambiar el orden de las cards?**
Sí. Las cards se muestran en el orden en que aparecen en el HTML.
Cortá y pegá el bloque `<article class="ba-card...">` donde lo necesites.

**¿Qué pasa si la imagen es horizontal o vertical?**
Todas las imágenes se recortan a 240px de alto con `object-fit: cover`.
Si la foto queda mal centrada, cambiá `object-position: center` por
`object-position: top` o `object-position: bottom` en el `style` de esa card.

**¿El sitio tiene solo español (sin toggle ES/EN)?**
Simplificá así — borrá los `<span class="lang-es">` y `<span class="lang-en">`
y escribí el texto directamente:
```html
<p class="ba-meta-value">Limpieza profunda</p>
```
