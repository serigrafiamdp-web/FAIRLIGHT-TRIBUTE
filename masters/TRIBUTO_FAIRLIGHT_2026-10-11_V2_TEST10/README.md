# MASTER TRIBUTO FAIRLIGHT — V2 TEST10 REDUCED (PASS)

**Fecha de aprobación:** 2026-10-11. **Estado:** MASTER ACTUAL. Usuario confirmó el resultado tras la prueba TEST10 y pidió consolidarlo.

El binario definitivo es una copia **byte por byte** de `FAIRLIGHT_MASTER_TEST10_REDUCED_SCROLL_LZ_SFX.prg`. Se promovió sin recompilarlo ni modificar un solo byte.

- Archivo principal: `MASTER_TRIBUTO_FAIRLIGHT_V2_11_OCT_2026.prg`, 7167 bytes, SHA-256 `df39015ae0332cd6e6c9b13ecbc2a696524a4b2f59ce1de34dfa3c2684e134db`.
- Sin comprimir: `MASTER_TRIBUTO_FAIRLIGHT_V2_11_OCT_2026_UNPACKED.prg`, 31854 bytes, SHA-256 `62abf0c9d738d2344b1e4692e8b1003ec563a0b56cd21e6a86642e2242305f30`.
- Texto legible: `MASTER_TRIBUTO_FAIRLIGHT_V2_11_OCT_2026_SCROLL.txt`; el texto runtime se codifica como una sola línea con 3 espacios entre párrafos.
- Salto desde MASTER V1: **solo se sustituyó tabla de texto** (la parte ejecutable descomprimida fuera de `$7E40..$846C` permanece idéntica).

## PASSES incluidos

- Transición previa negro completo -> gris completo -> primer frame limpio, y continúa el programa sin colgarse (TEST09 PASS).
- Borde gris al aparecer el arte.
- 22 frames FAIRLIGHT y música SID Druid II.
- Scroll gris claro (`$0F`) en fila 24, columnas visibles 2 a 39.
- Respeto total a columnas pintadas 1 y 40, y a la fila 25 decorada.
- 116 espacios iniciales para sincronización musical; 24 espacios finales; la velocidad no cambió.
- Mensaje inglés **reducido a 1289 caracteres**, manteniendo la palabra `LOGO`, la historia de Suecia/Boca/D10S y los saludos originales.
- PRG autoextraíble con compresor LZ propio (no Exomizer).

## Respaldo histórico y flujo de trabajo

El MASTER V1/TEST09, 7308 bytes (SHA-256 `bee4a50a48598ccb570a1ad9129ccd556e548fec4d29a33ce90718a645896a9b`), se conserva intacto en `masters/TRIBUTO_FAIRLIGHT_2026-10-11/` y en Library. Este V2 sustituye al V1 **solo como referencia de desarrollo actual**, no lo borra.

En el repositorio GitHub los ficheros LVLLVL editables (`screens/`, `tile sets/`, etc.) siguen intactos. No existe todavía un pipeline reconstruible desde `asm/main.asm` hasta este PRG final: el ejecutable está archivado como artefacto binario aprobado.

Cambios futuros = crear nuevos TEST11+ -> confirmar PASS/FAIL en VICE -> entonces promover una nueva versión sin sobrescribir las copias fechadas.