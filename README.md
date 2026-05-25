Este no es el proyecto original, solo agrega la compatibilidad multi-sucursal UTN y detección dinámica de facultad.
Link al proyecto original: https://github.com/inakigarcia1/modern-sysacad


Este PR extiende ModernSysacad para que funcione en otras facultades regionales de UTN, no solo en FRT Tucumán.

Cambios realizados:

Manifests (manifest.chromium.json, manifest.firefox.json): se agregó https://servicios.fra.utn.edu.ar/* a los matches del content script y de web_accessible_resources. Esto permite que la extensión se ejecute también en el Sysacad de la Facultad Regional Avellaneda (FRA).
content.js: se reemplazó el string hardcodeado "Facultad Regional Tucumán" por una detección dinámica del nombre de la facultad. La extensión extrae automáticamente el código regional del hostname (ej. fra, frt, frc) y lo mapea al nombre completo mediante un objeto regionalMap. Si la regional no está en el mapa, muestra el código como fallback.
Cómo se probó:

Cargada como extensión sin empaquetar en Chrome
Verificado su funcionamiento en https://servicios.fra.utn.edu.ar/Sysacad/loginAlumno.asp
El nombre mostrado es "Facultad Regional Avellaneda" en lugar de "Tucumán"
Los links relativos del menú laterar y el login resuelven correctamente bajo el subdirectorio /Sysacad/
Compatibilidad hacia atrás:

Sin cambios en style.css ni en la lógica de cálculo de promedios
100% retrocompatible con FRT Tucumán — el regionalMap incluye 'frt': 'Tucumán'


Para agregar otra sucursal en el futuro, solo hace falta:

Agregar el dominio al array matches en ambos manifests
Agregar la entrada en regionalMap en content.js
