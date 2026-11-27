# Procedimientos

Escritos para que cualquier integrante pueda repetirlos (prueba B06). Comandos para la terminal, ejecutados desde la carpeta raíz del repositorio. En Windows, si `python` no existe, usen `py`.

## 0. Configuración inicial (una sola vez, la hace el admin)

1. **Settings → Pages → Build and deployment**
   - Source: **Deploy from a branch**
   - Branch: **main**, carpeta **/docs** → **Save**
   - Marcar **Enforce HTTPS** cuando aparezca disponible.
2. **Actions**: esperar a que el proceso *pages build and deployment* termine en verde (1–2 min).
3. **Settings → Pages**: copiar la URL que aparece en *"Your site is live at…"* y pegarla en el README y la bitácora.
4. Configurar la protección de `main` y el ruleset de tags (ver [PERMISOS.md](PERMISOS.md)).

## 1. Publicar la versión 1 (prueba B01)

1. Confirmar que `docs/index.html` muestra **Versión 1** y que el pie dice **v1.0.0**.
2. Abrir la URL en **ventana privada** y, si es posible, en un navegador distinto al usado para configurar.
3. Verificar que aparece "Versión 1", que el pie dice "v1.0.0" y que **se ven los estilos** (título morado).
4. Marcar el punto de recuperación:
   ```
   git checkout main
   git pull
   git tag v1.0.0
   git push origin v1.0.0
   ```
5. Captura con la URL visible y hora en la bitácora.

## 2. Respaldo independiente (prueba B03)

Se hace **antes** de cada actualización.

```
python scripts/herramientas.py preparar        # solo la primera vez: crea trabajo/ desde sitio_v1
```

Copiar en `trabajo/` la versión que está publicada (los archivos de `docs/`) y luego:

```
python scripts/herramientas.py respaldar
```

El script imprime una ruta tipo `respaldos/20261121_101500_123456`. Esa carpeta contiene `index.html`, `styles.css` y `manifest.json` con las huellas SHA-256.

1. Comprimir esa carpeta en un ZIP llamado `respaldo_vX.Y.Z_FECHA.zip`.
2. Subirlo a la carpeta compartida de Google Drive *[completar nombre]*.
3. Anotar en la bitácora: ruta, versión respaldada y archivos incluidos.

> `respaldos/` y `trabajo/` están en `.gitignore`: el respaldo vive en Drive, **fuera de GitHub**, que es el lugar que puede fallar.

## 3. Actualizar a la versión 2 (prueba B02)

```
git checkout main
git pull
git checkout -b actualizar-v2
```

1. Copiar `sitio_v2/index.html` y `sitio_v2/styles.css` dentro de `docs/` (reemplazar).
2. En `docs/index.html`, agregar en el footer `<br><small>v2.0.0</small>` antes de `</footer>`.
3. Probar en local:
   ```
   python -m http.server 8000 --bind 127.0.0.1 --directory docs
   ```
   Abrir http://127.0.0.1:8000 y comprobar "Versión 2" y "Ruta de espacios verdes". Detener con Ctrl+C.
4. Subir y abrir el PR:
   ```
   git add docs
   git commit -m "Publica versión 2.0.0 del catálogo"
   git push -u origin actualizar-v2
   ```
   En GitHub: **Compare & pull request** → el revisor aprueba → **Merge**.
5. Esperar el despliegue en **Actions**, verificar la URL en **ventana privada** y crear el tag:
   ```
   git checkout main
   git pull
   git tag v2.0.0
   git push origin v2.0.0
   ```

## 4. Recuperación después de un error (prueba B04)

**Cronómetro:** empieza cuando el error queda visible en la URL pública y termina cuando la URL pública (en ventana privada) muestra de nuevo la versión correcta. El tiempo de despliegue de Pages cuenta.

### 4.1 Provocar el error controlado

```
git checkout main
git pull
git checkout -b error-simulado
```

Reemplazar el contenido de `docs/index.html` por una página que diga **Catálogo incorrecto** (o borrar `docs/styles.css`). Commit, push, PR, aprobación y merge. Verificar que la URL muestra el error y **anotar la hora de inicio**.

> Ojo: el sitio puede seguir respondiendo HTTP 200 aunque el contenido esté mal. Se verifica mirando el contenido, no el código de respuesta.

### 4.2 Recuperar (procedimiento normal)

```
git checkout main
git pull
git log --oneline -5                 # identificar el commit del merge con el error
git checkout -b recuperacion
git revert -m 1 <HASH_DEL_MERGE>     # deshace el merge sin borrar historial
git push -u origin recuperacion
```

PR → aprueba el **revisor designado** → Merge → esperar Actions → verificar en ventana privada → **anotar la hora de fin**.

### 4.3 Recuperar desde un tag (alternativa)

Si no se sabe qué commit causó el error, se restaura `docs/` exactamente como estaba en la última versión buena:

```
git checkout main
git pull
git checkout -b recuperacion
git checkout v2.0.0 -- docs/
git commit -m "Restaura docs/ desde v2.0.0"
git push -u origin recuperacion
```

### 4.4 Procedimiento de emergencia

Si el revisor no está disponible y el sitio está mal publicado, el **admin** puede aprobar o hacer el merge saltándose la regla, solo para la recuperación. Debe dejar en la bitácora quién lo hizo, a qué hora y por qué.

### 4.5 Si GitHub falla por completo

Requisito: un clon local del repositorio hecho **antes** de la falla (el script vive en GitHub). Comandos desde la raíz de ese clon.

1. Descargar de Drive el último ZIP de respaldo.
2. Descomprimirlo **dentro de `respaldos/`**, de modo que quede `respaldos/NOMBRE_REAL/manifest.json` junto a `index.html` y `styles.css`. El script rechaza rutas fuera de `respaldos/`.
3. Si no existe la carpeta `trabajo/`, crearla primero:
   ```
   python scripts/herramientas.py preparar
   ```
4. Restaurar. El script compara las huellas SHA-256 antes de copiar y no copia nada si no coinciden:
   ```
   python scripts/herramientas.py restaurar --respaldo respaldos/NOMBRE_REAL
   ```
5. Demostrar en local con `python -m http.server 8000 --bind 127.0.0.1 --directory trabajo`, o subir `index.html` y `styles.css` a otro alojamiento estático.

## Problemas frecuentes

| Síntoma | Qué revisar |
|---|---|
| Se sigue viendo la versión anterior | Caché de Pages (~10 min). Ventana privada o Ctrl+Shift+R. Revisar que Actions terminó en verde. |
| Error 404 | Esperar 2 min; confirmar que Pages usa `main` + `/docs` y que el archivo se llama `index.html`. |
| Página sin estilos | `styles.css` debe estar en `docs/` con ese nombre exacto (minúsculas). |
| Puerto 8000 ocupado | Usar 8001 en el comando y en la URL. |
| El respaldo no coincide | Usar otro ZIP íntegro. **No** editar `manifest.json` para forzarlo. |
