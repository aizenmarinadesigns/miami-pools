# Prompt para crear la galería Antes & Después

Copiá este prompt exacto en Claude cuando empieces un sitio nuevo.
Reemplazá los valores entre `[CORCHETES]` con la info de tu cliente.

---

## PROMPT PARA COPIAR

```
Quiero que agregues una sección "Antes & Después" en index.html.
Es un slider de cards con imágenes reales del trabajo del cliente.

DATOS DEL SITIO:
- Color primario: [ej. sky-500 / #0ea5e9]
- Color acento (precio): [ej. #0284c7]
- Fondo de la sección: [ej. bg-white / bg-gray-50]
- Idiomas: [ES solamente / ES + EN con toggle]
- Nombre del negocio: [ej. Miami Pools]

CARDS A CREAR (una por trabajo):
Card 1:
  - Imagen: [URL o nombre de archivo local, ej. img/antes-despues/trabajo1.png]
  - Alt: [descripción de la imagen]
  - Ubicación: [ej. Kendall]
  - Tiempo: [ej. 6 horas]
  - Servicio: [ej. Limpieza profunda]
  - Precio: [ej. $350]

Card 2: [igual que arriba]
Card 3: [igual que arriba]
(podés agregar las que quieras)

REQUISITOS TÉCNICOS:
- El slider muestra 1 card en mobile, 2 en tablet (≥640px), 3 en desktop (≥1024px)
- Flechas de navegación arriba a la derecha del título
- Dots indicadores debajo del slider
- Swipe táctil en mobile
- Teclado: flechas ← → (que NO funcionen cuando el usuario está en un input/select del formulario)
- Hover: imagen hace scale suave
- Badges "ANTES" y "DESPUÉS" sobre la imagen (izquierda y derecha)
- Grid de 4 datos debajo de la imagen: Ubicación, Tiempo, Servicio, Inversión
- Precio en color acento
- Sin líneas divisorias entre las columnas del grid
- El JS lee las cards dinámicamente → agregar nuevas cards solo requiere agregar HTML

COMENTARIOS EN EL CÓDIGO:
- Comentario claro arriba de cada card que diga "Card N — [Ubicación]"
- Comentario explicando cómo duplicar para agregar más cards

EXTRAS (si el sitio tiene toggle ES/EN):
- Todos los labels (Ubicación/Location, Tiempo/Time, Servicio/Service, Inversión/Investment, ANTES/BEFORE, DESPUÉS/AFTER) en ambos idiomas con span.lang-es y span.lang-en

Quiero que la sección tenga id="transformaciones" y que quede dentro del <main>
de index.html, entre la sección de servicios y los testimonios.
```

---

## NOTAS PARA VOS CUANDO LO USES

| Qué cambiar | Dónde |
|---|---|
| Color primario | `bg-[#TUCOLOR]` en badges y dots activos |
| Fondo de sección | `class="bg-white"` en `<section>` |
| Imágenes | `src="img/antes-despues/TUNOMBRE.png"` |
| Datos de cada card | Los 4 campos: ubicación, tiempo, servicio, precio |
| ID de la sección | `id="transformaciones"` → cambiarlo si el nav apunta a otro anchor |

---

## QUÉ HACE EL SLIDER (para que entiendas qué pedís)

- **Mobile**: 1 card visible, se desliza
- **Tablet** (≥640px): 2 cards
- **Desktop** (≥1024px): 3 cards
- **Navegación**: flechas + dots + swipe + teclado
- **JS automático**: calcula cuántos dots hacer según cuántas cards hay
  → si agregás cards, los dots se actualizan solos
