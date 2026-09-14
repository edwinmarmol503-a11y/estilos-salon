# ESTILO'S SALÓN — Sitio Web

Experiencia web premium para un salón de belleza en El Salvador. Negro profundo + azul neón,
intro cinematográfica del logo con ilusión de profundidad, animaciones con GSAP + ScrollTrigger.

## Cómo ver el sitio

Este es un sitio estático (HTML/CSS/JS puro, sin build step). Basta con servirlo:

```bash
npx serve .
```

o abrir `index.html` directamente con Live Server en VS Code. No abras el archivo con doble clic
(`file://`) para desarrollo — algunos navegadores restringen fuentes/scripts en ese modo.

## Estructura

```
/estilos-salon
  index.html
  /css
    style.css        → estilos base, layout, componentes
    animations.css    → @keyframes + prefers-reduced-motion
    responsive.css     → media queries (tablet/mobile) + fixes de hover táctil
  /js
    navigation.js      → navbar sticky, menú móvil, scroll suave, año del footer
    animations.js      → intro cinematográfica (GSAP timeline), tilt 3D del logo,
                          partículas del hero, ScrollTrigger reveals
    gallery.js          → lightbox de la galería
    main.js             → cursor personalizado, envío del formulario de contacto
  /assets
    /images
      logo-symbol.svg     → símbolo recreado en vector a partir del logo proporcionado
      about-salon.jpg     → foto temporal de stock (Unsplash) para Nosotros
      service-*.jpg (x6)  → fotos temporales de stock para cada tarjeta de Servicios
      gallery-1..7.jpg    → fotos temporales de stock para la Galería
    /icons
    /fonts
```

## ⚠️ Pendientes antes de publicar (contenido real)

El sitio está construido con placeholders claramente marcados como `[AGREGAR ...]`. Reemplaza:

1. **Logo**: `assets/images/logo-symbol.svg` fue recreado a mano en vector porque no se recibió
   el archivo original del logo, solo una vista previa en el chat. Si tienes el archivo original
   (PNG/SVG/AI), reemplázalo en esa ruta — funciona igual como capa independiente del wordmark.
2. **Fotografías (IMPORTANTE)**: las fotos de Nosotros, Servicios y Galería son actualmente
   **fotos de stock temporales de Unsplash** (licencia libre para uso comercial), usadas solo para
   mostrar cómo luce el diseño con imágenes reales — no son fotos del salón. Para producción,
   sustitúyelas por fotografía real del negocio: mismo nombre de archivo en `assets/images/`
   (`about-salon.jpg`, `service-corte.jpg`, `service-color.jpg`, `service-tratamientos.jpg`,
   `service-manicure.jpg`, `service-unas.jpg`, `service-peinados.jpg`, `gallery-1.jpg` a
   `gallery-7.jpg`) para que el sitio las tome automáticamente sin tocar el HTML.
3. **Textos**: slogan ("Tu estilo comienza aquí." — temporal), precios de servicios, años/estadísticas
   de Nosotros, direcciones y horarios de Sucursales, teléfono/correo/redes de Contacto y Footer,
   número de WhatsApp (`whatsapp-fab` href y footer).
4. **Formulario de contacto**: `#contactForm` en `main.js` solo simula el envío. Conéctalo a tu
   servicio real (backend propio, Formspree, WhatsApp Business API, etc.).

## Notas técnicas

- Tipografías: Cormorant Garamond (display) + Jost (texto), vía Google Fonts.
- Animaciones: GSAP 3 + ScrollTrigger vía CDN (cdnjs). Sin dependencia de Three.js — la
  profundidad del logo se logra con CSS 3D (`perspective`, `translateZ`, capas), suficiente para
  el efecto deseado sin costo de rendimiento.
- Accesibilidad: navegación por teclado, `prefers-reduced-motion` respetado (desactiva intro y
  animaciones decorativas), foco visible, formulario con labels asociados.
- El cursor personalizado y el tilt 3D del logo se desactivan automáticamente en pantallas
  táctiles / anchos menores a 900px.
