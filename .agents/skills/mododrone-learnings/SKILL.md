---
name: mododrone-learnings
description: Base de conocimiento y aprendizajes del proyecto Modo Drone Web. Contiene la arquitectura, convenciones, configuraciones de Git, desglose completo de index.html y registro de evoluciones del proyecto.
---

# Modo Drone Web - Skill de Aprendizajes & Guía del Proyecto

Este documento registra la arquitectura completa, el desglose de secciones, componentes, APIs, diseño y convenciones técnicas de la plataforma web de **Modo Drone** (`index.html`).

---

## 1. Información General del Proyecto
- **Nombre**: Modo Drone | Hub de Operaciones & FPV
- **Repositorio Git**: `https://github.com/Dariobod/mododrone_web.git`
- **Rama Principal**: `main`
- **Archivo Principal**: `index.html` (Single Page Application responsive)

---

## 2. Sistema de Diseño & Estilos Visuales (Design Tokens)

### Estética y Concepto
- **Estilo**: *Apple Dark Modernism* combinado con elementos de *Neón Cyberpunk/Aero*.
- **Efectos principales**:
  - **Glassmorphism**: `background: rgba(28, 28, 30, 0.6); backdrop-filter: saturate(180%) blur(20px); border: 1px solid rgba(255, 255, 255, 0.08);`
  - **Glass Cards**: `background: rgba(40, 40, 42, 0.4); backdrop-filter: blur(10px); border: 1px solid rgba(255, 255, 255, 0.05);`
  - **Glow Effects**: Sombras luminosas en verde neón (`shadow-glow`, `shadow-[0_0_15px_rgba(206,250,3,0.3)]`).

### Paleta de Colores
| Nombre Token | Código Hex / RGBA | Uso / Aplicación |
| :--- | :--- | :--- |
| `apple-bg` | `#000000` | Fondo general de la aplicación |
| `apple-card` | `#1c1c1e` | Fondo de tarjetas, modales y superficies elevadas |
| `apple-text` | `#f5f5f7` | Color de texto principal |
| `apple-gray` | `#86868b` | Texto secundario, subtítulos e iconos inactivos |
| `apple-green` | `#cefa03` | **Color de acento primario (Verde Neón Modo Drone)** |
| `apple-green-gradient` | `from-[#cefa03] to-[#eaff80]` | Gradiente de texto destacado e insignias |
| `glass` | `rgba(28, 28, 30, 0.7)` | Fondo de la Navbar fija |

### Tipografía e Iconografía
- **Fuente Principal**: `Inter` (vía Google Fonts) + fallbacks Sans-Serif (`-apple-system`, `BlinkMacSystemFont`).
- **Iconos**: **FontAwesome 6.4.0** (`fa-brands`, `fa-solid`, `fa-regular`).

### Animaciones Custom en CSS
- `.fade-in`: Animación `fadeIn 0.8s ease-out` para entrada suave con desplazamiento vertical (`translateY(20px) -> 0`).
- `.modal-content-enter`: Animación `slideUp 0.4s cubic-bezier(0.16, 1, 0.3, 1)` para modales.
- **Hover en Tarjetas**: `transform hover:-translate-y-1 hover:shadow-apple-hover transition-all duration-300`.

---

## 3. Desglose Estructural de Secciones en `index.html`

### A. Navbar Glass Fija (`<nav>`)
- **Posición**: Fija (`fixed w-full z-40`), efecto blur con borde inferior semitransparente.
- **Marca**: Logo de Modo Drone (`https://lh3.googleusercontent.com/d/1sPs2vD4seUO_QgIBoVx5ZAZIEGCD7HQ9=w1000?authuser=0`) + título.
- **Navegación Desktop**: Enlaces con `scrollToSection` a `#inicio`, `#portfolio`, `#tutoriales`, `#contacto`.
- **Redes Sociales**: Accesos directos a TikTok (`@mododrone`), YouTube (`ModoDrone`) e Instagram (`modo_drone`).

### B. Hero Section (`#inicio`)
- **Visuales**: Video de fondo en autoplay/loop/muted desde Cloudinary (`https://res.cloudinary.com/dd0gsndtt/video/upload/v1775685403/video_banner_01_yimb2w.mp4`) con overlay en gradiente oscuro.
- **Contenido**: Título principal *"Vuelo Sin Límites"* con gradiente verde neón + bajada de línea destacada por borde verde lateral.
- **Flecha de Scroll**: Botón con animación `animate-bounce` que desplaza hacia la sección portfolio.

### C. Sección Portfolio (`#portfolio`)
- **Propósito**: Galería de videos cinematográficos de paisajes y vuelos.
- **Disposición**: Grid de tarjetas en formato horizontal `16:9` (`aspect-video`).
- **Skeletons**: Indicadores de carga animados (`animate-pulse`) previa llegada de datos de la API.
- **Paginación**: Paginador numérico interactivo (8 elementos por página) con scroll suave automático.

### D. Sección Reels & Shorts (`#reels`)
- **Propósito**: Videos verticales dinámicos e imponentes cuya categoría comience con `Reel-`.
- **Botonera de Filtros (`#reels-filters`)**: Filtros automáticos generados según subcategorías `Reel-*`.
- **Disposición**: Grid vertical en formato `9:16` (`aspect-[9/16]`).
- **CTA Directo**: Enlace al perfil oficial de Instagram con icono de Instagram.
- **Paginación**: Paginación numérica independiente (10 elementos por página).

### E. Sección Academia & Tutoriales (`#tutoriales`)
- **Propósito**: Cursos, Shorts y guías para pilotos de dron.
- **Botonera de Filtros (`#tutoriales-filters`)**: Filtros dinámicos por categoría ("Todos", "Cursos", "Tutoriales", etc.) generados a partir de los datos recibidos de la API.
- **Disposición**: Grid vertical en formato `9:16` (`aspect-[9/16]`) optimizado para formato Shorts / Reels.
- **CTA Directo**: Botón para ir al canal oficial de YouTube con icono oficial.
- **Paginación**: Paginador numérico interactivo (10 elementos por página).

### F. Sección Contacto & Cotización (`#contacto`)
- **Propósito**: Captura de clientes para proyectos de tomas con dron, edición, eventos e inspecciones técnicas.
- **Diseño**: Tarjeta contenedora curva (`rounded-[2rem]`) con esfera difuminada brillante (`bg-apple-green/20 blur-3xl`).
- **Columna Izquierda**: Enlaces de correo (`mododroneok@gmail.com`) y perfil de Instagram.
- **Columna Derecha**: Formulario interactivo (`#contactForm`) conectado a Google Apps Script con feedback visual (botón con spinner y mensaje de éxito `#formSuccess`).

### G. Footer (`<footer>`)
- Fondo súper oscuro (`bg-[#050505]`), iconos sociales circulares con efecto glass, logo en escala de grises y copyright dinámico (`#year`).

### H. Asistente AI / Bot Reglamentario & Meteorológico (`#droneBot`)
- **Widget flotante**: Esquina inferior derecha (`fixed bottom-6 right-6 z-[100]`).
- **Ventana de Chat (`#chatWindow`)**:
  - Cabecera en verde neón con icono de robot.
  - Asistente inteligente para reglamentación aeronáutica y herramientas climáticas en tiempo real.
  - Paginador de menú interactivo (`loadMoreMenu`).
- **APIs Integradas en el Bot**:
  - **Open-Meteo API**: Viento (`wind_speed_10m`), Lluvia y visibilidad (`precipitation, visibility`), Índice UV (`uv_index`).
  - **NOAA SWPC API**: Índice Kp de actividad solar/geomagnética para evitar pérdidas de señal GPS.
  - **Sunrise-Sunset API**: Cálculo de la *Golden Hour* y horario de atardecer para filmación aeronáutica.
  - **Base de Datos de Reglamento**: Consulta dinámica desde Apps Script (`?tipo=reglamento`).

### I. Modal Reproductor de Video (`#videoModal`)
- Modal adaptativo inteligente:
  - **Videos horizontales (Portfolio)**: Reproductor de 16:9 centrado con barra superior.
  - **Videos verticales (Shorts/Tutoriales/Reels)**: Formato split en desktop (reproductor 9:16 a la izquierda, descripción con tipografía destacada a la derecha).
- Cierre mediante tecla `Escape`, botón "X" o clic fuera del contenido (`modalOverlay`).

---

## 4. Endpoints y Backend de Integración

| Identificador | URL | Descripción |
| :--- | :--- | :--- |
| `API_URL` | `https://script.google.com/macros/s/AKfycbxh8Fy1ANi-PfDz3z3neKNfQlqZXJXMHBU2iFDPUP7tFBEVObfnQYWx0In2q3K2NlHQrA/exec` | Obtención de videos (Portfolio, Reels y Tutoriales) y reglamentación del bot |
| `CONTACT_API_URL` | `https://script.google.com/macros/s/AKfycbzawIZGAOFMLRIM4Z-DGfIgXQDec57eastP4yIvM7ypw4-EsEAwggGLo39HhmiIMndijA/exec` | Envío de formulario de contacto (vía `POST` `no-cors`) |
| `Open-Meteo Weather` | `https://api.open-meteo.com/v1/forecast` | Datos meteorológicos (viento, lluvia, visibilidad, UV) |
| `NOAA Space Weather` | `https://services.swpc.noaa.gov/products/noaa-planetary-k-index.json` | Índice Kp geomagnético |
| `Sunrise-Sunset API` | `https://api.sunrise-sunset.org/json` | Horarios solares y Golden Hour |

---

## 5. Reglas de Oro para Futuras Modificaciones

1. **Respetar la paleta de colores**: Mantener los tokens de Tailwind en `tailwind.config` (`apple-green: #cefa03`, `apple-card: #1c1c1e`, `apple-bg: #000000`). No introducir colores secundarios discordantes.
2. **Conservar la distinción Horizontal vs. Vertical**:
   - Portfolio = formato landscape `aspect-video`.
   - Academia / Tutoriales / Reels = formato portrait `aspect-[9/16]`.
3. **Efectos de vidrio y bordes**: Utilizar siempre clases `.glass`, `.glass-card` y bordes sutiles `border-white/10` o `border-white/5`.
4. **Manejo de asincronismo y Skeletons**: Al agregar nuevas listas o secciones dinámicas, mantener skeletons de carga para no romper el layout inicial.
5. **No alterar los scripts de integración con Google Apps Script y APIs públicas** sin verificar primero su funcionamiento.
6. **Actualizar esta Skill**: Cualquier adición relevante de código, módulo o endpoint debe ser registrada inmediatamente en este archivo (`.agents/skills/mododrone-learnings/SKILL.md`).

---

## 6. Historial de Cambios del Proyecto
- **2026-08-01**:
  - Inicialización del repositorio Git local y remoto (`https://github.com/Dariobod/mododrone_web.git`).
  - Creación del archivo `.gitignore` y Skill `.agents/skills/mododrone-learnings/SKILL.md`.
  - Auditoría y análisis técnico completo de `index.html` (Secciones, Estilos, Tailwind Config, APIs climáticas/reglamentación, Modal adaptativo y Asistente AI).
  - Prueba y confirmación exitosa de flujo CI/CD automático con Cloudflare Pages (reversión del menú a "Contacto").
  - **Tag `v1.0.0`**: Creación y push de la etiqueta de versión estable de referencia a GitHub.
  - **Nueva Sección Reels**: Implementación de la sección `#reels` entre Portfolio y Tutoriales para mostrar videos categorizados como `Reel-*` en formato vertical `9:16` con paginador y filtros dinámicos.
  - **Favicon**: Configuración del icono de la barra de navegación como favicon del sitio en `<head>`.
  - **Scroll Suave con Inercia**: Integración de la librería **Lenis** (`unpkg.com/lenis`) para lograr desplazamiento fluido con aceleración e inercia al hacer scroll con la rueda del mouse y navegación entre secciones.
  - **Optimización Integral SEO & GEO (Inteligencia Artificial)**:
    - **Meta Tags**: Description, Keywords, Robots `max-image-preview:large`, Canonical.
    - **Social Sharing**: Meta etiquetas Open Graph (OG) y Twitter Cards.
    - **Datos Estructurados (JSON-LD)**: Esquemas Schema.org para `Organization`, `ProfessionalService`, `WebSite` y `FAQPage`.
    - **Rastreadores y Crawlers**: Creación de `robots.txt` permitiendo explícitamente bots de IA (`GPTBot`, `PerplexityBot`, `ClaudeBot`, `Google-Extended`, etc.).
    - **Indexación y GEO Standard**: Creación del mapa del sitio `sitemap.xml` y del estándar abierto `llms.txt` para motores de búsqueda conversacionales y LLMs.
    - **Optimización Semántica & Sinónimos**: Incorporación explícita de variaciones clave en SEO/GEO (`dron`, `drones`, `VANT - Vehículos Aéreos No Tripulados`, `SVANT`, `RPAS`, `modo dron`, `vuelo no tripulado` y `aeronave no tripulada`) en meta tags, JSON-LD `alternateName`, subtítulos visibles y `llms.txt`.
  - **Prueba de UI - Carrusel de Reels**: Modificación temporal de la sección `#reels` para mostrar las tarjetas en una única línea horizontal con desplazamiento fluido y flechas laterales de navegación (`scrollReelsCarousel`).
  - **Prueba de UI - Reproducción Directa de Videos en Reels**: Carga de videos en vivo (autoplay, muted, loop) con máscara temporal de portada (`reel-cover-thumb`) que se desvanece suavemente a los 1.8s (`transition-opacity duration-700`), ocultando al 100% el destello inicial de los íconos de pausa/flechas de YouTube **sin realizar ningún recorte de imagen ni alterar la escala del video original**.
- **2026-08-03**:
  - **Optimización de Carga Instantánea en Reels (Dual-Layer & Lazy Video Swap)**: Implementación del modo de carga ultrarrápida mediante la constante `REELS_INSTANT_LOAD_MODE`. Renderizado inmediato (0ms) de miniaturas estáticas e inyección diferida del reproductor de YouTube mediante `IntersectionObserver` cuando la sección entra en el viewport, realizando una transición de desvanecimiento cruzado (`cross-fade`) imperceptible. Se conserva el interruptor global para reversión instantánea al comportamiento anterior en caso de ser requerido.
- **2026-08-05**:
  - **Simplificación del Carrusel & Hover Preview en Reels**: Remoción total de iFrames permanentes embebidos en las tarjetas del carrusel. Las tarjetas cargan miniaturas estáticas `9:16` con el título ubicado por debajo. Al posicionar el cursor sobre cualquier tarjeta (`onmouseenter`), se inyecta dinámicamente el iFrame del video en vista previa silenciada, y al retirar el cursor (`onmouseleave`), se remueve inmediatamente el iFrame del DOM. Al hacer clic, se abre el modal emergente.
