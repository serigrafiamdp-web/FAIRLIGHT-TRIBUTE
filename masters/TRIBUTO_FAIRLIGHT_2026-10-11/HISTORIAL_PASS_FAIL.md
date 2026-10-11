# HISTORIAL CONSOLIDADO Y LECCIONES

- **SCROLL 12 PASS** — motor ECM estable; mantiene buffer de 40 y enmascara exterior 2..39.
- **SCROLL 13 FAIL** — temporizador nuevo de pausa produce flicker.
- **SCROLL 14 PASS** — 80 espacios silenciosos en lugar de nuevo temporizador.
- **SCROLL 15 PASS** — 100 espacios; sincronización SID.
- **SCROLL 16/17/18** — ajustes de 110,112,114 espacios para afinar sincronización.
- **SCROLL 19 PASS** — 116 espacios musicales.
- **SCROLL 20 PASS** — relato extendido (1440 chars), mover tabla a `$7E40`, sumar números/signos, no pisar código raster.
- **BORDER+SCROLL 01 FAIL** — llamada a `$1110` sin cuerpo; error de integración.
- **BORDER FINAL SCROLL 02 PASS** — recuperar trampolín faltante y pintura de columnas 1/40.
- **BORDER FINAL(1) 03** — cambio de texto a gris claro `$0F` aprobado; limpieza accidental de la fila 25 detectada.
- **BORDER FINAL(1) 04 PASS** — conservar fila 25 pintada y bordes, sin limpieza en init o IRQ. Base nativa de transiciones.
- **05 FAIL** — negro -> gris, cuelgue; retorno mal alineado en rutina de arranque.
- **06 FAIL** — gris en mitad del render: imagen/arte corrompido por intervención en IRQ.
- **07** — transición en preloader LZ, intro sin modificar: aparece frame inicial sucio.
- **08 FAIL** — primer frame limpio, pero congelado cerca del segundo frame con una sola nota SID: modificar IRQ resultó peligroso.
- **09 PASS PERFECTO** — negro -> gris -> arte limpio; revelar **antes de SID e instalación de IRQ** mediante un hook en arranque de una sola ejecución; programa principal continúa intacto.

## Disciplina de trabajo
Congelar MASTER confirmado por VICE y guardar SHA-256. Un cambio a la vez -> test nombrado -> PASS/FAIL. Nunca declarar PASS basándose solo en emulación reducida de CPU, LZ roundtrip o chequeos estáticos. Documentar el cambio concreto, direcciones de memoria y compatibilidad con animación + SID + scroll.