# Bitácora del equipo

Basada en `PLANTILLA_EVIDENCIAS.md` del paquete del reto. Los campos marcados con *[completar]* se llenan durante el encuentro 2. **No escribir contraseñas, tokens ni claves.** Las capturas se guardan en `documentacion/evidencias/`.

**Cómo usar esta bitácora**

1. Antes de cada prueba, leer su ficha y el procedimiento enlazado.
2. Anotar la hora de inicio **antes** de empezar (hora de Colombia, UTC−5, formato `HH:MM:SS`).
3. Tomar la captura en ventana privada y guardarla con el nombre indicado en la ficha.
4. Llenar "Resultado observado" con lo que pasó de verdad, no con lo esperado.
5. Actualizar la fila de la prueba en el [tablero](#tablero-de-pruebas).

---

## Tablero de pruebas

Las pruebas se ejecutan en este **orden** (el respaldo va antes de la actualización):

| Orden | Prueba | Responsable | Estado | ¿Cumple? | Evidencia |
|:-:|---|---|---|---|---|
| 1 | [B01 — Publicación](#b01--publicación) | *[completar]* | En curso | *[ ]* | `B01_v1.png` |
| 2 | [B03 — Respaldo](#b03--respaldo) | *[completar]* | Pendiente | *[ ]* | `B03_drive.png` |
| 3 | [B02 — Actualización](#b02--actualización) | *[completar]* | Pendiente | *[ ]* | PR + `B02_v2.png` |
| 4 | [B04 — Recuperación](#b04--recuperación) | *[completar]* | Pendiente | *[ ]* | `B04_error.png`, `B04_recuperado.png` |
| 5 | [B05 — Permisos](#b05--permisos) | *[completar]* | Pendiente | *[ ]* | `B05_*.png` |
| 6 | [B06 — Repetibilidad](#b06--repetibilidad) | *[completar: no puede ser el admin]* | Pendiente | *[ ]* | `B06_*.png` |

Estados: Pendiente · En curso · Hecha · Repetida. ¿Cumple?: Sí / No / Parcial / No realizado.

---

## Registro del equipo

- **Equipo:** *[completar]*
- **Integrantes y responsabilidades:**

  | Nombre | Usuario GitHub | Rol |
  |---|---|---|
  | *[completar]* | *[completar]* | admin |
  | *[completar]* | *[completar]* | revisor |
  | *[completar]* | *[completar]* | actualiza |
  | *[completar]* | *[completar]* | documenta |
  | *[completar]* | *[completar]* | repite B06 |

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
- **URL:** https://thomast-maker.github.io/Infra-Nube-Proyecto-Estud-IA/
- **Resultado observado:**
  - Pages ya estaba configurado desde `main` + `/docs`, con HTTPS obligatorio activo.
  - El despliegue del commit `a1c62ac` (merge del PR #1) quedó en estado `built` sin errores.
  - Comprobado con curl a las 10:24:38: la página responde HTTP 200 y contiene "Versión 1" y "v1.0.0"; `/styles.css` responde HTTP 200.
  - La caché de Pages es `max-age=600` (10 min).
  - Comprobación visual en ventana privada: *[completar]*
- **Inicio, fin y duración:** inicio del despliegue 10:06:50 · fin (`built`) 10:07:10 · duración 20 s (dato de la API de GitHub Pages, `pages/builds/latest`).
- **Evidencia:** *[completar: evidencias/B01_v1.png]*
- **¿Cumple?** *[Sí / No / Parcial / No realizado]*
- **Error encontrado y ajuste:** *[completar]*
- **Resultado al repetir la prueba:** *[completar]*

## B03 — Respaldo

> Se ejecuta **antes** de B02: no se actualiza sin respaldo de lo publicado.

- **Qué queremos comprobar:** existe una copia íntegra, fuera de GitHub, con ubicación, versión y archivos identificados.
- **Versión y estado inicial:** v1.0.0 publicada (contenido de `docs/`).
- **Pasos para repetirla:** [PROCEDIMIENTOS.md §2](PROCEDIMIENTOS.md).
- **Resultado esperado:** ZIP `respaldo_v1.0.0_20261121.zip` en Drive con `index.html`, `styles.css` y `manifest.json`; las huellas del manifiesto coinciden con `docs/`.
- **Observación previa:** el respaldo existente `respaldos/20261121_085314_059737` (08:53) coincide por SHA-256 con `sitio_v1/` original, **no** con lo publicado (`docs/index.html` tiene el pie v1.0.0). Hay que hacer un respaldo nuevo copiando `docs/` a `trabajo/`.
- **Ruta del respaldo local:** *[completar: respaldos/AAAAMMDD_HHMMSS_…]*
- **Ubicación en Drive y quién tiene acceso:** *[completar]*
- **Resultado observado:** *[completar]*
- **Inicio, fin y duración:** *[completar]*
- **Evidencia:** *[completar: evidencias/B03_drive.png (carpeta de Drive con el ZIP)]*
- **¿Cumple?** *[completar]*
- **Error encontrado y ajuste:** *[completar]*
- **Resultado al repetir la prueba:** *[completar]*

## B02 — Actualización

- **Qué queremos comprobar:** la versión 2 se publica por PR y el cambio se ve en la URL.
- **Versión y estado inicial:** v1.0.0 publicada; respaldo B03 hecho.
- **Pasos para repetirla:** [PROCEDIMIENTOS.md §3](PROCEDIMIENTOS.md).
- **Resultado esperado:** la URL muestra "Versión 2", "Ruta de espacios verdes" y el pie "v2.0.0"; existe el tag `v2.0.0`.
- **Resultado observado:** *[completar]*
- **Inicio, fin y duración:** *[completar: inicio = creación del PR · fin = "Versión 2" visible en ventana privada]*
- **Evidencia:** *[completar: enlace al PR + evidencias/B02_v2.png]*
- **¿Cumple?** *[completar]*
- **Error encontrado y ajuste:** *[completar]*
- **Resultado al repetir la prueba:** *[completar]*

## B04 — Recuperación

- **Qué queremos comprobar:** después de un error publicado, se recupera la versión correcta y se mide el tiempo.
- **Versión y estado inicial:** *[completar: v2.0.0 publicada]*
- **Error provocado:** *[completar: p. ej. index.html reemplazado por "Catálogo incorrecto"]*
- **Pasos para repetirla:** [PROCEDIMIENTOS.md §4](PROCEDIMIENTOS.md).
- **Resultado esperado:** la URL vuelve a mostrar la versión del tag elegido, con estilos.
- **Método usado:** *[revert / restaurar desde tag / emergencia del admin]*
- **Resultado observado:** *[completar]*
- **Inicio, fin y duración:**
  - Inicio (error visible en la URL): *[completar]*
  - Fin (versión correcta en la URL, ventana privada): *[completar]*
  - Duración: *[completar]*
- **Versión recuperada:** *[completar]*
- **Evidencia antes y después:** *[completar: evidencias/B04_error.png, evidencias/B04_recuperado.png]*
- **Pasos manuales y cuáles automatizaríamos:** *[completar]*
- **¿Cumple?** *[completar]*
- **Error encontrado y ajuste:** *[completar]*
- **Resultado al repetir la prueba:** *[completar]*

## B05 — Permisos

- **Qué queremos comprobar:** lectura, actualización y administración están separadas.
- **Versión y estado inicial:** *[completar: versión publicada y protección de `main` y tags activas]*
- **Pasos para repetirla:** [PERMISOS.md, "Cómo demostrarlo"](PERMISOS.md).
- **Resultado esperado:** sin sesión se ve el sitio y no se edita; un push directo a `main` y el borrado de un tag `v*` son rechazados; solo el admin ve la configuración.
- **Resultado observado:**

  | Nivel | Acción probada | Resultado |
  |---|---|---|
  | Lectura (sin sesión) | Abrir el sitio / intentar editar | *[completar]* |
  | Actualización | Push directo a `main` | *[completar]* |
  | Actualización | Borrar un tag `v*` | *[completar]* |
  | Administración | Ver Settings del repositorio | *[completar]* |

- **Evidencia (sin credenciales):** *[completar: evidencias/B05_push_rechazado.png, evidencias/B05_tag_rechazado.png]*
- **¿Cumple?** *[completar]*
- **Limitación:** en repo personal no hay rol "solo lectura" dentro de GitHub; ver PERMISOS.md.
- **Error encontrado y ajuste:** *[completar]*

## B06 — Repetibilidad

- **Qué queremos comprobar:** otro integrante (que no sea el admin) repite la actualización o la recuperación solo con estas instrucciones.
- **Quién la repite:** *[completar]*
- **Procedimiento repetido:** *[actualización / recuperación]*
- **Pasos para repetirla:** [PROCEDIMIENTOS.md §3 o §4](PROCEDIMIENTOS.md), sin ayuda verbal del resto del equipo.
- **Resultado esperado:** obtiene el mismo resultado que en B02 o B04.
- **Resultado observado:** *[completar]*
- **Dudas que tuvo y qué se corrigió en la documentación:** *[completar]*
- **Inicio, fin y duración:** *[completar]*
- **Evidencia:** *[completar: evidencias/B06_resultado.png + enlace al PR si aplica]*
- **¿Cumple?** *[completar]*

---

## Cierre

- **Qué funciona realmente:** *[completar]*
- **Qué quedó como propuesta o pendiente:** *[completar]*
- **Procedimiento para recrear y recuperar:** [PROCEDIMIENTOS.md](PROCEDIMIENTOS.md).
- **Limitaciones y cambios para el encuentro 3:** *[completar. Ideas: organización gratuita con roles Read/Write/Admin; automatizar el respaldo con GitHub Actions; verificación automática de la URL después de cada despliegue]*
