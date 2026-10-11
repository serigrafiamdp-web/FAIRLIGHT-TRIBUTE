# MAPA DE ARQUITECTURA — MASTER TRIBUTO FAIRLIGHT

Congelado **2026-10-11**, basado en **BORDER FINAL(1) SCROLL TEST09**. PASS en VICE.

## Binarios de referencia

- Packed LZ SFX: 7308 bytes, SHA256 `bee4a50a48598ccb570a1ad9129ccd556e548fec4d29a33ce90718a645896a9b`.
- Unpacked: 31854 bytes, SHA256 `f57315cce7daa54857cb571b463a2b4c8581ac0e83b2b868dfbafecd16b7b922`.
- Conservar hashes y PRG de respaldo sin modificar al hacer nuevas pruebas.

## Contrato funcional

- **Pantalla inicial:** negro completo, borde negro (~25 frames PAL); gris completo, borde gris (~40 frames PAL); entonces mostrar primer arte FAIRLIGHT limpio y continuar la animación.
- **CRÍTICO:** la transición se implementa en el preloader LZ y un enganche **de una sola ejecución** en el arranque nativo, ANTES de instalar el IRQ. No interferir con el raster IRQ.
- 22 frames animados y reproductor SID **Druid II**, init `$7000`, play `$7003`, sin cambios.
- Scroll mono-linea: **fila 24**, columnas **2 a 39**; ECM gray-light **$0F** sobre negro.
- **No sobrescribir** con espacio o color las columnas 1 y 40, ni borrar fila 25 pintada. Las columnas exteriores contienen arte del usuario.
- Texto actual: 1440 caracteres de homenaje + **116** caracteres vacíos iniciales para sincronización SID + 24 finales. El mensaje largo narra Suecia, Boca Juniors, D10S, Fairlight y greetings. Los 116 espacios se calibraron de a 2.
- Scroll utiliza buffer interno de 40 columnas, visibilidad 2..39, sin agregar temporizadores que introduzcan flicker.
- Preservar los 6 glifos ECM instalados para la puntuación y números del texto. Resto del tileset se conserva del arte BORDER FINAL(1).

## Regiones y puntos de entrada documentados

- `$08E6` SYS/bootstrap del cargador visual, con origen LZ trasladado desde `$0944`; mini handoff `$02C0`.
- `$0820` entrada al programa nativo, originalmente del TEST04.
- Preparación del primer frame `$0D86 -> $0E4E`. Una vez completada, hook único `$0C10 -> $1119` en TEST09: restablece la instrucción de inicio, activa DEN (`$D011` bit 4) y retorna a `$0C14` para SID e instalación IRQ **originales**.
- El IRQ principal `$0C4C..$0C87` queda **idéntico a TEST04 PASS** (no usar el wrapper de TEST08).
- `$1110..$1118`: subrutina instalada que necesita `$0EA5`; si falta (BORDER TEST01) el programa salta a código inválido.
- SID `$7000..$74FF`. Rutinas de scroll en `$7600..$76FF`.
- Texto largo almacenado en `$7E40..$846C`, desplazado del viejo sitio para evitar pisar rutinas raster alrededor de `$7D00`.
- Raster 38-column mode solamente en la franja scroll; los extremos quedan pintados en RAM, aunque pueden recortarse visualmente durante la franja.

## No regresiones

No modificar IRQ ni introducir contadores de espera para el texto. No reactivar el borrado de fila 25 ni pintar columnas 1/40. No fusionar otra imagen/tileset sin validar slots 56,57,58,59,60,62. Cada cambio en un nuevo PRG TEST con prueba PASS/FAIL en VICE.

## Fuente editable vs binario master

El proyecto LVLLVL disponible en GitHub contiene JSON de pantallas y tilesets, y `asm/main.asm` de demostración. **No se ha establecido un pipeline reproducible que genere este binario desde esos archivos.** Conservar ambos trabajos separados hasta documentar un ensamblado auténtico.