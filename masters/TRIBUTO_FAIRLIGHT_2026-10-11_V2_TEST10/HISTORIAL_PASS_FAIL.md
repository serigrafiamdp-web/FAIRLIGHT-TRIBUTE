# HISTORIAL PASS/FAIL — MASTER TRIBUTO FAIRLIGHT V2

- **SCROLL 12 PASS:** buffer de 40 caracteres interno; visible 2..39, estabilidad ECM.
- **SCROLL 13 FAIL:** espera cronometrada extra produjo flicker.
- **SCROLL 14 PASS:** espera por 80 caracteres vacíos sin cambiar IRQ.
- **SCROLL 15 PASS:** 100 espacios iniciales.
- **SCROLL 16-18:** ajustes 110,112,114 espacios de sincronía.
- **SCROLL 19 PASS:** 116 espacios, entrada sincronizada con Druid II.
- **SCROLL 20 PASS:** texto de 1440 caracteres, tabla reubicada fuera de raster, nuevos glifos.
- **BORDER + SCROLL 01 FAIL:** salto a subrutina ausente en `$1110`.
- **BORDER FINAL SCROLL 02 PASS:** runtime combinado estable, sin tocar columnas 1/40.
- **BORDER FINAL(1) 03:** gris claro aprobado, pero detectada limpieza de fila 25.
- **BORDER FINAL(1) 04 PASS:** conserva pintura de fila 25 y extremos.
- **TRANSICIÓN 05 FAIL:** pantalla negro -> gris; colgada en arranque.
- **TRANSICIÓN 06 FAIL:** intervención en IRQ corrompió arte.
- **TRANSICIÓN 07:** mostró frame sucio entre gris e intro.
- **TRANSICIÓN 08 FAIL:** frame limpio pero congeló animación y SID cerca de 2.º frame.
- **TRANSICIÓN 09 PASS PERFECTO:** revelar después de preparar primer frame, **antes de habilitar SID e IRQ**. Master original V1.
- **TEST10 REDUCED SCROLL PASS:** texto nuevo de 1289 caracteres, conserva exactamente la plataforma TEST09, menos 141 bytes en PRG comprimido. Promovido a **MASTER V2** 2026-10-11.

## Reglas

**Nunca sobrescribir la versión de referencia PASS anterior.** Cualquier cambio con un TEST nuevo, un cambio funcional aislado, verificar memoria y LZ + probar arte/audio/scroll en VICE, marcar PASS/FAIL. Solo promocionar un TEST aprobado.