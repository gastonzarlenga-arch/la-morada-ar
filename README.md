# LA MORADA — Menú WebAR

Repositorio privado del prototipo de realidad aumentada.

## Estado
El Galaxy S21 Ultra carga Three.js, abre AR y detecta superficies. Todavía **no está confirmada** la visualización del marcador sobre la mesa. La siguiente versión debe aislar el renderizado y proyección de cámara.

## Publicación por FTPS
El workflow `.github/workflows/deploy.yml` solo se ejecuta manualmente y está protegido por el ambiente `ar-staging`.

Configurar en GitHub > Settings > Environments > **New environment**: `ar-staging`.
Allí, agregar secretos:
- `FTP_HOST`: `cp7037.webempresa.eu`
- `FTP_USER`: usuario FTP limitado de WePanel
- `FTP_PASSWORD`: contraseña FTPS (NO compartir por chat)

Agregar variable del environment:
- `FTP_REMOTE_DIR`: **ruta del directorio remoto vista desde la cuenta FTP**, terminada en `menuvr/staging/` (por ejemplo `public_html/menuvr/staging/`, solo si ésa es la ruta real).

**Importante:** hay que verificar la raíz FTP y crear la carpeta de pruebas antes del primer despliegue. No usar `/menuvr/` de producción aún. El workflow solo sube `site/index.html`, no borra archivos. El FTP remoto puede ser relativo a la raíz de la cuenta.

## Flujo
1. Se agrega una versión validada en `site/index.html`.
2. Se comprueban secretos y ruta exacta.
3. En Actions > Publicar La Morada AR (FTPS) > Run workflow.
4. Se verifica la URL pública de staging.
5. Solo después se plantea el pase a producción.

El QR queda postergado.
