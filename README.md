# Portal de Situación UNGRD — Sismo San José del Palmar (Chocó)

Portal web de un solo repositorio que integra dos tableros para el evento sísmico:

- **Afectaciones (EDAN)** — consolidado de afectaciones por departamento y municipio, con mapa coropletico de Colombia.
- **Capacidades USAR** — equipos de busqueda y rescate movilizados, con mapa de movilizacion origen -> zona.

Ambos leen sus datos en vivo desde hojas de Google Sheets publicadas (formato CSV) y recalculan todo en el navegador. Conservan como respaldo la carga de un archivo `.xlsx` y unos datos de ejemplo.

## Archivos

- `index.html` — portal con encabezado UNGRD y pestanas; embebe los dos tableros.
- `afectaciones.html` — tablero de afectaciones (GeoJSON de Colombia incrustado).
- `capacidades-usar.html` — tablero de capacidades USAR (centroides de municipios incrustados).

## Publicar en GitHub Pages

1. Crear un repositorio y subir estos tres archivos (y este README).
2. En **Settings -> Pages**, elegir la rama `main` y carpeta `/root`, y guardar.
3. El portal queda disponible en `https://<usuario>.github.io/<repositorio>/`.

Al servirse desde `https` (GitHub Pages), la lectura de Google Sheets es **directa**: deje **desmarcada** la casilla "Proxy CORS". Esa casilla solo es necesaria cuando el archivo se abre localmente (`file://`), caso en el que la lectura se enruta por un proxy publico.

## Fuentes de datos

Cada tablero trae precargada la URL de su hoja publicada (campo "Fuente de datos"). Para cambiarla, publique la hoja en **Archivo -> Compartir -> Publicar en la web** y use el enlace en formato CSV (`.../pub?output=csv`). El boton "Actualizar desde Drive" vuelve a leer la fuente.

## Notas

- Requiere conexion a internet para las librerias (Leaflet, SheetJS), el mapa base y la lectura de datos.
- Las hojas publicadas quedan accesibles publicamente. Para datos restringidos, use un proxy propio con Google Apps Script o autenticacion (OAuth) en un despliegue con backend.
- Producto de trabajo institucional. Cifras EDAN/operativas preliminares sujetas a verificacion. Ley 1523 de 2012 — SNGRD.
