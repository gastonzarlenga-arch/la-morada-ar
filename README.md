# LA MORADA — Menú WebAR

Repositorio privado para el menú AR. La detección de superficies y el renderizado normal funcionan; la visibilidad final del contenido AR continúa en diagnóstico.

## Publicación segura de prueba

El usuario FTP de WePanel tiene asignada la raíz:
`/home/lamorad1/public_html/lamoradaburgers.com.ar/menuvr`.

Esto significa que **la carpeta de la web `/menuvr/` ya es la raíz del usuario FTP**. No repetir `public_html/menuvr` en la ruta remota.

Destino único de la automatización: **`staging/index.html`**, relativo a esa raíz FTP. URL prevista: `https://lamoradaburgers.com.ar/menuvr/staging/`.

El workflow `.github/workflows/deploy.yml` se ejecuta **solo manualmente** y está asociado al environment `ar-staging`. No se ejecutó ningún despliegue desde este repositorio al preparar esta configuración.

En GitHub > Settings > Environments > `ar-staging`:
- Secret `FTP_HOST`: `cp7037.webempresa.eu`
- Secret `FTP_USER`: cuenta FTP restringida de WePanel
- Secret `FTP_PASSWORD`: contraseña (nunca compartir en chat)
- Variable **`FTP_REMOTE_DIR`**: exactamente **`staging/`**.

El workflow verifica esa variable antes de publicar. Únicamente sube `site/index.html` y no elimina archivos. No modifica `/menuvr/index.html`.

Para lanzar una prueba: GitHub > Actions > «Publicar La Morada AR (FTPS)» > Run workflow. Verificar que aparezca la página de staging y revisar los logs si falla. Si Webempresa asigna otra raíz FTP, detener el flujo y corregirlo antes de intentar publicar.

El QR definitivo permanece postergado.
