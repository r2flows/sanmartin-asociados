# San Martín & Asociados

Landing de San Martín & Asociados (proyectos eléctricos).

**Producción:** https://sanmartin-asociados.cl (y `www`)

## Estructura

```
public/        raíz web servida por Caddy (index.html + img/)
Dockerfile     caddy:2-alpine
Caddyfile      binding a $PORT y cache headers
railway.json   builder DOCKERFILE
```

El sitio es una sola página: HTML, CSS, JS y fuentes van inline. Lo único
externo son las imágenes de `public/img/`.

Las fotos llegan por WhatsApp con nombres genéricos; las crudas quedan en
`originales/` (sin versionar) y cada una se guarda en `public/img/` con el
nombre que el HTML espera.

## Desarrollo local

```bash
docker build -t sma .
docker run --rm -p 8080:8080 -e PORT=8080 sma
# http://localhost:8080
```

## Deploy

```bash
railway up --service sanmartin-asociados
```

Esta carpeta vive dentro de `chatterbox`, que está enlazado al proyecto
Railway AgentLoop: pasar siempre `--service` para no heredar ese enlace.

## Pendientes

- [ ] **El formulario de cotización no envía nada.** Valida y muestra un
      aviso de "vista previa"; hay que conectarlo a un backend.
- [ ] Agregar `canonical`, `og:url` y `og:image` apuntando a
      `sanmartin-asociados.cl`; el HTML de diseño no los trae.
