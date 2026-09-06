# GIFTviewer

Aplicación HTML standalone (un solo archivo, cero dependencias) para crear, editar y exportar bancos de preguntas en formato **GIFT** (Moodle).

## Funcionalidades

### Edición de preguntas
- **Tres tipos** de pregunta: opción múltiple, verdadero/falso y respuesta corta.
- **Formulario visual** con pestañas y **editor RAW** (Markdown GIFT completo) integrado en la misma modal.
- **Búsqueda global** (atajo `/`) en enunciados, respuestas y retroalimentación.
- **Modo pantalla completa** (atajo `F`) con ajuste de línea activable.
- Edición inline de preguntas con formulario o directamente en GIFT.

### Persistencia
- Estado completo (preguntas, posición, nombre de archivo) se guarda automáticamente en `localStorage` y se restaura al recargar la pestaña o cerrar el navegador.

### Exportación a documento
La herramienta incluye una modal de configuración (atajo `Descargar ▾`) con opciones comunes para los tres formatos:

| Formato | Descripción |
|---------|-------------|
| **PDF** | Genera una portada personalizable (logo, nombre, fecha, instrucciones, criterios de corrección) y el listado de preguntas. Usa `window.print()` del navegador. |
| **TXT** | Archivo de texto plano. Las respuestas correctas se marcan con `**...**` (Markdown) salvo que se active la opción "no marcar en negrilla". |
| **RTF** | Formato rico compatible con Word/LibreOffice. Las respuestas correctas aparecen en **negrita**. Generado manualmente sin librerías externas. |

### Opciones de exportación (comunes a los tres formatos)
- **Título personalizado** del examen.
- **Aleatorizar el orden** de las respuestas (`shuffle` + hoja de soluciones).
- **No marcar en negrita** las respuestas correctas.
- **Portada** (solo PDF): logo con alineación configurable, campos de nombre y fecha, descripción, dos bloques de instrucciones, salto de página.

### Otros
- Modo claro/oscuro con paleta azul marino.
- Atajos de teclado (`←` `→` para navegar, `S` para solución, `L` para listado, `R` para editor RAW, `F` para pantalla completa, `/` para búsqueda, `Esc` para cerrar modales).
- Exportar/importar el banco completo en formato GIFT (descarga y carga de ficheros `.gift`).
- Merge de archivos GIFT (combinar con el banco actual: al principio, al final o después de la pregunta actual).
- Detector de errores de sintaxis GIFT con reporte detallado.

## Uso

Abrir directamente en cualquier navegador moderno. No necesita servidor, instalación ni conexión a internet.

## Tecnología

- **HTML + CSS + JavaScript** en un solo archivo (~100 KB).
- Sin librerías externas, frameworks ni API de red.
- Persistencia vía `localStorage`.
- Exportación PDF vía API nativa `window.print()` + `@media print`.
- Exportación TXT/RTF generada íntegramente en JavaScript (texto plano).

## Formato GIFT soportado

| Tipo | Sintaxis GIFT |
|------|---------------|
| Opción múltiple | `::Pregunta:: { =Respuesta1 ~Respuesta2 ~Respuesta3 }` |
| Verdadero/Falso | `::Pregunta:: { =Verdadero ~Falso }` |
| Respuesta corta | `::Pregunta:: { =respuesta1 =respuesta2 }` |

## Autor

Jose Sanchez — [jfsanchez.es](https://jfsanchez.es) — © 2026

Aviso: Código íntegramente generado con IA (OpenCode + BigPickle). Sólo cumple un propósito: Ser una herramienta no fácilmente extensible pero si fácilmente ejecutable.

Probado en Brave. Probablemente contenga errores de parsing en aperturas de llaves o escape de esos caracteres. Pensado para formatos GIFT simples (varias opciones, una correcta).

Permite ver un examen y generarlo en papel o reutilizar las preguntas de moodle a papel. Probado sólo con archivos GIFT generados a mano, probablemente fallen los complejos de moodle con imágenes u otros recursos.
