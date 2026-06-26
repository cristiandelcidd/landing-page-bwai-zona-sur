# Mis Apuntes de Prompts

# Prompt: Generación de PRD.md (Desde Cero)

> Actúa como un Product Manager técnico. Genera el archivo `./PRD.md` (Product Requirements Document) para una Landing Page de un evento tecnológico llamado 'Build with AI' de GDG Choluteca. El documento debe definir en Markdown limpio la visión del producto, objetivos de conversión, público objetivo, y los requisitos funcionales detallados de sus secciones clave: un Navbar con efecto blur, una sección Hero con llamados a la acción, una cuadrícula para el perfil de los Speakers, una Agenda en formato de línea de tiempo y un Formulario de registro con validaciones de estado. Guarda el resultado directamente en el archivo.

## Prompt para crear el DESIGN.md:

> Actúa como un Diseñador de Sistemas UI. Genera un archivo `./design.md` para la Landing Page de un evento de Google llamado 'Build with AI'. Usa un estilo limpio y moderno (estilo GDG) e incluye secciones detalladas de: Colors (con HEX reales de Google), Typography (con fuentes web y escala), Border Radius, Component Specs (comportamiento hover de botones y tarjetas de speakers), Spacing Grid (múltiplos de 8px) y Do's and Don'ts de validación. Guarda el resultado directamente en el archivo.

## Prompt inicial para maquetar la interfaz en Stitch:

> Quiero que crees una landing page para el evento Build With AI Zona Sur en Choluteca, se está llevando a cabo en UNAH Campus Choluteca, quiero que incluyas los estilos, tipografia y espaciados definidos en el design.md

# Prompt: Rediseño, Verificación y Update de DESIGN.md

> Actúa como un desarrollador frontend. El diseño actual de la UI no me gusta del todo. Usa la skill `frontend-design` para renovar por completo la interfaz, incluyendo fuentes, colores, estilos y todo lo demás. Luego, levanta el proyecto localmente para verificar que todo esté funcionando de forma correcta en el navegador. Una vez que termines, actualiza el archivo `design.md`.