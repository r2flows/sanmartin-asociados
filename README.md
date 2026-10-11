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

- [ ] **Faltan las imágenes.** El HTML referencia 17 archivos que no vinieron
      con la entrega; van en `public/img/` con estos nombres:
      `logo.png`, `montaje-altura.jpg`, `tablero-canalizacion.jpg`,
      `rotiseria.jpg`, `sala-proceso.jpg`, `rampa.jpg`, `bandeja-highbay.jpg`,
      `empalme-rural.jpg`, `estacionamiento.jpg`,
      `iluminacion-sala-ventas.jpg`, `tablero-distribucion.jpg`,
      `tableros-generales.jpg` y, en `clientes/`, `adventista-chillan.png`,
      `alborada-temuco.png`, `vd.png`, `super-ganga.png`,
      `banco-falabella.png`.
- [ ] **El formulario de cotización no envía nada.** Valida y muestra un
      aviso de "vista previa"; hay que conectarlo a un backend.
- [ ] Agregar `canonical`, `og:url` y `og:image` apuntando a
      `sanmartin-asociados.cl`; el HTML de diseño no los trae.
