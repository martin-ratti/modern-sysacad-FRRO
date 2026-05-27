# ModernSysacad

Una extensión de Chrome y Firefox que **moderniza el SYSACAD** de las Facultades Regionales de UTN. Diseño limpio, modo oscuro, y atajos visuales para que la información que importa esté siempre a un vistazo.

---

## Regionales soportadas

| Regional | Dominio | Producto SYSACAD |
|---|---|---|
| **Tucumán (FRT)** | `sysacad.frt.utn.edu.ar` | SYSACAD ASP clásico |
| **Resistencia (FRRe)** | `sysacadweb.frre.utn.edu.ar` | SYSACAD-WEB (Bootstrap 3) |

Cada regional tiene su propio par de archivos (`*.js` + `*.css`) que el manifest solo inyecta en el dominio correspondiente. No hay riesgo de cross-contamination entre regionales: el código de FRT nunca corre en FRRe ni viceversa.

---

## Features

### FRT (Tucumán)
* 🌗 Modo oscuro
* 🎨 Sidebar custom con íconos
* 📊 Promedio académico (general + por año)
* 📝 Promedios Con/Sin Aplazos en Exámenes (con conversión texto → número)
* 📜 Decoración de páginas de certificados, inscripciones y avisos

### FRRe (Resistencia)
* 🌗 Modo oscuro con transición **View Transitions API** (radial reveal desde el click)
* ✨ Animaciones de count-up, stagger entrance, fade-in, pulse y wobble
* 🎓 **Login rediseñado**: toggle Alumno/Docente con sliding indicator (estilo iOS), logo UTN moderno
* 📊 **Estado Académico**: banner de promedio + stat cards (Aprobadas / Cursando / Equivalencias) + barra de progreso de carrera + grilla de promedios por año (★ marca el mejor)
* 📝 **Exámenes**: promedios Con/Sin Aplazos, stat cards (Total / Aprobados / Aplazos), notas coloreadas
* 📅 **Grilla semanal de horarios** en Materias Actuales: parsea la columna Horarios y arma una vista timetable Lun–Sáb con bloques de colores por materia
* 🔍 **Buscador** en tablas grandes — insensible a acentos y multi-token (`"fisica"` matchea `"Física"`)
* ✓ Checks Si/No en Materias del Plan
* 🟢🟡 Status dots en Estado Académico (Aprobada / Cursando / Equivalencia)
* ℹ️ FAB de créditos con info de la versión

---

## Instalación local (desarrollo)

### 1. Manifest

El repo tiene un manifest por navegador. **Copialo** (no lo renombres) como `manifest.json`:

* **Chrome / Edge / Brave / Opera**: copiá `manifest.chromium.json` → `manifest.json`
* **Firefox**: copiá `manifest.firefox.json` → `manifest.json`

> `manifest.json` está en `.gitignore` y no se commitea — es un archivo local de desarrollo. La fuente de verdad son `manifest.chromium.json` y `manifest.firefox.json`.

### 2. Cargar la extensión

**Chrome / Chromium:**
1. Andá a `chrome://extensions/`
2. Activá el **"Modo de desarrollador"** (switch arriba a la derecha)
3. Clickeá **"Cargar descomprimida"** y seleccioná la carpeta raíz del proyecto

**Firefox:**
1. Andá a `about:debugging` → **"Este Firefox"**
2. Clickeá **"Cargar complemento temporal..."** y seleccioná `manifest.json`

Listo. Entrá al SYSACAD de tu regional y vas a ver los cambios.

---

## Colaborar

Cualquier mejora de UI, nuevas features o adaptaciones a nuevas regionales son bienvenidas. El proyecto mantiene una sola rama principal (`main`).

### Agregar una nueva regional

1. Agregá una entrada en `content_scripts` y `web_accessible_resources` de ambos manifests apuntando al dominio de tu regional.
2. Creá `<regional>.js` y `<regional>.css` con tu lógica y estilos.
3. Tu código se ejecutará automáticamente solo en tu dominio gracias al `matches` del manifest.

### Mejorar una regional existente

1. Editá el `.js` y `.css` correspondiente (`content.js` + `style.css` para FRT, `frre.js` + `frre.css` para FRRe).
2. No tocar los archivos de otras regionales.

### Pull request

1. Hacé un **fork** del repo.
2. Creá una rama: `git checkout -b feature/mi-mejora`.
3. Commit y push a tu fork.
4. Abrí un PR contra `main`.

---

## Colaboradores

**FRT (Tucumán)** — autor original: [Iñaki García](https://github.com/inakigarcia1) y la [comunidad](https://github.com/inakigarcia1/modern-sysacad/graphs/contributors)

**FRRe (Resistencia)**:
* Tomás Kobluk
* Gonzalo Fidanza
* Lorenzo Arduino

---

## ☕ Apoyá el proyecto

Este proyecto es 100% gratuito y de código abierto. Si te ahorró un dolor de cabeza (o de ojos), podés invitarle un cafecito al autor original:

[![Cafecito](https://img.shields.io/badge/Invitame%20un-Cafecito-ffdd00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://cafecito.app/inakigarcia)

---

## 📄 Licencia

Este proyecto está bajo la Licencia MIT. Ver `LICENSE` para más detalles.
