# Design System — Build with AI Landing Page

> **Evento oficial de Google · GDG Choluteca**
> Especificación visual y de componentes para la landing page del evento. Estilo limpio, moderno, inspirado en la identidad de Google Developer Groups (GDG). Alta densidad de información con balance editorial de espacio en blanco.

---

## Table of Contents

1. [Brand Identity](#brand-identity)
2. [Colors](#colors)
3. [Typography](#typography)
4. [Border Radius](#border-radius)
5. [Spacing Grid](#spacing-grid)
6. [Component Specs](#component-specs)
7. [Do's and Don'ts](#dos-and-donts)
8. [Implementation Notes](#implementation-notes)

---

## Brand Identity

| Atributo      | Descripción                                                  |
| ------------- | ------------------------------------------------------------ |
| **Tono**      | Profesional, técnico, inclusivo, entusiasta sin ser informal |
| **Audiencia** | Developers de todos los niveles, estudiantes de tecnología, entusiastas de IA |
| **Keywords**  | Innovación, comunidad, aprendizaje, código abierto, Google   |

---

## Colors

La paleta utiliza los colores oficiales de Google (Material Design) con matices ajustados para máxima legibilidad en web. Se definen tanto en HEX como en su equivalente OKLCH para integración directa con Tailwind CSS v4.

### Core Palette

| Token               | HEX       | OKLCH                          | Uso                                                                 |
| ------------------- | --------- | ------------------------------ | ------------------------------------------------------------------- |
| `--color-gblue`     | `#1A73E8` | `oklch(0.53 0.21 264)`         | Botones CTA primarios, links, foco activo                           |
| `--color-gblue-hover` | `#1557B0` | `oklch(0.44 0.18 264)`       | Hover y estado `:active` del azul primario                          |
| `--color-gred`      | `#EA4335` | `oklch(0.58 0.22 28)`          | Alertas, badges de "Live", destacados urgentes                      |
| `--color-gyellow`   | `#FBBC05` | `oklch(0.83 0.17 85)`          | Insignias decorativas, advertencias, acentos sutiles                |
| `--color-ggreen`    | `#34A853` | `oklch(0.58 0.18 154)`         | Confirmaciones, badges de "Registrado", estados de éxito            |

### Neutrals

| Token                | HEX       | OKLCH                  | Uso                                                        |
| -------------------- | --------- | ---------------------- | ---------------------------------------------------------- |
| `--color-background` | `#FFFFFF` | `oklch(1 0 0)`         | Fondo general de página                                    |
| `--color-surface`    | `#F8F9FA` | `oklch(0.975 0 0)`     | Fondos de tarjetas en reposo, secciones alternas           |
| `--color-text`       | `#202124` | `oklch(0.21 0 0)`      | Texto principal — nunca usar `#000` puro                   |
| `--color-text-muted` | `#5F6368` | `oklch(0.46 0 0)`      | Texto secundario, metadatos, descripciones                 |
| `--color-border`     | `#DADCE0` | `oklch(0.87 0 0)`      | Bordes de inputs, divisores, contornos de tarjetas         |

### Semantic (feedback states)

| Token                 | HEX       | OKLCH                  | Uso                         |
| --------------------- | --------- | ---------------------- | --------------------------- |
| `--color-success`     | `#34A853` | `oklch(0.58 0.18 154)` | Mensajes de éxito           |
| `--color-warning`     | `#FBBC05` | `oklch(0.83 0.17 85)`  | Mensajes de advertencia     |
| `--color-error`       | `#EA4335` | `oklch(0.58 0.22 28)`  | Mensajes de error           |
| `--color-info`        | `#1A73E8` | `oklch(0.53 0.21 264)` | Mensajes informativos       |

### Usage Ratio

```
Google Blue   ████████████████████ 60%  ← Acción principal dominante
Surface       ████████             25%  ← Fondos de sección
Google Red    ███                   5%  ← Acentos puntuales
Google Yellow ██                    5%  ← Detalles decorativos
Google Green  ██                    5%  ← Estados de éxito
```

**Regla de oro:** El azul de Google (`#1A73E8`) debe ser el color dominante en la jerarquía visual. Los demás colores de la paleta Google (rojo, amarillo, verde) se usan como acentos para comunicación semántica, nunca como colores competidores del azul en acciones primarias.

---

## Typography

### Font Stack

| Rol              | Familia                         | Pesos              | Fuente                         |
| ---------------- | ------------------------------- | ------------------ | ------------------------------ |
| **Headings**     | Google Sans / Open Sans         | 700 (Bold)         | `@fontsource-variable/open-sans` |
| **Body / UI**    | Open Sans Variable              | 400, 500, 600      | `@fontsource-variable/open-sans` |
| **Code**         | JetBrains Mono / Fira Code      | 400 (Regular)      | Google Fonts CDN               |

**Fallback stack:** `"Open Sans Variable", "Google Sans", Roboto, system-ui, -apple-system, sans-serif`

### Type Scale

| Token        | Size     | Line Height   | Weight   | Usage                                      |
| ------------ | -------- | ------------- | -------- | ------------------------------------------ |
| `text-hero`  | `48px`   | `56px` (1.16) | 700      | Hero title principal                       |
| `text-h1`    | `40px`   | `48px` (1.2)  | 700      | Títulos de sección                         |
| `text-h2`    | `32px`   | `40px` (1.25) | 700      | Subtítulos de sección                      |
| `text-h3`    | `24px`   | `32px` (1.33) | 600      | Títulos de tarjeta, nombres de speakers    |
| `text-body`  | `16px`   | `24px` (1.5)  | 400      | Párrafos, descripciones generales          |
| `text-sm`    | `14px`   | `20px` (1.43) | 400      | Metadatos, fechas, etiquetas secundarias   |
| `text-xs`    | `12px`   | `16px` (1.33) | 500      | Overlines, captions, badges                |
| `text-code`  | `14px`   | `20px` (1.43) | 400      | Bloques de código, comandos, variables     |

### Letter Spacing Adjustments

- **Hero / Display headings:** `-0.02em` (tight) para títulos de gran formato.
- **Overlines & captions:** `+0.04em` (wide) + `uppercase` cuando funcionan como etiquetas.
- **Body text:** `0` (default) — no modificar.

### Responsive Scale

| Breakpoint | Hero     | H1     | H2     | H3     | Body   |
| ---------- | -------- | ------ | ------ | ------ | ------ |
| ≥ 1024px   | `48px`   | `40px` | `32px` | `24px` | `16px` |
| 768–1023px | `40px`   | `32px` | `28px` | `22px` | `16px` |
| < 768px    | `32px`   | `28px` | `24px` | `20px` | `16px` |

---

## Border Radius

| Token        | Value      | Tailwind Class | Uso                                                           |
| ------------ | ---------- | -------------- | ------------------------------------------------------------- |
| `radius-sm`  | `4px`      | `rounded-sm`   | Badges de tecnología, chips, bloques de código inline         |
| `radius-md`  | `8px`      | `rounded-md`   | Botones, inputs, selects, formularios de registro             |
| `radius-lg`  | `10px`     | `rounded-lg`   | (Variable base de shadcn/ui)                                  |
| `radius-xl`  | `12px`     | `rounded-xl`   | Tarjetas secundarias, contenedores de features                |
| `radius-2xl` | `16px`     | `rounded-2xl`  | Tarjetas de speakers, agenda items, bloques destacados        |
| `radius-full`| `9999px`   | `rounded-full` | Avatares de speakers, píldoras de estado, badges circulares   |

**Regla:** Cualquier radio que no sea `sm`, `md`, o `full` debe estar justificado por el contexto del componente. Para botones e inputs siempre usar `8px`; para avatares siempre `9999px`.

---

## Spacing Grid

Toda la distribución espacial se rige por múltiplos de **8px**. No se deben usar valores arbitrarios.

### Base Multiples

| Token  | Value | Uso típico                                              |
| ------ | ----- | ------------------------------------------------------- |
| `1`    | 8px   | Espaciado mínimo entre ícono y texto, gap de badges     |
| `2`    | 16px  | Padding interno de tarjetas, gap de listas              |
| `3`    | 24px  | Padding horizontal de contenedor, gap entre columnas    |
| `4`    | 32px  | Gap entre secciones en mobile                           |
| `6`    | 48px  | Margin-bottom de títulos de sección                     |
| `8`    | 64px  | Padding vertical entre secciones principales (desktop)  |
| `12`   | 96px  | Hero section padding vertical                           |
| `16`   | 128px | Separación de mega-secciones (footer, pre-footer)       |

### Layout Tokens

| Token                 | Value    | Descripción                                                |
| --------------------- | -------- | ---------------------------------------------------------- |
| `container-max-width` | `1200px` | Ancho máximo del contenido principal                       |
| `container-padding-x` | `24px`   | Padding horizontal interno del contenedor                  |
| `section-padding-y`   | `64px`   | Espaciado vertical entre secciones (32px en mobile)        |
| `section-gap`         | `48px`   | Separación entre título de sección y su contenido          |
| `card-padding`        | `24px`   | Padding interno uniforme para todas las tarjetas           |
| `card-gap`            | `24px`   | Gap entre tarjetas en grid layout                          |

### Grid Columns

Las secciones de contenido usan un grid de 12 columnas con gap de `24px`:

```
|  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |  9  | 10  | 11  | 12  |
```

- **Hero content:** 6 columnas centradas (col-start-4 a col-end-10)
- **Speaker grid:** 3 columnas (4 cols cada una) en desktop, 1 columna en mobile
- **Agenda / Timeline:** 8 columnas centradas

---

## Component Specs

### 1. CTA Button (Primary)

El botón principal de llamado a la acción para registro y acciones prioritarias.

| Property              | Value                                                   |
| --------------------- | ------------------------------------------------------- |
| **Background**        | `#1A73E8` (Google Blue)                                 |
| **Text**              | `#FFFFFF`, weight 500 (Medium), size 16px               |
| **Border Radius**     | `8px`                                                   |
| **Padding**           | `12px 24px` (48px height total)                         |
| **Min Width**         | `160px`                                                 |

#### States

| State      | Visual                                                   | Duration |
| ---------- | -------------------------------------------------------- | -------- |
| **Rest**   | `bg-[#1A73E8] text-white rounded-md`                     | —        |
| **Hover**  | `bg-[#1557B0] translate-y-[-2px] shadow-md`              | `200ms ease-out` |
| **Active** | `bg-[#1557B0] translate-y-0 shadow-sm scale-[0.98]`      | `100ms ease-out` |
| **Focus**  | `ring-2 ring-[#1A73E8]/40 ring-offset-2`                 | `0ms` (instant)  |
| **Disabled** | `bg-[#DADCE0] text-[#5F6368] cursor-not-allowed`      | —        |

```css
/* Reference implementation */
.btn-primary {
  background: #1A73E8;
  color: #FFFFFF;
  border-radius: 8px;
  padding: 12px 24px;
  font-weight: 500;
  font-size: 16px;
  transition: background 200ms ease-out, transform 200ms ease-out, box-shadow 200ms ease-out;
}
.btn-primary:hover {
  background: #1557B0;
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(26, 115, 232, 0.25);
}
.btn-primary:active {
  transform: translateY(0) scale(0.98);
  box-shadow: 0 2px 6px rgba(26, 115, 232, 0.15);
}
```

---

### 2. CTA Button (Secondary / Outline)

Para acciones secundarias como "Ver agenda" o "Conocer más".

| Property              | Value                                                   |
| --------------------- | ------------------------------------------------------- |
| **Background**        | Transparent                                             |
| **Border**            | `1px solid #DADCE0`                                     |
| **Text**              | `#1A73E8`, weight 500, size 16px                        |
| **Border Radius**     | `8px`                                                   |
| **Padding**           | `12px 24px`                                             |

#### States

| State      | Visual                                                   |
| ---------- | -------------------------------------------------------- |
| **Rest**   | `border border-[#DADCE0] text-[#1A73E8] rounded-md`      |
| **Hover**  | `bg-[#1A73E8]/5 border-[#1A73E8] translate-y-[-2px]`     |
| **Active** | `bg-[#1A73E8]/10 translate-y-0 scale-[0.98]`              |
| **Focus**  | `ring-2 ring-[#1A73E8]/40 ring-offset-2`                  |

---

### 3. Speaker Card

Tarjeta de presentación para cada ponente del evento.

| Property              | Value                                                   |
| --------------------- | ------------------------------------------------------- |
| **Background**        | `#FFFFFF`                                               |
| **Border**            | `1px solid #DADCE0`                                     |
| **Border Radius**     | `16px`                                                  |
| **Padding**           | `24px`                                                  |
| **Width**             | 100% (dentro de grid column)                            |
| **Shadow (rest)**     | `none` — la tarjeta es completamente plana en reposo    |

#### Hover State

| Property             | Value                                  | Duration       |
| -------------------- | -------------------------------------- | -------------- |
| **Transform**        | `translateY(-4px)`                     | `300ms ease`   |
| **Box Shadow**       | `0 8px 30px rgba(0, 0, 0, 0.08)`      | `300ms ease`   |
| **Border Color**     | `#1A73E8` (cambia a azul Google)       | `300ms ease`   |

```css
.speaker-card {
  background: #FFFFFF;
  border: 1px solid #DADCE0;
  border-radius: 16px;
  padding: 24px;
  transition: transform 300ms ease, box-shadow 300ms ease, border-color 300ms ease;
}
.speaker-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.08);
  border-color: #1A73E8;
}
```

#### Card Internal Layout

```
┌──────────────────────────────┐
│  ┌──────┐                    │   Avatar: 80x80px, rounded-full
│  │      │  Nombre Completo   │   Name: text-h3, weight 600, color #202124
│  │      │  Cargo · Empresa   │   Role: text-sm, weight 400, color #5F6368
│  └──────┘                    │
│                              │
│  Bio descriptiva del speaker │   Bio: text-body, weight 400, color #5F6368
│  en 2-3 líneas máximo...     │
│                              │
│  ┌────────┐ ┌────────┐       │   Topic badges: radius-sm, bg-surface
│  │  GenAI  │ │ Vertex │       │
│  └────────┘ └────────┘       │
└──────────────────────────────┘
```

---

### 4. Registration Form Input

Campos del formulario de registro al evento.

| Property              | Value                                                   |
| --------------------- | ------------------------------------------------------- |
| **Background**        | `#FFFFFF`                                               |
| **Border**            | `1px solid #DADCE0`                                     |
| **Border Radius**     | `8px`                                                   |
| **Padding**           | `12px 16px`                                             |
| **Text**              | `16px`, weight 400, color `#202124`                     |
| **Placeholder**       | `16px`, weight 400, color `#5F6368`                     |
| **Height**            | `48px`                                                  |

#### States

| State       | Visual                                                    | Duration |
| ----------- | --------------------------------------------------------- | -------- |
| **Rest**    | `border-[#DADCE0] bg-white`                               | —        |
| **Hover**   | `border-[#5F6368]`                                        | `150ms`  |
| **Focus**   | `border-[#1A73E8] ring-[3px] ring-[#1A73E8]/20`           | `150ms`  |
| **Error**   | `border-[#EA4335] ring-[3px] ring-[#EA4335]/20`           | `150ms`  |
| **Success** | `border-[#34A853]`                                         | `150ms`  |
| **Disabled**| `bg-[#F8F9FA] text-[#5F6368] cursor-not-allowed`          | —        |

---

### 5. Navigation Bar

Barra de navegación fija superior.

| Property              | Value                                                   |
| --------------------- | ------------------------------------------------------- |
| **Background**        | `#FFFFFF` con `backdrop-filter: blur(12px)` al hacer scroll |
| **Border Bottom**     | `1px solid #DADCE0` (solo cuando hay scroll)            |
| **Height**            | `64px`                                                  |
| **Padding X**         | `24px`                                                  |

#### Nav Link States

| State      | Visual                                                     |
| ---------- | ---------------------------------------------------------- |
| **Rest**   | `text-[#5F6368] text-sm font-medium`                       |
| **Hover**  | `text-[#1A73E8]`                                           |
| **Active** | `text-[#1A73E8]` con indicador inferior de 2px `bg-[#1A73E8]` |

---

### 6. Agenda / Timeline Item

Elemento de la línea de tiempo del evento.

| Property              | Value                                                   |
| --------------------- | ------------------------------------------------------- |
| **Background**        | `#FFFFFF`                                               |
| **Border Left**       | `2px solid #1A73E8` (marcador de timeline)              |
| **Border Radius**     | `16px`                                                  |
| **Padding**           | `24px`                                                  |
| **Dot Indicator**     | Círculo de 12px `bg-[#1A73E8]` posicionado a la izquierda |

---

### 7. Hero Section

Sección principal de apertura.

| Property              | Value                                                   |
| --------------------- | ------------------------------------------------------- |
| **Background**        | `#FFFFFF`                                               |
| **Padding Y**         | `128px` desktop / `80px` mobile                         |
| **Text Align**        | Center                                                  |
| **Max Width**         | `800px` contenido centrado                              |

**Hero Badge (evento oficial):** `bg-[#1A73E8]/10 text-[#1A73E8] text-xs font-medium uppercase tracking-wider rounded-full px-3 py-1`

---

## Do's and Don'ts

### Colors

| Do ✅                                                                     | Don't ❌                                                                          |
| ------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| Usa `#1A73E8` (Google Blue) como color dominante para toda acción primaria | Usar Google Red o Yellow para botones CTA principales                             |
| Usa `#202124` para texto de cuerpo y títulos                              | Usar `#000000` puro para ningún texto; causa fatiga visual y se ve amateur       |
| Combina los 4 colores Google con moderación (máx. 2 acentos por sección)  | Saturar una sección con los 4 colores simultáneamente                             |
| Usa `#34A853` exclusivamente para confirmaciones y estados de éxito       | Usar verde para botones de navegación o acciones genéricas                        |
| Mantén el fondo blanco (`#FFFFFF`) como default de página                 | Usar fondos oscuros o degradados como base de la landing                          |

### Typography

| Do ✅                                                                     | Don't ❌                                                                          |
| ------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| Respeta la escala tipográfica definida sin desviaciones                   | Usar más de 3 tamaños de fuente diferentes en una misma sección                  |
| Usa `font-weight: 500` para botones y elementos interactivos              | Usar `font-weight: 300` (Light) en párrafos; no tiene suficiente contraste        |
| Mantén `uppercase` solo en overlines de 12px                              | Poner botones, labels o títulos completos en mayúsculas                           |
| Usa `letter-spacing: -0.02em` solo en Hero/Display headings               | Aplicar letter-spacing negativo a texto de cuerpo                                |

### Border Radius

| Do ✅                                                                     | Don't ❌                                                                          |
| ------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| Usa exactamente `8px` para todos los botones e inputs                     | Mezclar radios diferentes en botones de la misma jerarquía                        |
| Usa `16px` para tarjetas principales (speakers, agenda)                   | Usar radios >16px en tarjetas que contengan texto e imágenes                      |
| Usa `9999px` (rounded-full) solo en avatares y pills                      | Usar `rounded-full` en botones rectangulares o tarjetas                           |
| Mantén consistencia: mismo radio para mismo tipo de componente            | Variar el radio "porque se ve mejor" sin razón de sistema                         |

### Spacing

| Do ✅                                                                     | Don't ❌                                                                          |
| ------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| Todo espaciado debe ser múltiplo de `8px`                                 | Usar valores como `7px`, `13px`, `22px`, `31px`                                   |
| Usa `64px` de padding vertical entre secciones en desktop                 | Usar `60px` o `70px` por ajuste visual; respeta la grilla                         |
| Padding interno de tarjetas siempre `24px`                                | Variar el padding de tarjetas del mismo tipo entre secciones                      |
| Gap de grid siempre `24px`                                                | Usar `gap-5` (20px) o `gap-7` (28px) en la misma página                          |

### Components

| Do ✅                                                                     | Don't ❌                                                                          |
| ------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| Las tarjetas de speaker NO tienen sombra en reposo (diseño plano)         | Usar `box-shadow` permanente en tarjetas; solo debe aparecer en hover             |
| El hover de botones debe incluir `translateY(-2px)` con transición suave  | Usar `scale()` en hover de botones primarios; se ve inestable                     |
| El borde de las tarjetas en hover cambia a azul Google (`#1A73E8`)        | Dejar el borde gris en hover; pierde feedback visual                              |
| La navbar debe tener backdrop-blur solo después de scroll                 | Aplicar backdrop-blur permanente cuando la navbar está en el top                  |
| El foco de inputs debe tener un anillo azul sutil de 3px                  | Usar outlines del navegador por defecto sin estilizar                             |

### Motion

| Do ✅                                                                     | Don't ❌                                                                          |
| ------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| Transiciones de hover: `200-300ms ease-out`                               | Usar duraciones menores a 150ms (se siente brusco) o mayores a 500ms (se siente lento) |
| Usa `ease-out` para entradas y `ease-in` para salidas                     | Usar `linear` para transiciones interactivas                                      |
| Las tarjetas de speaker usan `300ms ease` por el efecto de elevación      | Usar la misma duración para hover de botones y tarjetas (son micro-interacciones diferentes) |

---

## Implementation Notes

### Tailwind CSS v4 (shadcn/ui) Alignment

El proyecto utiliza Tailwind CSS v4 con variables CSS de shadcn/ui. Para implementar este design system se recomienda:

1. **Extender el tema** en `src/index.css` agregando los tokens de color Google como custom properties dentro de `@theme inline { }`:

```css
@theme inline {
  /* Google brand colors */
  --color-gblue:        #1A73E8;
  --color-gblue-hover:  #1557B0;
  --color-gred:         #EA4335;
  --color-gyellow:      #FBBC05;
  --color-ggreen:       #34A853;

  /* Neutral overrides */
  --color-surface:       #F8F9FA;
  --color-text-muted:    #5F6368;
}
```

2. **Clases utilitarias disponibles** tras la extensión:
   - `bg-gblue`, `text-gblue`, `border-gblue`, `ring-gblue`
   - `bg-surface`, `text-text-muted`

3. **La fuente Open Sans** ya está importada y configurada como `--font-sans`. No se requieren cambios adicionales.

4. **El sistema de border-radius** de shadcn (basado en `--radius: 0.625rem`) es compatible; los valores de este documento (`4px`, `8px`, `16px`) se mapean a `rounded-sm`, `rounded-md`, `rounded-2xl` respectivamente.

5. **Componentes shadcn/ui** como `Button`, `Input`, `Card` deben ser wrappeados o estilizados directamente con las clases de color Google definidas en este documento, sobrescribiendo los defaults neutrales de shadcn donde corresponda.

---

## Changelog

| Date       | Version | Description                    |
| ---------- | ------- | ------------------------------ |
| 2026-06-25 | 1.0.0   | Initial design system release  |
