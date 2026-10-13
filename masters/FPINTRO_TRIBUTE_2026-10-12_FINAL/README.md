# FPINTRO-TRIBUTE — MASTER actual (12 de octubre de 2026)

**Ejecutable vigente (sin apagado de video):** `MASTER_FPINTRO_TRIBUTE_12_OCT_2026.prg`

- PRG C64 autodescompresor custom LZ; tamaño **7039 bytes**.
- SHA-256 del PRG: `cbe8eb99b3e47aa3f643965b8be997cbd2a8cbf748b0fd3e05d668affb11a4e0`.
- Imagen descomprimida: **31854 bytes**, SHA-256 `88975c615f4212b9efafd7c22bca10920476e0e6d21cbc606177bd27f011cc64`.
- Origen visual: `FAIRLIGHT TRIBUTE BORDER VER 2.prg`, SHA-256 `0761c52ebb4491a5dc17e46b1931acfae251249395796cddc95422dcb8e8604c`.
- Se preservaron 376 cambios visuales de la última corrección respecto a `FAIRLIGHT TRIBUTE CORRECTED(1).prg`.

## Características

- Transición negro -> gris -> intro limpia, conservando el borde gris.
- 22 frames de animación Fairlight, música SID Druid II, scroll reducido de tributo a Suecia/Argentina.
- Scroll en fila 24, columnas 2-39, gris claro $0F; **116 espacios iniciales** para sincronización con Druid II.
- Fila 25 y columnas 1/40 decoradas, sin sobreescrituras del scroll.
- **La pantalla permanece encendida y el scroll vuelve a comenzar indefinidamente**. No se incluye la versión de captura con apagado a 650 frames.

## Preservación y validación

El binario y su descompresión LZ fueron verificados byte a byte y la integración respeta los bloques de música/IRQ comprobados. Esta combinación particular es promovida a MASTER por solicitud del usuario; **no hay aún en esta conversación una confirmación explícita de PASS en VICE para el nuevo BORDER VER 2**.

No reemplazar la instantánea histórica `MASTER_TRIBUTO_FAIRLIGHT_V2_11_OCT_2026` (en Library / repositorio histórico FAIRLIGHT-TRIBUTE). Mantener este MASTER versionado; cualquier revisión nueva se prueba como TEST y no debe sobrescribir los binarios anteriores sin indicación expresa.

