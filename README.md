# Seguimiento de Actividad

**App publicada:** https://claude.ai/artifact/Pfr4h2AkxREzKFXiX66yBk (privada; se comparte desde el menú *Share* de la página).

App para llevar el registro fotográfico de los detalles que quedan en la revisión de una actividad de obra. Misma línea visual de Rendimientos AyC y Vale de Obra: panel en cristal sobre luz azul y naranja, modo oscuro y claro (recuerda la elección), logo de Arquitectura & Concreto blanco en oscuro y azul en claro, Sora / IBM Plex Sans / IBM Plex Mono.

## Pestañas

| Pestaña | Qué hace |
|---|---|
| Reporte | Filtros por piso, ubicación, estado (pendiente / corregido), fechas y texto. Muestra totales, cierre en %, detalles por piso y las tarjetas con foto. Cada detalle se marca **Corregido** (o se reabre), se edita o se borra. **Descargar reporte PDF** arma el informe con lo filtrado. |
| Registrar | Foto, piso, ubicación y descripción (más la fecha de revisión, hoy por defecto). En el celular abre la cámara; en el computador se puede arrastrar la imagen. Las ubicaciones frecuentes salen como botones rápidos. |
| Ajustes | Información de la actividad: nombre, obra, torre o etapa, contratista, responsable de la revisión, residente, fechas, estado, alcance, pisos (`1-12, Cubierta`) y ubicaciones frecuentes. Crear otra actividad o borrarla. |

Navegación: menú lateral en computador, solo íconos en pantallas medianas y barra inferior en el celular.

## Reporte PDF

Se genera en el navegador (jsPDF): encabezado con logo, datos de la actividad y el filtro usado, resumen (detalles, pendientes, corregidos, % de cierre), tabla por piso y el registro fotográfico, dos detalles por fila con número, estado, piso, ubicación, fecha y descripción.

## Datos

La app guarda todo en la base de datos del artefacto:

```
actividades/<id>                    información de la actividad (Ajustes)
actividades/<id>/detalles/<detId>   { fecha, piso, ubicacion, descripcion, foto: {asset | data, w, h}, estado, corregido, creado, editado }
```

Las fotos se reducen a 1600 px y se suben al almacenamiento del artefacto (solo quien puede editar). Si quien registra no tiene ese permiso, la foto va dentro del documento, reducida a 1100 px.

`app/index.html` es el código de la app; se publica en la misma URL cada vez que cambia, con los logos de `app/marca/`.
