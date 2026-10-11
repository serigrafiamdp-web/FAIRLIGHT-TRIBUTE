# MAPA TÉCNICO — MASTER TRIBUTO FAIRLIGHT V2

**Base:** TEST09 PASS negro -> gris -> intro limpia. **Único cambio de TEST10:** tabla de texto del scroll (1289 vs. 1440 caracteres).

## Memoria y ejecución

- Loader LZ SFX al ejecutar: transición negra (~25 cuadros PAL), gris (~40 cuadros), descompresión y arranque limpio.
- SYS/bootstrap de preloader alrededor de `$08E6`, cargador a partir de `$0944`, mini handoff `$02C0`.
- Entrada nativa `$0820` (programa aprobado). Primer frame preparado antes de revelar display. Hook de revelado **una sola vez** en `$0C10 -> $1119`, retorno a `$0C14`; **no inyectar wrappers en IRQ**.
- IRQ raster principal `$0C4C..$0C87` en funcionamiento TEST04/09 aprobado.
- Sprite/animación 22 frames; SID Druid II inicia `$7000`, play `$7003` en IRQ.
- Rutinas de scroll alrededor de `$7600..$76FF`; datos de mensaje en `$7E40..$846C`, reinicio usando terminador `$FF`.
- En V2 terminador de mensaje `$83D5`; espacio posterior hasta el límite del área original se limpió para evitar residuos.
- Scroll se dibuja en **fila 24**, columnas **2..39**, Color RAM gris claro `$0F`, caracteres ECM; conserva columnas exteriores 1 y 40 sin escrituras.
- **Fila 25 pintada**: no ejecutar ninguna de las limpiezas antiguas.
- Posiciones de glifos especiales ECM 56,57,58,59,60,62: preservar, no alterar el logo.

## Texto y sincronía

- 116 glifos blancos/negros vacíos iniciales (visualmente no aparecen); calibrados para comenzar en frase musical de Druid II.
- 1289 caracteres de mensaje vs. 1440 del V1; se mantienen 24 espacios finales antes de reiniciar.
- Al acortar el texto, la duración total de cada vuelta disminuye; **la primera aparición** sigue sincronizada con los 116 espacios.
- Pasos de scroll de 1 pixel/cuadro PAL; mantener un solo motor sin contador de pausas o IRQ extra (TEST13 introducía flicker).

## Integridad

- MASTER actual packed 7167 bytes SHA-256 `df39015ae0332cd6e6c9b13ecbc2a696524a4b2f59ce1de34dfa3c2684e134db`.
- MASTER actual unpacked 31854 bytes SHA-256 `62abf0c9d738d2344b1e4692e8b1003ec563a0b56cd21e6a86642e2242305f30`.
- BASE V1 packed SHA-256 `bee4a50a48598ccb570a1ad9129ccd556e548fec4d29a33ce90718a645896a9b`.
- TEST10 informe técnico de construcción: se verificaron 928 ticks de espera, primer glifo, doble buffer, extremos, terminador/reset, propagación de puntero entre páginas y LZ byte a byte. La validación en VICE corresponde al usuario.

**Nota:** `asm/main.asm` de LVLLVL no compila este PRG final en su estado actual. Evitar afirmaciones de reconstrucción desde fuente hasta documentar las transformaciones/builder real.