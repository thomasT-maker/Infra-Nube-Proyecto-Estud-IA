# Bitácora del equipo

Basada en `PLANTILLA_EVIDENCIAS.md` del paquete del reto. Los campos marcados con *[completar]* se llenan durante el encuentro 2. **No escribir contraseñas, tokens ni claves.** Las capturas se guardan en `documentacion/evidencias/`.

## Registro del equipo

- **Equipo:** *[completar]*
- **Integrantes y responsabilidades:** *[completar: nombre — usuario GitHub — rol (admin / revisor / actualiza / documenta / repite B06)]*
- **Fecha:** 21 de noviembre de 2026 (encuentro 2)
- **Modalidad:** nube (GitHub Pages)
- **Arquitectura elegida y motivo:** sitio estático publicado con GitHub Pages desde `/docs` de `main`, versionado con Git y tags, respaldo independiente en Google Drive. Motivos en el [README](../README.md) y el [esquema](ESQUEMA.md).
- **Ayudas utilizadas y cambios realizados:**
  - `scripts/herramientas.py` del paquete: se usa para generar respaldos con manifiesto SHA-256 y como plan B local. Git reemplaza a `actualizar` y `restaurar` en la nube.
  - **Cambio propio:** se agregó la marca `v1.0.0` en el pie de `docs/index.html` (se conserva el texto "Versión 1" del cuerpo, que pide la guía). `sitio_v1/` y `sitio_v2/` quedan intactos.
  - Los PDF y las guías del paquete no se publican en el repositorio; se guardan en Drive.
  - Se usó Claude (asistente de IA) para estructurar el repositorio y redactar la documentación; el equipo revisó y ejecutó los procedimientos.
- **Recursos, permisos y posibles costos:** ver [PERMISOS.md](PERMISOS.md) y [ESQUEMA.md](ESQUEMA.md). Costo del ejercicio: ninguno.

---

## B01 — Publicación

- **Qué queremos comprobar:** el sitio abre en la dirección pública con la versión inicial y sus estilos.
- **Versión y estado inicial:** v1.0.0 en `docs/` de `main`; Pages recién activado.
- **Pasos para repetirla:** [PROCEDIMIENTOS.md §0 y §1](PROCEDIMIENTOS.md).
- **Resultado esperado:** la URL muestra "Versión 1", el pie "v1.0.0" y el título en morado, desde ventana privada y en un navegador distinto al de configuración.
- **Resultado observado:** Pages ya estaba configurado desde `main` + `/docs`, con HTTPS obligatorio activo. El despliegue del commit `a1c62ac` (merge del PR #1) quedó en estado `built` sin errores. Comprobado con curl a las 10:24:38 (hora de Colombia): la página responde HTTP 200 y contiene "Versión 1" y "v1.0.0"; `/styles.css` responde HTTP 200. La caché de Pages es `max-age=600` (10 min). *[completar: comprobación visual en ventana privada]*
- **URL:** https://thomast-maker.github.io/Infra-Nube-Proyecto-Estud-IA/
- **Inicio, fin y duración:** 21/11/2026, hora de Colombia (UTC−5). Inicio del despliegue: 10:06:50 · fin (`built`): 10:07:10 · duración: 20 s (dato de la API de GitHub Pages, `pages/builds/latest`).
- **Evidencia:** *[completar: evidencias/B01_v1.png]*
- **¿Cumple?** *[Sí / No / Parcial / No realizado]*
- **Error encontrado y ajuste:** *[completar]*
- **Resultado al repetir la prueba:** *[completar]*

## B02 — Actualización

- **Qué queremos comprobar:** la versión 2 se publica por PR y el cambio se ve en la URL.
- **Versión y estado inicial:** v1.0.0 publicada; respaldo B03 hecho.
- **Pasos para repetirla:** [PROCEDIMIENTOS.md §3](PROCEDIMIENTOS.md).
- **Resultado esperado:** la URL muestra "Versión 2", "Ruta de espacios verdes" y el pie "v2.0.0"; existe el tag `v2.0.0`.
- **Resultado observado:** *[completar]*
- **Inicio, fin y duración:** *[completar]*
- **Evidencia:** *[completar: enlace al PR + evidencias/B02_v2.png]*
- **¿Cumple?** *[completar]*
- **Error encontrado y ajuste:** *[completar]*
- **Resultado al repetir la prueba:** *[completar]*

## B03 — Respaldo

- **Qué queremos comprobar:** existe una copia íntegra, fuera de GitHub, con ubicación, versión y archivos identificados.
- **Versión y estado inicial:** *[completar: versión respaldada]*
- **Pasos para repetirla:** [PROCEDIMIENTOS.md §2](PROCEDIMIENTOS.md).
- **Resultado esperado:** ZIP en Drive con `index.html`, `styles.css` y `manifest.json`.
- **Ruta del respaldo local:** *[completar: respaldos/AAAAMMDD_HHMMSS_…]*
- **Ubicación en Drive y quién tiene acceso:** *[completar]*
- **Resultado observado:** *[completar]*
- **Evidencia:** *[completar]*
- **¿Cumple?** *[completar]*

## B04 — Recuperación

- **Qué queremos comprobar:** después de un error publicado, se recupera la versión correcta y se mide el tiempo.
- **Versión y estado inicial:** *[completar: v2.0.0 publicada]*
- **Error provocado:** *[completar: p. ej. index.html reemplazado por "Catálogo incorrecto"]*
- **Pasos para repetirla:** [PROCEDIMIENTOS.md §4](PROCEDIMIENTOS.md).
- **Resultado esperado:** la URL vuelve a mostrar la versión del tag elegido, con estilos.
- **Método usado:** *[revert / restaurar desde tag / emergencia del admin]*
- **Hora de inicio (error visible en la URL):** *[completar]*
- **Hora de fin (versión correcta en la URL, ventana privada):** *[completar]*
- **Duración:** *[completar]*
- **Versión recuperada:** *[completar]*
- **Evidencia antes y después:** *[completar: evidencias/B04_error.png, evidencias/B04_recuperado.png]*
- **Pasos manuales y cuáles automatizaríamos:** *[completar]*
- **¿Cumple?** *[completar]*

## B05 — Permisos

- **Qué queremos comprobar:** lectura, actualización y administración están separadas.
- **Pasos para repetirla:** [PERMISOS.md, "Cómo demostrarlo"](PERMISOS.md).
- **Resultado esperado:** sin sesión se ve el sitio y no se edita; un push directo a `main` y el borrado de un tag `v*` son rechazados; solo el admin ve la configuración.
- **Resultado observado:** *[completar]*
- **Evidencia (sin credenciales):** *[completar]*
- **¿Cumple?** *[completar]*
- **Limitación:** en repo personal no hay rol "solo lectura" dentro de GitHub; ver PERMISOS.md.

## B06 — Repetibilidad

- **Qué queremos comprobar:** otro integrante (que no sea el admin) repite la actualización o la recuperación solo con estas instrucciones.
- **Quién la repite:** *[completar]*
- **Procedimiento repetido:** *[actualización / recuperación]*
- **Resultado observado:** *[completar]*
- **Dudas que tuvo y qué se corrigió en la documentación:** *[completar]*
- **Inicio, fin y duración:** *[completar]*
- **¿Cumple?** *[completar]*

---

## Cierre

- **Qué funciona realmente:** *[completar]*
- **Qué quedó como propuesta o pendiente:** *[completar]*
- **Procedimiento para recrear y recuperar:** [PROCEDIMIENTOS.md](PROCEDIMIENTOS.md).
- **Limitaciones y cambios para el encuentro 3:** *[completar. Ideas: organización gratuita con roles Read/Write/Admin; automatizar el respaldo con GitHub Actions; verificación automática de la URL después de cada despliegue]*
