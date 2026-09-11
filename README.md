# Cobranzas · Administración de Parques Nacionales

Tablero interactivo de cobranzas de la **Dirección Nacional de Uso Público — Dirección de Concesiones**, con el informe trienal en PDF incorporado.

Período: **agosto 2023 a agosto 2026** · tres ciclos anuales de septiembre a agosto, contados hacia atrás desde el 31 de agosto de 2026.

## Qué contiene

| Archivo | Contenido |
| --- | --- |
| `index.html` | Tablero completo: datos, estilos, gráficos, buscador y logo institucional, todo embebido |
| `Informe_Cobranzas_trienal_ago26.pdf` | Informe de cobranzas en formato presentación, enlazado desde el encabezado y el pie del tablero |
| `manifest.webmanifest` | Definición de la aplicación instalable (nombre, iconos, colores, pantalla completa) |
| `sw.js` | Service worker: permite usar el tablero y abrir el informe sin conexión |
| `icons/` | Iconos de la aplicación en 192 y 512 px, versión enmascarable para Android y touch icon para iOS |
| `.nojekyll` | Evita que GitHub Pages procese el sitio con Jekyll |

## Qué muestra el tablero

- **Universo**: prestadores turísticos o todos los pagos, con filtro de medios de pago electrónicos (depurados por defecto: sólo figuran registrados hasta julio de 2025).
- **Conjunto**: diez principales pagadores o nueve dependencias.
- **Unidad**: pesos constantes ajustados por CER, dólares del día o pesos corrientes.
- **Vista**: tendencia de media móvil de 3 meses (por defecto) o valores mensuales; opción de acumular la selección.
- **Buscador**: cualquiera de los 250 mayores pagadores por razón social o CUIT —97,6% de la cobranza del período—, que se dibuja en ámbar sobre el gráfico.
- **Franja inferior** con el total del conjunto en escala propia, tabla de comparación por ciclo anual y nota metodológica.

## Publicar en GitHub Pages

1. Crear un repositorio y subir el contenido de esta carpeta a la rama `main`:

   ```bash
   git init
   git add .
   git commit -m "Tablero de cobranzas APN"
   git branch -M main
   git remote add origin https://github.com/USUARIO/REPOSITORIO.git
   git push -u origin main
   ```

2. En el repositorio: **Settings → Pages → Build and deployment**, elegir *Deploy from a branch*, rama `main` y carpeta `/ (root)`. Guardar.

3. En un minuto queda publicado en `https://USUARIO.github.io/REPOSITORIO/`.

GitHub Pages sirve el sitio por HTTPS, que es el requisito para que funcione el service worker y la instalación como aplicación.

## Instalar en el teléfono

**Android (Chrome).** Abrir el enlace publicado y tocar *Instalar aplicación* en el menú de tres puntos, o aceptar el aviso que aparece solo. Queda un ícono en el escritorio y la app se abre a pantalla completa, sin barra de navegador.

**iPhone y iPad (Safari).** Abrir el enlace, tocar el botón *Compartir* y elegir *Agregar a inicio*. Safari no muestra aviso automático: hay que usar esa opción.

**Escritorio (Chrome o Edge).** Aparece un ícono de instalación en la barra de direcciones.

Una vez instalada, el tablero y el informe quedan guardados en el dispositivo y se pueden consultar sin conexión. Al publicar una versión nueva, el tablero se actualiza solo la próxima vez que se abra con internet.

### Si actualizás los archivos

El service worker guarda copias con la etiqueta de versión que figura en `sw.js`. Cuando reemplaces el tablero o el informe, cambiá esa línea —por ejemplo de `cobranzas-apn-v1` a `cobranzas-apn-v2`— para que los dispositivos ya instalados descarten la copia vieja.

## Notas

No hay dependencias ni proceso de compilación. Los gráficos son SVG generados con JavaScript sin librerías externas; lo único que se descarga de la red es la tipografía Archivo desde Google Fonts, que el service worker guarda en el primer uso y que cae a la tipografía del sistema si no está disponible.

El archivo `index.html` también funciona abierto localmente con doble clic, aunque en ese caso no se instala como aplicación ni se activa el modo sin conexión, que requieren HTTPS.

## Fuente

Elaboración propia sobre datos disponibles en ReNaRI. El informe de deuda citado corresponde al relevamiento al 31 de agosto de 2026.
