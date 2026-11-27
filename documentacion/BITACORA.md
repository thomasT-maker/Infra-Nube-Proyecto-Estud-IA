# Bitácora del equipo

Basada en `PLANTILLA_EVIDENCIAS.md` del paquete del reto. Los campos marcados con *[completar]* se llenan durante el encuentro 2. **No escribir contraseñas, tokens ni claves.** Las capturas se guardan en `documentacion/evidencias/`.

## Registro del equipo

- **Equipo:** *[completar: nombre del equipo]*
- **Integrantes y responsabilidades:**

  | Nombre | Usuario GitHub | Participación |
  |---|---|---|
  | Thomas Taborda Castañeda | `thomasT-maker` | Admin y revisor |
  | Thomas Taborda Castañeda | `tabordathomas-maker` | Cuenta de pruebas: propone los cambios |
  | Andrés | `andrezg876-lang` | Actualización a la versión 2 (B02, PR #4) |
  | Juan | `juanpati913-sketch` | Nota en el README (PR #6) |
  | Simón Castrillón | *[completar usuario]* | Mejora de `PROCEDIMIENTOS.md` (PR #5) |

- **Transparencia sobre las cuentas:** `thomasT-maker` y `tabordathomas-maker` son de la misma persona. Con ellas se demuestra la separación de permisos (quien propone no publica sin la aprobación de otra cuenta), no la separación de personas.
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

**Resumen:** la versión 1 quedó publicada en GitHub Pages desde la carpeta `/docs` de `main` a las 10:07 a. m. del 21/11/2026. La dirección pública abre y muestra "Versión 1", el pie "v1.0.0", el título en morado y las dos experiencias. Es una publicación en la **nube** (GitHub Pages), no local. El tag `v1.0.0` se creó el 25/11/2026 a las 4:31 p. m. sobre el commit `a1c62ac` (merge del PR #1).

- **Qué queremos comprobar:** el sitio abre en la dirección pública con la versión inicial y sus estilos.
- **Versión y estado inicial:** v1.0.0 en `docs/` de `main`; Pages recién activado.
- **Pasos para repetirla:** [PROCEDIMIENTOS.md §0 y §1](PROCEDIMIENTOS.md).
- **Resultado esperado:** la URL muestra "Versión 1", el pie "v1.0.0" y el título en morado, desde ventana privada y en un navegador distinto al de configuración.
- **Resultado observado:**
  1. **Verificación del equipo (navegador del integrante, 21/11/2026 ≈ 11:10 a. m.):** la URL pública abre y muestra ✅ "Versión 1", ✅ el pie "v1.0.0", ✅ el título "Ruta Local" en morado (los estilos cargan) y ✅ las dos experiencias: *Recorrido por las historias del barrio* y *Taller de oficios y memoria*.
  2. **Verificación complementaria sin sesión (10:30 a. m.):** desde un navegador sin sesión de GitHub, la URL responde HTTP 200 y `styles.css` responde HTTP 200. Encabezados: `Last-Modified` 10:07:09 a. m. (hora en que Pages publicó) y `Cache-Control: max-age=600` (caché de 10 minutos).
- **URL:** https://thomast-maker.github.io/Infra-Nube-Proyecto-Estud-IA/
- **Inicio, fin y duración:** Pages publicó a las 10:07 a. m.; verificaciones a las 10:30 a. m. y ≈ 11:10 a. m. del 21/11/2026.
- **Evidencia:**

  Captura del equipo, con la barra de direcciones visible:

  ![B01: versión 1 publicada, captura del equipo](evidencias/B01_v1_publicada.png)

  **Descripción:** sitio público con la barra de direcciones visible. Muestra el título "Ruta Local" en morado, "Versión 1", dos experiencias (*Recorrido por las historias del barrio* y *Taller de oficios y memoria*) y el pie con `v1.0.0`.

  Verificación complementaria sin sesión, con una franja agregada que indica la URL, la hora y los encabezados HTTP:

  ![B01: verificación sin sesión](evidencias/B01_v1_verificacion_sin_sesion.png)

  **Descripción:** la misma versión 1, con una franja agregada que indica la URL, la fecha y hora (21/11/2026, 10:30 a. m.), las respuestas HTTP 200 del sitio y de `styles.css`, y que se consultó sin sesión de GitHub.

  Punto de recuperación `v1.0.0`, creado el 25/11/2026 a las 4:31 p. m. sobre `a1c62ac`:

  ![B01: release v1.0.0](evidencias/B01_tag_v1_release.png)

  **Descripción:** página de la release "v1.0.0 – Versión 1 publicada", creada por `thomasT-maker` sobre el commit `a1c62ac`, con el código fuente descargable en ZIP y tar.gz.

- **¿Cumple?** Sí
- **Error encontrado y ajuste:** en la publicación no hubo errores. Dos ajustes de documentación: (1) la captura del navegador integrado no mostraba la barra de direcciones, así que se agregó una franja con la URL y la hora; (2) el tag `v1.0.0`, que estaba pendiente, se creó el 25/11/2026 sobre el commit publicado `a1c62ac`.
- **Resultado al repetir la prueba:** se verificó dos veces, desde el navegador del equipo y desde un navegador sin sesión de GitHub, con el mismo resultado. **No la repitió todavía otro integrante siguiendo las instrucciones:** esa repetición corresponde a B06 y queda pendiente.

## B02 — Actualización

**Resumen:** la versión 2 se publicó por Pull Request. Andrés propuso el cambio en el PR #4, el admin lo aprobó a las 11:30 a. m. del 21/11/2026 y Pages lo publicó en 24 segundos. La dirección pública muestra "Versión 2" y la nueva experiencia *Ruta de espacios verdes*. El tag `v2.0.0` se creó el 25/11/2026 sobre el commit `2676ef1`. Después de esta prueba, el PR #8 (25/11) dejó `main` con el CSS dentro de `index.html`; ver "Error encontrado".

- **Qué queremos comprobar:** la versión 2 se publica por PR y el cambio se ve en la URL.
- **Quién la hizo:** `andrezg876-lang` propuso el cambio; `thomasT-maker` (admin) lo revisó, aprobó e hizo el merge.
- **Versión y estado inicial:** v1.0.0 publicada (commit `a1c62ac`). El respaldo B03 todavía no se había hecho al momento de actualizar.
- **Pasos realizados:**
  1. El integrante reemplazó `docs/index.html` por el contenido de `sitio_v2/index.html` y abrió el **[PR #4](https://github.com/thomasT-maker/Infra-Nube-Proyecto-Estud-IA/pull/4)** ("mi version 2, andres") desde su propia copia (*fork*) del repositorio. Cambió solo 1 archivo (`docs/index.html`); `styles.css` es igual en v1 y v2.
  2. El admin revisó el cambio y lo **aprobó**. La regla `proteger-main` exige 1 aprobación antes del merge.
  3. Merge a `main` (commit `2676ef1`) y despliegue automático de GitHub Pages.
  4. Verificación en el navegador sobre la URL pública.
- **Resultado esperado:** la URL muestra "Versión 2", "Ruta de espacios verdes" y el pie "v2.0.0"; existe el tag `v2.0.0`.
- **Resultado observado:** la URL pública muestra ✅ "Versión 2", ✅ la nueva experiencia **Ruta de espacios verdes** (3 experiencias en total) y ✅ el título en morado (los estilos cargan). ⚠️ El pie **no** muestra "v2.0.0", porque se copió `sitio_v2/index.html` tal cual, sin agregar la marca que sí tiene la v1.
- **Tiempos (21/11/2026, hora de Colombia):**

  | Momento | Hora |
  |---|---|
  | PR #4 creado | 11:25:41 |
  | Aprobación del admin | 11:30:04 |
  | Merge a `main` | 11:30:15 |
  | Pages: despliegue iniciado → terminado | 11:30:18 → 11:30:39 |
  | **Del PR al sitio actualizado** | **≈ 5 min** (de los cuales ~4 min 20 s fueron la espera de la aprobación y 24 s el merge y el despliegue) |

- **Evidencia:**

  Sitio publicado con la versión 2 (captura del equipo, barra de direcciones visible):

  ![B02: versión 2 publicada](evidencias/B02_v2_publicada.png)

  **Descripción:** sitio público con "Versión 2" y tres experiencias; la nueva es *Ruta de espacios verdes*. Los estilos cargan y el pie no muestra número de versión.

  Punto de recuperación `v2.0.0`, creado el 25/11/2026 a las 4:43 p. m. (Colombia) por el admin sobre el commit `2676ef1`, el merge del PR #4:

  ![B02: release v2.0.0](evidencias/B02_tag_v2_release.png)

  **Descripción:** página de la release "v2.0.0 – Versión 2 publicada", vista sin sesión (aparecen los botones *Sign in* y *Sign up*), sobre el commit `2676ef1` y con referencia al PR #4.

- **¿Cumple?** Sí. La versión 2 se publicó por PR con aprobación del admin, se ve en la URL pública y quedó marcada con el tag `v2.0.0`.
- **Observación y decisión:** el pie de la versión 2 **no** muestra la marca `v2.0.0`, porque se copió `sitio_v2/index.html` tal cual. Como la guía solo pide comprobar que aparece "Versión 2" y los tags no se pueden mover, se decidió **no** modificar el pie y etiquetar el commit que ya estaba publicado y verificado. Así el tag coincide exactamente con lo que muestra la captura. La versión del sitio se identifica por el tag y por el texto "Versión 2" del cuerpo.
- **Error encontrado y ajuste:**
  1. El pie de la versión 2 no dice `v2.0.0`, porque se copió `sitio_v2/index.html` sin esa marca. Se decidió no cambiarlo y etiquetar el commit ya verificado. La versión se identifica por el tag y por el texto "Versión 2".
  2. El tag `v2.0.0` se creó el 25/11/2026, después de la prueba, y no al momento del merge.
  3. **Observación posterior:** el PR #8 ("Volver a la version 1", 25/11/2026, 4:28 p. m.) reemplazó el contenido de `docs/index.html` por el CSS. El commit `2676ef1` y el tag `v2.0.0` no se ven afectados, pero `main` sí, y el sitio publicado muestra texto de código en lugar del catálogo. Resuelto el 26/11/2026 con el PR #9 (revert del PR #8).
- **Resultado al repetir la prueba:** no se ha repetido todavía. La repetición por otro integrante, siguiendo solo `PROCEDIMIENTOS.md`, corresponde a B06 y queda pendiente.

## B03 — Respaldo

**Resumen:** se creó un respaldo de la versión 2 publicada correctamente (tag `v2.0.0`, commit `2676ef1`). El respaldo se hizo el 26/11/2026 a las 11:49 a. m. (hora de Colombia), a partir del tag y no de `main`, porque `main` tenía el CSS dentro de `index.html` por el PR #8. Las huellas SHA-256 de la copia coinciden con las de los archivos del tag. Se comprimió en un ZIP y se subió a Google Drive.

- **Qué queremos comprobar:** existe una copia íntegra, fuera de GitHub, con ubicación, versión y archivos identificados.
- **Versión respaldada:** v2.0.0 (commit `2676ef1`, merge del PR #4).
- **Ruta del respaldo local:** `respaldos\20261126_114935_473619` (equipo del integrante, rama local `bitacora-b01`).
- **Archivos incluidos:**
  - `index.html`: SHA-256 `b6a32ff3f46af4730b7faa17661355ef57d13f337e618de6dd2bedd656ad1302`
  - `styles.css`: SHA-256 `436b588e09fcbcae2b86a737a64393a81c1f667abeb36e9ebfdd836cc32da022`
  - `manifest.json`: lista las dos huellas anteriores.
- **Ubicación en Drive:** archivo `respaldo_v2_20261126.zip`. La captura no muestra en qué carpeta está. *[pendiente: confirmar que esté en "Ruta Local - Respaldos (EstudIA)"]*
- **Quién tiene acceso:** solo la cuenta del admin. *[pendiente: compartir la carpeta con el equipo, sin enlace público]*
- **Resultado observado:** el `manifest.json` tiene las mismas huellas que los archivos del tag `v2.0.0`. Se comprobó con `sha256sum` y con `diff` (salida `IGUAL`).
- **Evidencia:**

  Terminal con el comando `respaldar` y el manifiesto:

  ![B03: terminal con respaldo y manifiesto](evidencias/B03_respaldo_v2_terminal.png)

  **Descripción:** terminal con el comando `respaldar`, la ruta creada (`respaldos\20261126_114935_473619`) y el contenido de `manifest.json` con las huellas SHA-256 de `index.html` y `styles.css`.

  Drive con el ZIP subido:

  ![B03: ZIP en Google Drive](evidencias/B03_respaldo_v2_drive.png)

  **Descripción:** página principal de Google Drive, en "Archivos sugeridos", con `respaldo_v2_20261126.zip` propio, creado a las 11:56 a. m. La captura no muestra en qué carpeta está ni con quién se comparte.

- **¿Cumple?** Sí, con dos pendientes: confirmar que el ZIP esté en la carpeta de respaldos y compartir esa carpeta con el equipo.
- **Error encontrado y ajuste:**
  1. **Huellas que no coincidían.** Al principio, `trabajo/index.html` tenía la versión 1. El paso `preparar` copia la v1 y el paso de copiar desde el tag no se había ejecutado después. Ajuste: volver a copiar `index.html` desde `v2.0.0` y comprobar con `diff` hasta obtener `IGUAL`.
  2. **Riesgo evitado.** `main` estaba roto por el PR #8. Respaldar desde `main` habría guardado la versión incorrecta. Ajuste: respaldar desde el tag `v2.0.0`.
  3. **Ubicación sin evidencia.** La captura de Drive no muestra la carpeta del ZIP. Ajuste pendiente: confirmar que esté en la carpeta de respaldos y capturarlo allí.
- **Uso del tag en este respaldo:** un tag es una marca fija en un commit. `v2.0.0` apunta a `2676ef1`, la versión correcta. Por eso el respaldo se tomó de ahí y no de `main`, que cambia con cada merge.
- **Resultado al repetir la prueba:** pendiente. La repetición por otro integrante corresponde a B06.

## B04 — Recuperación

**Resumen:** se provocó un error publicado en `main` con el PR #10 ("B04: error simulado") y se recuperó con un *revert* (PR #11). La URL pública volvió a mostrar la versión 2 con sus estilos, idéntica al commit `2676ef1`. El error estuvo en línea unos 4 minutos, según las horas de los despliegues en GitHub Actions (ver "Tiempos").

- **Qué queremos comprobar:** después de un error publicado, se recupera la versión correcta y se mide el tiempo.
- **Versión y estado inicial:** v2.0.0 publicada (tag `v2.0.0`, commit `2676ef1`), con "Versión 2" y los estilos morados.
- **Error provocado:** `docs/index.html` reemplazado por una página de prueba con el título "Catálogo incorrecto" y el texto "Versión de error para practicar la restauración." Se hizo desde la cuenta de pruebas (`tabordathomas-maker`) como PR #10, con el admin (`thomasT-maker`) como revisor.
- **Pasos para repetirla:** [PROCEDIMIENTOS.md §4](PROCEDIMIENTOS.md).
- **Resultado esperado:** la URL vuelve a mostrar la versión del tag elegido, con estilos.
- **Método usado:** *revert*. Se creó el PR #11 ("Revert 'B04: error simulado'") desde el PR #10 ya fusionado; el admin lo aprobó y lo fusionó. Los tags `v1.0.0` y `v2.0.0` no se tocaron.
- **Tiempos (hora de Colombia, UTC-5):**

  | Momento | Hora | Fuente |
  |---|---|---|
  | Merge del PR #10 (error a `main`) | 16:48:10 | commit `34b60a2` |
  | Despliegue de Pages con el error (run #7) | ≈ 16:48, duró 23 s | Actions |
  | Merge del PR #11 (revert a `main`) | 16:52:05 | commit `10eeaa8` |
  | Despliegue de Pages con la v2 recuperada (run #8) | ≈ 16:52, duró 25 s | Actions |

- **Hora de inicio (error visible en la URL):** ≈ 4:48 p. m. (despliegue #7, que terminó unos 23 s después del merge del PR #10).
- **Hora de fin (versión correcta en la URL, ventana privada):** ≈ 4:52 p. m. (despliegue #8, que terminó unos 25 s después del merge del PR #11).
- **Duración:** **≈ 4 minutos** (de 16:48:33 a 16:52:30, unos 3 min 57 s). La pestaña Actions muestra solo horas relativas, así que la precisión es de ±1 minuto. Si se quiere la hora exacta, pasar el cursor sobre cada run en Actions. La hora de la captura de Actions es 17:06 (run #7 "18 minutes ago", run #8 "14 minutes ago").
- **Versión recuperada:** v2 (commit `2676ef1`). Se comprobó que `docs/index.html` de `main` es idéntico al de ese commit y que `styles.css` también coincide.
- **Evidencia antes y después:**

  Error publicado, con la barra de direcciones visible:

  ![B04: error publicado](evidencias/B04_error.png)

  **Descripción:** la URL pública muestra "Catálogo incorrecto" y "Versión de error para practicar la restauración.", sin estilos.

  Versión recuperada tras el revert, con la barra de direcciones visible:

  ![B04: versión recuperada](evidencias/B04_recuperado.png)

  **Descripción:** la misma URL vuelve a mostrar "Versión 2", las tres experiencias y los estilos.

  Pestaña Actions con los dos despliegues de Pages (run #7 con el error y run #8 con la recuperación):

  ![B04: despliegues en GitHub Actions](evidencias/B04_actions_despliegues.png)

  **Descripción:** pestaña *Actions* con los despliegues de Pages. Los números 7 (el error) y 8 (la recuperación) terminaron correctamente, en 23 s y 25 s. El reloj del equipo marca 17:06 del 26/11/2026.

- **Pasos manuales y cuáles automatizaríamos:**
  - *Manuales (hoy):* editar `index.html` en GitHub, abrir el PR, aprobarlo, fusionarlo, abrir el revert, aprobarlo, fusionarlo y comprobar la URL en ventana privada.
  - *Automatizables:* crear el revert desde el último tag válido con un comando o un workflow; comprobar después del despliegue que la URL responde 200 y contiene "Versión 2"; avisar al equipo si falla.
  - *No automatizable sin cambiar la configuración:* la aprobación. La regla `proteger-main` exige un aprobador distinto del autor, y no hay un *bypass* configurado para emergencias. Por eso el admin debe aprobar a mano; en esta prueba el admin aprobó y fusionó el revert en pocos minutos.
- **¿Cumple?** Sí. La versión correcta quedó publicada por un PR revisado, sin tocar el tag, y la duración (≈ 4 minutos) se midió con los despliegues de Actions.
- **Error encontrado y ajuste:** ninguno en la recuperación. Se encontró un detalle: el PR #10 se creó desde la rama `main` de la cuenta de pruebas en lugar de una rama propia, y eso no afectó al resultado. Para B06 conviene usar una rama con nombre propio, como indica `PLAN_PRUEBAS.md`.
- **Resultado al repetir la prueba:** pendiente. La repetición por otro integrante corresponde a B06.

## B05 — Permisos

**Resumen:** el 26/11/2026 por la noche se probó qué puede hacer cada nivel de acceso. La cuenta de pruebas (`tabordathomas-maker`) no pudo guardar directamente en `main` ni borrar el tag `v1.0.0`, y no tiene acceso a las opciones de administración del repositorio. Queda por capturar la lectura sin sesión.

- **Qué queremos comprobar:** lectura, actualización y administración están separadas.
- **Pasos para repetirla:** [PERMISOS.md, "Cómo demostrarlo"](PERMISOS.md).
- **Resultado esperado:** sin sesión se ve el sitio y no se edita; un cambio directo a `main` y el borrado de un tag `v*` son rechazados; solo el admin administra el repositorio.
- **Resultado observado y explicación:**

  | Prueba | Qué pasó | Por qué pasa |
  |---|---|---|
  | Ver el sitio publicado | La URL muestra "Versión 2", las tres experiencias y los estilos | GitHub Pages es público: para leer no se necesita permiso. La captura no permite saber si la ventana tenía sesión iniciada |
  | Guardar directo en `main` (cuenta de pruebas) | GitHub avisa *"You can't commit to main because it is a protected branch"* y solo ofrece crear una rama y un Pull Request. No quedó ninguna rama nueva ni cambio en `main` | La regla `proteger-main` exige que todo cambio entre por Pull Request |
  | Borrar el tag `v1.0.0` (usando la URL de la cuenta de pruebas) | Rechazado: `GH013: Repository rule violations`, *"Cannot delete this tag"*. El tag sigue existiendo en `a1c62ac` | La regla `proteger-versiones` impide borrar los tags `v*` |
  | Abrir *Settings* (cuenta de pruebas) | La pestaña **sí aparece**, pero dice *"You don't have access to repository options"* y solo ofrece *Secrets and variables* | Un colaborador con permiso de escritura puede gestionar secretos de Actions, pero no la configuración, las reglas ni los colaboradores |
  | Ver las reglas (admin) | `proteger-main` activa sobre `main`: exige Pull Request, impide borrar y forzar cambios. `proteger-versiones` activa sobre `v*`: impide actualizar, borrar y forzar cambios. Ambas sin excepciones (*Bypass list* vacía) | Solo el dueño del repositorio ve y cambia estas reglas |

- **Evidencia (sin credenciales):**

  Lectura del sitio publicado:

  ![B05: sitio publicado](evidencias/B05_lectura_sitio.png)

  **Descripción:** sitio público con "Versión 2", las tres experiencias y los estilos. La imagen no permite saber si había una sesión iniciada.

  Cambio directo a `main` bloqueado:

  ![B05: commit directo bloqueado](evidencias/B05_commit_directo_bloqueado.png)

  **Descripción:** la cuenta de pruebas edita `README.md` y GitHub avisa que no puede guardar en `main` porque es una rama protegida; solo ofrece crear una rama y un Pull Request.

  Borrado del tag rechazado:

  ![B05: borrado de tag rechazado](evidencias/B05_tag_protegido.png)

  **Descripción:** PowerShell con el intento de borrar `v1.0.0` usando la URL de la cuenta de pruebas. GitHub responde `GH013`, *Cannot delete this tag*, y rechaza el envío.

  Cuenta de pruebas: pestañas del repositorio y página de configuración:

  ![B05: pestañas vistas por la cuenta de pruebas](evidencias/B05_pestanas_cuenta_pruebas.png)

  **Descripción:** página principal del repositorio con la sesión de `tabordathomas-maker`. La pestaña *Settings* sí aparece.

  ![B05: configuración sin acceso](evidencias/B05_settings_cuenta_pruebas.png)

  **Descripción:** *Settings* abierto por la cuenta de pruebas: *"You don't have access to repository options"*; en el menú lateral solo figura *Secrets and variables*.

  Reglas vistas por el admin:

  ![B05: proteger-main, estado y destino](evidencias/B05_rulesets_main_1.png)

  **Descripción:** `proteger-main` en estado *Active*, sin excepciones (*Bypass list* vacía) y aplicada a `main`.

  ![B05: proteger-main, reglas](evidencias/B05_rulesets_main_2.png)

  **Descripción:** reglas marcadas en `proteger-main`: impedir borrados, exigir Pull Request antes de fusionar y bloquear *force push*.

  ![B05: proteger-versiones, estado y destino](evidencias/B05_rulesets_tags_1.png)

  **Descripción:** `proteger-versiones` en estado *Active*, sin excepciones y aplicada a `v*` (`v1.0.0` y `v2.0.0`).

  ![B05: proteger-versiones, reglas](evidencias/B05_rulesets_tags_2.png)

  **Descripción:** reglas marcadas en `proteger-versiones`: impedir actualizaciones y borrados, y bloquear *force push*.

- **¿Cumple?** Parcialmente. La actualización y la administración quedaron comprobadas. Para la lectura falta evidencia de que, **sin sesión**, el sitio se ve y la configuración no se puede abrir.
- **Error encontrado y ajuste:**
  1. `PLAN_PRUEBAS.md` esperaba que la cuenta de pruebas no viera la pestaña *Settings*. Sí la ve, con acceso limitado a *Secrets and variables*. Ajuste: comprobar el acceso por lo que permite la página, no por la presencia de la pestaña.
  2. La captura de `proteger-main` deja plegados los ajustes del Pull Request, así que no muestra el número de aprobaciones exigidas. *[pendiente: captura con "Show additional settings" abierto]*
- **Limitaciones:**
  - En un repositorio personal no hay rol de "solo lectura" ni roles intermedios; ver PERMISOS.md.
  - Todo colaborador puede gestionar los secretos de Actions. Hoy el proyecto no depende de ninguno.
  - Las dos cuentas usadas son de la misma persona (ver "Registro del equipo").

## B06 — Repetibilidad

**Estado: pendiente. Todavía no se ha realizado.**

- **Qué queremos comprobar:** que una integrante que no sea administradora pueda repetir el procedimiento de recuperación siguiendo únicamente las instrucciones documentadas.
- **Quién la repite:** Elisa María Plazas (no administradora).
- **Procedimiento propuesto:** recuperación mediante PROCEDIMIENTOS.md §4.2.
- **Resultado observado:** se publicó un error controlado mediante un Pull Request. Se identificó el commit del error (95adec0) y se ejecutó git revert -m 1 95adec0. Se publicó la rama recuperacion mediante un Pull Request y se restauró correctamente la Versión 2 en GitHub Pages.
- **Dudas que tuvo y qué se corrigió en la documentación:**  se aclaró la identificación del hash del merge, el uso del editor Vim y la conservación del commit de recuperación en una rama independiente.
- **Inicio, fin y duración:** 27/11/2026 16:28  hasta 27/11/2026 16:56. 28 minutos.
- **Evidencias:** B06_error.png, B06_error_simulado.png y B06_recuperado.png.
- **¿Cumple?**  Sí. Una integrante no administradora ejecutó satisfactoriamente el procedimiento documentado y verificó la recuperación de la versión correcta.


---

## Cierre

- **Qué funciona realmente:**
  - Publicación del sitio con GitHub Pages desde `/docs` de `main` (B01).
  - Actualización a la versión 2 por Pull Request con aprobación (B02).
  - Respaldo con huellas SHA-256, comprimido y subido a Google Drive (B03).
  - Recuperación de un error publicado con *revert*, en unos 4 minutos (B04).
  - Bloqueo de cambios directos a `main` y del borrado de tags, y administración restringida (B05).
- **Qué quedó como propuesta o pendiente:**
  - B05: evidencia de lectura sin sesión y del número de aprobaciones de `proteger-main`.
  - B06: repetición por otro integrante.
  - B03: confirmar que el ZIP esté en la carpeta de respaldos y compartirla con el equipo, sin enlace público.
- **Procedimiento para recrear y recuperar:** [PROCEDIMIENTOS.md](PROCEDIMIENTOS.md).
- **Limitaciones y cambios para el encuentro 3** (propuestas, no implementadas):
  - Usar una organización gratuita con roles separados (Read, Write, Admin).
  - Automatizar el respaldo con GitHub Actions.
  - Verificar automáticamente la URL después de cada despliegue.
