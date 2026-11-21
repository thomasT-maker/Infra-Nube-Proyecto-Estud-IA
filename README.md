# Ruta Local: publicación y respaldo de un sitio estático

Hackatón EstudIA, reto **Nube e infraestructura (nivel básico)**. Ruta Local es una organización ficticia; todo el contenido es sintético.

| | |
|---|---|
| **Sitio publicado** | https://thomast-maker.github.io/Infra-Nube-Proyecto-Estud-IA/ |
| **Versión actual** | v1.0.0 |
| **Alojamiento** | GitHub Pages, publicando desde la carpeta `/docs` de la rama `main` |
| **Copia independiente** | Carpeta compartida de Google Drive *[completar nombre]* |

## Estructura del repositorio

```
docs/              Lo ÚNICO que se publica: index.html, styles.css, .nojekyll
sitio_v1/          Versión 1 original del reto (no se modifica)
sitio_v2/          Versión 2 original del reto (fuente de la actualización)
scripts/           herramientas.py: respaldo con manifiesto SHA-256 y demo local
documentacion/     Procedimientos, permisos, esquema y bitácora de pruebas
```

> `docs/` es la carpeta que publica GitHub Pages. No pongan ahí archivos `.md`, PDF ni nada que no deba ser público.

## Documentación

- [Procedimientos: publicar, actualizar, respaldar y recuperar](documentacion/PROCEDIMIENTOS.md)
- [Permisos: lectura, actualización y administración](documentacion/PERMISOS.md)
- [Esquema de infraestructura](documentacion/ESQUEMA.md)
- [Bitácora de pruebas B01–B06](documentacion/BITACORA.md)

## Por qué GitHub Pages

- Es gratuito para repositorios públicos y no exige tarjeta ni contratar recursos.
- Da una dirección única con HTTPS, que resuelve el problema de las versiones que circulan por mensajería.
- Git guarda cada versión publicada, y los tags `v1.0.0` y `v2.0.0` marcan los puntos de recuperación.
- Con PR obligatorio y revisor, se separa quién propone cambios de quién los aprueba.

**Limitaciones:** el repositorio debe ser público; la caché de Pages tarda unos 10 minutos en renovarse; y si GitHub falla, el respaldo de Drive sirve para volver a publicar en otro alojamiento.
