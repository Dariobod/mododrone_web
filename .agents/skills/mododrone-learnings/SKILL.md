---
name: mododrone-learnings
description: Base de conocimiento y aprendizajes del proyecto Modo Drone Web. Contiene la arquitectura, convenciones, configuraciones de Git y registro de evoluciones del proyecto.
---

# Modo Drone Web - Skill de Aprendizajes

Este documento registra las decisiones técnicas, la estructura del proyecto, las convenciones de diseño y el historial de cambios aplicados a la plataforma web de **Modo Drone**.

---

## 1. Información General del Proyecto
- **Proyecto**: Modo Drone (Hub de Operaciones & FPV)
- **Repositorio Git**: `https://github.com/Dariobod/mododrone_web.git`
- **Rama Principal**: `main`

---

## 2. Arquitectura y Stack Tecnológico
- **HTML5 Semántico**: Estructura modular con secciones (`inicio`, `portfolio`, `tutoriales`, `contacto`, modales, etc.).
- **Estilos y Diseño**:
  - **Tailwind CSS** (vía CDN con extensión de tema personalizada).
  - **Paleta de Colores**:
    - Fondo oscuro Apple: `#000000` / `#1c1c1e`
    - Acento / Verde Modo Drone: `#cefa03` (`apple-green`)
    - Texto principal: `#f5f5f7`
    - Texto secundario / gris: `#86868b`
  - **Tipografía**: Font `Inter` vía Google Fonts.
  - **Efectos visuales**: Glassmorphism (`backdrop-filter blur`), animaciones de entrada (`fade-in`, `slideUp`), glow de neón en botones y tarjetas.
- **Iconos & Recursos Multimedia**:
  - **FontAwesome 6.4.0** para iconos sociales e interactivos.
  - **Cloudinary / Google Drive** para imágenes y videos de fondo/hero.

---

## 3. Flujo de Trabajo y Versionado (Git)
- **Inicialización**: Repositorio local `git init -b main`.
- **Origen Remoto**: Conectado a `https://github.com/Dariobod/mododrone_web.git`.
- **Estrategia de Commit**: Commits descriptivos e informativos para mantener el historial limpio y trazable.
- **Skill en Workspace**: Todas las mejoras, nuevas funcionalidades y patrones aprendidos deben sincronizarse en `.agents/skills/mododrone-learnings/SKILL.md`.

---

## 4. Historial de Cambios y Aprendizajes
- **2026-08-01**:
  - Inicialización del repositorio Git local y vinculación al remoto de GitHub.
  - Creación del archivo `.gitignore` básico para entornos de desarrollo web.
  - Creación de la Skill de Aprendizaje del proyecto `.agents/skills/mododrone-learnings/SKILL.md`.
  - Primer commit e integración inicial con la página `index.html`.
