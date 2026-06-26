# PRD — Build with AI Landing Page

> **Documento de Requisitos de Producto**
> Evento oficial · GDG Choluteca · Build with AI Zona Sur
>
> Versión 1.0 — Junio 2026

---

## Tabla de Contenidos

1. [Resumen Ejecutivo](#resumen-ejecutivo)
2. [Visión del Producto](#visión-del-producto)
3. [Objetivos de Negocio y Métricas de Éxito](#objetivos-de-negocio-y-métricas-de-éxito)
4. [Público Objetivo](#público-objetivo)
5. [Recorrido del Usuario](#recorrido-del-usuario)
6. [Requisitos Funcionales](#requisitos-funcionales)
   - [FR-01: Navbar](#fr-01-navbar)
   - [FR-02: Sección Hero](#fr-02-sección-hero)
   - [FR-03: Cuadrícula de Ponentes](#fr-03-cuadrícula-de-ponentes)
   - [FR-04: Línea de Tiempo de la Agenda](#fr-04-línea-de-tiempo-de-la-agenda)
   - [FR-05: Formulario de Registro](#fr-05-formulario-de-registro)
7. [Requisitos No Funcionales](#requisitos-no-funcionales)
8. [Fuera de Alcance](#fuera-de-alcance)
9. [Preguntas Abiertas](#preguntas-abiertas)
10. [Glosario](#glosario)

---

## Resumen Ejecutivo

**Build with AI** es un evento presencial organizado por **GDG Choluteca** enfocado en inteligencia artificial aplicada al desarrollo de software. La landing page es el punto de entrada único para la audiencia: comunica la propuesta de valor del evento, presenta a los speakers, exhibe la agenda y —críticamente— convierte visitantes en asistentes registrados.

El proyecto se construye sobre **React 19 + TypeScript + Tailwind CSS v4 + shadcn/ui**, desplegado como sitio estático. Este PRD define el alcance funcional completo de la landing page.

---

## Visión del Producto

Ser la referencia regional de eventos tecnológicos comunitarios: una landing page que, en menos de 5 segundos, le comunique a un desarrollador exactamente qué va a aprender, quién se lo va a enseñar, cuándo ocurre y cómo asegurar su lugar — todo con la identidad visual limpia y moderna de Google Developer Groups.

**Principios rectores:**

1. **Velocidad perceptual** — El Hero debe resolver "¿qué es esto y por qué me importa?" sin scroll.
2. **Confianza por transparencia** — Speakers reales con foto, nombre real, y bio real. Sin placeholder genérico.
3. **Fricción mínima para conversión** — El formulario de registro debe ser el camino más corto posible entre el interés y la acción.
4. **GDG auténtico** — La identidad visual debe sentirse nativa de Google Developer Groups, no un template genérico.

---

## Objetivos de Negocio y Métricas de Éxito

### Objetivo primario

| Objetivo              | Métrica                                    | Meta        |
| --------------------- | ------------------------------------------ | ----------- |
| **Registros**         | Número de formularios completados y enviados | ≥ 150       |
| **Tasa de conversión** | Visitantes únicos → Registros completados   | ≥ 12%       |

### Objetivos secundarios

| Objetivo              | Métrica                                    | Meta        |
| --------------------- | ------------------------------------------ | ----------- |
| **Tiempo en página**  | Duración media de sesión                   | ≥ 90s       |
| **Scroll depth**      | % de usuarios que llegan a Agenda y Form   | ≥ 60%       |
| **Click-through CTA** | Clicks en botón de registro del Hero       | ≥ 40%       |
| **Compromiso social** | Clicks en links de redes sociales de GDG   | ≥ 10%       |
| **Rebote**            | Tasa de rebote                             | ≤ 35%       |

---

## Público Objetivo

### Perfiles de usuario

| Persona                       | Necesidad principal                       | Expectativa visual                        |
| ----------------------------- | ----------------------------------------- | ----------------------------------------- |
| **Dev Jr / Estudiante**       | Aprender IA aplicada, networking          | Lenguaje claro, no abrumador, seguro      |
| **Dev Sr / Profesional**      | Mantenerse al día, evaluar nivel del evento | Contenido técnico visible rápido          |
| **Organizador GDG / Sponsor** | Validar calidad y alcance del evento      | Profesionalismo, consistencia con GDG     |
| **Speaker invitado**          | Ver cómo será presentada su participación | Perfil bien diseñado, foto destacada      |

### Contexto de uso

- **Dispositivo principal:** Móvil (60%) y Desktop (40%) — estimado por ser un evento promocionado en redes sociales y grupos de WhatsApp/Telegram.
- **Conexión:** Predominantemente 4G/LTE. La página debe cargar en ≤ 3s en conexiones móviles.
- **Idioma:** Español (con términos técnicos en inglés donde sea necesario).

---

## Recorrido del Usuario

```
┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐
│  Llega   │───▶│  Hero    │───▶│ Speakers │───▶│  Agenda  │───▶│ Registro │
│ (link)   │    │ (scroll) │    │ (scroll) │    │ (scroll) │    │ (envío)  │
└──────────┘    └──────────┘    └──────────┘    └──────────┘    └──────────┘
                      │                                              │
                      │               ┌──────────┐                  │
                      └──────────────▶│ Registro │◀─────────────────┘
                        (CTA directo) │  (CTA)   │   (CTA al final
                                      └──────────┘    de Agenda)
```

1. **Touchpoint 1 — Link entrante:** El usuario hace clic en un link de Instagram, WhatsApp, LinkedIn o email.
2. **Touchpoint 2 — Hero (0–5s):** Decide si el evento es relevante. Ve fecha, lugar, título y botón CTA.
3. **Touchpoint 3 — Speakers (5–15s):** Evalúa la credibilidad del evento por quiénes presentan.
4. **Touchpoint 4 — Agenda (15–30s):** Confirma que los temas son de su interés.
5. **Touchpoint 5 — Registro (30–60s):** Completa el formulario y recibe confirmación.

**CTAs distribuidos:** Hero (primario) + sección sticky al final de Agenda (secundario). Ambos apuntan al formulario de registro, ya sea en página (ancla) o como sección visible al final.

---

## Requisitos Funcionales

### FR-01: Navbar

**Propósito:** Navegación fija con identidad de marca, accesos rápidos a secciones clave y efecto visual de profundidad al hacer scroll.

#### Requisitos

| ID      | Requisito                                                                 |
| ------- | ------------------------------------------------------------------------- |
| FR-01.1 | La navbar debe estar fija en la parte superior (`position: sticky`) durante todo el scroll. |
| FR-01.2 | Debe mostrar el logo/texto "Build with AI" alineado a la izquierda.       |
| FR-01.3 | Debe incluir enlaces de navegación interna (anclas) a: Hero, Speakers, Agenda, Registro. |
| FR-01.4 | El link correspondiente a la sección visible en viewport debe marcarse como activo. |
| FR-01.5 | En estado inicial (top of page, scrollY = 0), el fondo debe ser **transparente** y sin borde inferior. |
| FR-01.6 | Al hacer scroll pasados 50px, debe aplicarse un **efecto blur**: `backdrop-filter: blur(12px)` con fondo semi-transparente (`rgba(255,255,255,0.85)`) y borde inferior `1px solid #DADCE0`. |
| FR-01.7 | La transición entre estado transparente y blur debe ser suave: `transition: background 300ms ease, backdrop-filter 300ms ease, border-color 300ms ease`. |
| FR-01.8 | En mobile (≤ 768px), los links de navegación deben colapsar en un menú hamburguesa tipo *sheet* o *drawer* que se despliega desde la derecha. |
| FR-01.9 | El botón de registro/navbar debe mantener el estilo de CTA primario (Google Blue) para consistencia visual. |
| FR-01.10| La navbar debe tener una altura fija de `64px` sin cambios en ningún breakpoint. |

#### Estados

| Estado              | Comportamiento visual                                                     |
| ------------------- | ------------------------------------------------------------------------- |
| **Top (scrollY=0)** | Fondo transparente, sin borde, sin blur                                   |
| **Scrolled (>50px)** | Fondo `rgba(255,255,255,0.85)`, blur 12px, borde `#DADCE0`               |
| **Mobile open**     | Drawer lateral derecho con fondo blanco sólido, links en columna          |
| **Link active**     | Texto `#1A73E8` con indicador inferior de 2px `bg-[#1A73E8]`             |

---

### FR-02: Sección Hero

**Propósito:** Comunicar en ≤ 5 segundos la propuesta de valor del evento y proveer el CTA principal de registro.

#### Requisitos

| ID      | Requisito                                                                 |
| ------- | ------------------------------------------------------------------------- |
| FR-02.1 | La sección debe ocupar al menos `100vh` (viewport height completa) en desktop. En mobile puede ser `auto` con padding suficiente para no forzar scroll lateral. |
| FR-02.2 | Debe mostrar un **badge oficial** tipo píldora: texto `"Evento Oficial GDG"` sobre fondo `#1A73E8/10` con texto `#1A73E8`, tamaño 12px, `uppercase`, `font-weight: 500`, `letter-spacing: +0.04em`. |
| FR-02.3 | Debe contener el **título principal**: "Build with AI" con la palabra "AI" estilizada con el color Google Blue (`#1A73E8`) para énfasis. Tamaño 48px en desktop (32px mobile), weight 700. |
| FR-02.4 | Debe contener un **subtítulo descriptivo** de máximo 2 líneas: combina el nombre del evento regional más el valor para el asistente. Ej: "El evento de inteligencia artificial para developers de la Zona Sur". Tamaño 18px, weight 400, color `#5F6368`. |
| FR-02.5 | Debe mostrar **metadatos del evento** en formato de chips o línea horizontal: Fecha, Hora, Lugar (nombre de venue + ciudad). Cada ítem con ícono de Lucide alineado a la izquierda. |
| FR-02.6 | Debe contener un **botón CTA primario**: texto "Registrarse Gratis", estilizado según spec de diseño (Google Blue, 8px radius, 48px height). |
| FR-02.7 | Debe contener un **botón CTA secundario**: texto "Ver Agenda", estilo outline. |
| FR-02.8 | Ambos CTAs deben apuntar al formulario de registro: el primario con scroll suave a la sección, el secundario con scroll suave a la agenda y luego al formulario. |
| FR-02.9 | Todo el contenido del Hero debe estar centrado horizontal y verticalmente. |
| FR-02.10| El Hero debe tener un **elemento visual decorativo** (formas geométricas sutiles o gradientes suaves con los colores Google) que refuercen la identidad sin distraer del texto. |

#### Estados

| Estado            | Comportamiento visual                                                     |
| ----------------- | ------------------------------------------------------------------------- |
| **Default**       | Texto animado con fade-in desde opacidad 0 al cargar la página            |
| **Botón hover**   | Blue → Blue oscuro, translateY(-2px), shadow azul sutil (ver design.md)   |
| **Botón active**  | scale(0.98), sin translateY                                               |

---

### FR-03: Cuadrícula de Ponentes

**Propósito:** Presentar a los ponentes del evento con credibilidad, generando confianza en la calidad del contenido. No deben usarse placeholders.

#### Requisitos

| ID      | Requisito                                                                 |
| ------- | ------------------------------------------------------------------------- |
| FR-03.1 | La sección debe tener un título de sección: "Speakers" o "Ponentes".      |
| FR-03.2 | Los speakers deben mostrarse en un **grid responsive**: 3 columnas en desktop (≥1024px), 2 columnas en tablet (768–1023px), 1 columna en mobile (<768px). |
| FR-03.3 | El gap entre tarjetas debe ser de `24px` consistente en todos los breakpoints. |
| FR-03.4 | Cada tarjeta de speaker debe contener:                                   |
|         | - **Avatar:** Imagen del speaker, `80×80px`, `border-radius: 9999px`, centrada o alineada a la izquierda del contenido. |
|         | - **Nombre completo:** Tamaño 20px, weight 600, color `#202124`.          |
|         | - **Rol y empresa:** Formato "Rol · @Empresa". Tamaño 14px, weight 400, color `#5F6368`. |
|         | - **Bio:** Máximo 3 líneas de texto descriptivo. Tamaño 14px, weight 400, color `#5F6368`. |
|         | - **Topic badges:** 1–3 chips pequeños con los temas de la charla (ej: "GenAI", "Vertex AI", "Gemini"). Background `#F8F9FA`, texto `#1A73E8`, `border-radius: 4px`, padding `4px 8px`, tamaño 12px. |
| FR-03.5 | Los datos de los speakers deben provenir de un **archivo de datos estructurado** (ej: `src/data/speakers.ts`) que contenga un array tipado con los campos: `id, name, role, company, bio, topics, avatarUrl`. |
| FR-03.6 | Si un speaker no tiene `avatarUrl`, se debe mostrar un placeholder con las iniciales del nombre sobre fondo `#1A73E8/10` y texto `#1A73E8`. |
| FR-03.7 | Si el array de speakers está vacío, la sección no debe renderizarse (no mostrar sección vacía). |
| FR-03.8 | La tarjeta debe ser completamente **plana en reposo** (sin box-shadow) y solo aplicar elevación en hover (ver diseño). |
| FR-03.9 | El hover debe aplicar: `translateY(-4px)`, `box-shadow: 0 8px 30px rgba(0,0,0,0.08)`, `border-color: #1A73E8`. Transición de 300ms ease. |
| FR-03.10| Las tarjetas deben ser **interactivas al 100% de su superficie** (todo el card es clickeable/hoverable, no solo el avatar). |

#### Casos Límite

| Caso                         | Comportamiento                                                           |
| ---------------------------- | ------------------------------------------------------------------------ |
| 1 speaker                    | Tarjeta centrada, ancho máximo 400px                                     |
| 2 speakers                   | Layout de 2 columnas centradas                                           |
| Imagen de avatar no carga    | Fallback a iniciales del nombre                                          |
| Bio muy larga (>3 líneas)    | Truncar con `line-clamp-3` y ellipse                                    |
| Topics >3                    | Mostrar los primeros 3 y un badge "+N más"                              |

---

### FR-04: Línea de Tiempo de la Agenda

**Propósito:** Comunicar la estructura cronológica del evento de manera clara y visualmente atractiva.

#### Requisitos

| ID      | Requisito                                                                 |
| ------- | ------------------------------------------------------------------------- |
| FR-04.1 | La sección debe tener un título: "Agenda" o "Cronograma".                 |
| FR-04.2 | Los ítems de la agenda deben mostrarse en formato **línea de tiempo vertical** con un eje central (desktop) o izquierdo (mobile). |
| FR-04.3 | Cada ítem de la línea de tiempo debe contener:                            |
|         | - **Hora:** Formato `HH:MM AM/PM` (ej: "09:00 AM"). Tamaño 16px, weight 600, color `#1A73E8`. |
|         | - **Título de la actividad:** Tamaño 18px, weight 600, color `#202124`.   |
|         | - **Descripción:** Tamaño 14px, weight 400, color `#5F6368`. Máximo 2 líneas. |
|         | - **Tipo de actividad:** Icono + etiqueta (Charla, Workshop, Break, Keynote). |
|         | - **Speaker asociado (opcional):** Nombre del speaker con avatar pequeño de 24px. |
| FR-04.4 | El **nodo de timeline** debe ser un círculo de `12px` con borde `2px solid #1A73E8` y fondo blanco. Para ítems pasados (si aplica), fondo `#1A73E8` sólido. |
| FR-04.5 | La **línea conectora** entre nodos debe ser de `2px` de ancho, color `#DADCE0`. En desktop, la línea pasa por el centro; los ítems se alternan izquierda-derecha. |
| FR-04.6 | Los ítems deben alternarse a izquierda y derecha del eje en desktop (≥768px). En mobile, todos los ítems van alineados a la izquierda con el eje a la izquierda. |
| FR-04.7 | Los datos de la agenda deben provenir de un archivo de datos estructurado (ej: `src/data/agenda.ts`) con tipo `AgendaItem` conteniendo: `id, time, title, description, type ('talk' | 'workshop' | 'break' | 'keynote'), speakerId (opcional)`. |
| FR-04.8 | Los ítems deben renderizarse en **orden cronológico** según el campo `time`. |
| FR-04.9 | Si no hay ítems en la agenda, mostrar un mensaje: "Agenda próximamente — mantente atento." |
| FR-04.10| Debe haber un **botón CTA al final** de la sección Agenda: "Registrarse Gratis" que haga scroll suave hacia el formulario de registro. |

#### Estados Visuales

| Estado         | Comportamiento visual                                                     |
| -------------- | ------------------------------------------------------------------------- |
| **Default**    | Ítems con opacidad 1, nodos con fondo blanco y borde azul                |
| **Hover ítem** | Fondo del ítem cambia a `#F8F9FA` sutilmente (transición 200ms)           |
| **Break item** | Nodo con borde `#FBBC05` (amarillo) en lugar de azul; texto más pequeño   |
| **Keynote**    | Nodo con borde `#EA4335` (rojo) para destacar                             |

#### Casos Límite

| Caso                         | Comportamiento                                                           |
| ---------------------------- | ------------------------------------------------------------------------ |
| Agenda vacía                 | Mostrar estado placeholder: "Agenda próximamente"                        |
| Actividad sin speaker        | Omitir el avatar y nombre del speaker; mostrar solo título y hora        |
| Ítem de tipo "break"         | Estilo visual diferenciado: nodo amarillo, sin descripción extensa       |
| Título muy largo             | Truncar a 2 líneas con `line-clamp-2`                                    |

---

### FR-05: Formulario de Registro

**Propósito:** Capturar los datos del asistente con la menor fricción posible, validando en tiempo real y confirmando el registro exitoso.

#### Requisitos

| ID      | Requisito                                                                 |
| ------- | ------------------------------------------------------------------------- |
| FR-05.1 | La sección debe tener un título: "Regístrate" o "Asegura tu lugar".       |
| FR-05.2 | El formulario debe contener los siguientes campos:                        |
|         | - **Nombre completo** (texto, requerido)                                  |
|         | - **Email** (email, requerido, validación de formato)                     |
|         | - **Nivel de experiencia** (select, requerido, opciones: "Estudiante", "Junior", "Mid-level", "Senior", "No soy developer") |
|         | - **¿Cómo te enteraste?** (select, opcional, opciones: "Redes sociales", "WhatsApp/Telegram", "Un amigo/compañero", "GDG Choluteca", "Otro") |
| FR-05.3 | Todos los campos requeridos deben marcarse visualmente con un asterisco `*` en color `#EA4335`. |
| FR-05.4 | **Validación en tiempo real (onBlur):** Cada campo debe validarse al perder el foco, mostrando el mensaje de error correspondiente debajo del input. |
| FR-05.5 | Reglas de validación:                                                     |
|         | - **Nombre:** Mínimo 3 caracteres. No se permiten solo espacios. Mensaje: "El nombre debe tener al menos 3 caracteres." |
|         | - **Email:** Debe cumplir patrón `^[^\s@]+@[^\s@]+\.[^\s@]+$`. Mensaje: "Ingresa un email válido." |
|         | - **Nivel de experiencia:** Debe seleccionar una opción. Mensaje: "Selecciona tu nivel de experiencia." |
| FR-05.6 | El botón de envío debe permanecer **deshabilitado** (`disabled`) hasta que todos los campos requeridos sean válidos. |
| FR-05.7 | Al hacer clic en "Enviar" (o "Registrarme"), se debe simular el envío con un **delay artificial de 1–1.5s** (loading state en el botón con spinner y texto "Registrando..."). |
| FR-05.8 | Al completar el "envío" exitosamente:                                     |
|         | - Reemplazar el formulario con un **mensaje de confirmación**: ícono de check (Google Green `#34A853`), título "¡Registro exitoso!" y subtítulo "Te esperamos en Build with AI. Revisa tu email para más detalles." |
|         | - Mostrar un toast de confirmación (usar `sonner`).                       |
| FR-05.9 | Si ocurre un error en el envío (simulado):                                |
|         | - Mostrar mensaje de error genérico debajo del botón: "Ocurrió un error. Intenta de nuevo." |
|         | - El formulario debe permanecer con los datos ingresados (no limpiar).    |
| FR-05.10| Al hacer clic en "Limpiar" o botón secundario "Cancelar": limpiar todos los campos y resetear estados de validación. |
| FR-05.11| El formulario debe ser **responsive**: en mobile los campos deben ocupar el 100% del ancho. En desktop, nombre y email pueden ir en 2 columnas (50% cada una) y los selects en ancho completo. |
| FR-05.12| Los estados de los inputs deben seguir el diseño establecido (borde gris → borde azul en focus, borde rojo en error, ver design.md FR-04). |

#### Estados del Input

| Estado      | Borde          | Fondo   | Anillo                   | Icono/Mensaje                          |
| ----------- | -------------- | ------- | ------------------------ | -------------------------------------- |
| **Default** | `#DADCE0`      | White   | —                        | Placeholder en gris `#5F6368`          |
| **Focus**   | `#1A73E8`      | White   | `3px #1A73E8/20`         | Label en azul                          |
| **Error**   | `#EA4335`      | White   | `3px #EA4335/20`         | Ícono de alerta + mensaje en rojo      |
| **Success** | `#34A853`      | White   | —                        | Ícono check verde (solo si se usa)     |
| **Disabled**| `#DADCE0`      | `#F8F9FA`| —                       | Texto gris, cursor `not-allowed`       |

#### Estados del Botón de Envío

| Estado        | Visual                                                            |
| ------------- | ----------------------------------------------------------------- |
| **Disabled**  | `bg-[#DADCE0] text-[#5F6368] cursor-not-allowed`                  |
| **Enabled**   | `bg-[#1A73E8] text-white cursor-pointer`                          |
| **Loading**   | `bg-[#1557B0] text-white cursor-wait` con spinner animado         |
| **Hover**     | `bg-[#1557B0] translate-y-[-2px] shadow-md` (solo cuando enabled) |

#### Casos Límite

| Caso                                  | Comportamiento                                                      |
| ------------------------------------- | ------------------------------------------------------------------- |
| Doble clic en enviar                  | El botón debe deshabilitarse durante el loading state               |
| Usuario intenta enviar con campos inválidos | El botón está disabled; no hay acción posible                  |
| Email con espacios al inicio/final    | Trim automático antes de validar y enviar                           |
| Nombre con solo espacios              | Rechazar con mensaje de error específico                            |
| Redimensionar ventana con errores     | Los mensajes de error deben reposicionarse correctamente            |
| Recargar página tras registro exitoso | El formulario debe volver a su estado inicial                       |

---

## Requisitos No Funcionales

| ID     | Categoría         | Requisito                                                                     |
| ------ | ----------------- | ----------------------------------------------------------------------------- |
| NFR-01 | **Performance**   | Lighthouse Performance score ≥ 90 en desktop y ≥ 75 en mobile (3G throttling). |
| NFR-02 | **Performance**   | First Contentful Paint (FCP) ≤ 1.5s, Largest Contentful Paint (LCP) ≤ 2.5s.  |
| NFR-03 | **Performance**   | Total bundle size ≤ 150 KB (gzip) para la ruta principal.                     |
| NFR-04 | **Accessibility** | Lighthouse Accessibility score ≥ 95. Todos los inputs deben tener labels asociados vía `htmlFor`/`id`. |
| NFR-05 | **Accessibility** | Contraste de color mínimo 4.5:1 para texto normal, 3:1 para texto grande (≥18px bold). |
| NFR-06 | **Accessibility** | Navegación completa por teclado (Tab, Enter, Escape para cerrar menú mobile). |
| NFR-07 | **Accessibility** | Atributos `aria-current="page"` en link activo de navbar, `aria-label` en menú hamburguesa, `aria-live="polite"` en mensajes de error del formulario. |
| NFR-08 | **Responsive**    | Diseño funcional y visualmente correcto en viewports desde 320px hasta 1440px+. |
| NFR-09 | **SEO**           | Meta tags: `title`, `description`, `og:title`, `og:description`, `og:image`, `twitter:card`. |
| NFR-10 | **SEO**           | Una sola etiqueta `<h1>` en la página (Hero title). Jerarquía correcta de headings. |
| NFR-11 | **Browser**       | Compatible con últimas 2 versiones de Chrome, Firefox, Safari, Edge.           |
| NFR-12 | **Code Quality**  | TypeScript estricto. Sin errores de lint. Componentes tipados.                  |

---

## Fuera de Alcance

Para esta versión 1.0, los siguientes elementos quedan **explícitamente fuera de alcance**:

| Item                              | Razón                                                                          |
| --------------------------------- | ------------------------------------------------------------------------------ |
| Backend real con base de datos    | Se simula el envío del formulario con delay local. No hay API de registro real. |
| Autenticación / Login             | El registro es abierto, sin cuentas de usuario.                                |
| Pasarela de pago                  | El evento es gratuito. No se requiere procesamiento de pagos.                  |
| Sistema de emails transaccionales | Fuera de alcance inicial; se menciona en mensaje de confirmación como UX copy. |
| Admin panel / Dashboard           | No hay panel para gestionar registros ni speakers en esta fase.                |
| i18n / Multi-idioma               | Solo español en v1.                                                            |
| Animaciones complejas (Framer)    | Solo transiciones CSS y animaciones utilitarias (`tw-animate-css`).            |
| Tests automatizados               | Recomendados pero no requeridos para el MVP del workshop.                      |

---

## Preguntas Abiertas

| # | Pregunta                                                         | Estado      |
|---|------------------------------------------------------------------|-------------|
| 1 | ¿Se requiere un contador regresivo (countdown) en el Hero?       | Por decidir |
| 2 | ¿Habrá un mapa embebido (Google Maps) para la ubicación?         | Por decidir |
| 3 | ¿Se integrará con Google Forms o Firebase para el registro real? | Por decidir |
| 4 | ¿Los speakers tienen links a redes sociales (GitHub, LinkedIn)?  | Por confirmar con speakers |
| 5 | ¿Se necesita una sección de Sponsors/Partners?                   | Por decidir |

---

## Glosario

| Término          | Definición                                                                   |
| ---------------- | ---------------------------------------------------------------------------- |
| **GDG**          | Google Developer Groups — comunidades locales de developers respaldadas por Google. |
| **CTA**          | Call To Action — elemento de interfaz que invita al usuario a realizar una acción (ej: botón de registro). |
| **Hero**         | Sección principal superior de la landing page, visible sin scroll.           |
| **MVP**          | Minimum Viable Product — alcance mínimo funcional para la versión 1.0.       |
| **shadcn/ui**    | Librería de componentes para React basada en Radix UI y Tailwind CSS.        |
| **viewport**     | Área visible del navegador. `100vh` = 100% de la altura del viewport.         |
