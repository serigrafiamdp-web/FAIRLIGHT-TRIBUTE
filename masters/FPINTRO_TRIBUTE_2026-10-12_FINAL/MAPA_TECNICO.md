# MAPA y contratos — FPINTRO-TRIBUTE MASTER

- PRG packed LZ SFX; native unpacked 31.854 bytes. Entrypoint bootstrap y rutina de scroll se conservaron del MASTER V2.
- SID Druid II en $7000-$74FF; init $7000, play $7003. IRQ musical $0C4C-$0C87 sin cambios según comparación con el MASTER anterior.
- Scroll de texto reducido con 116 espacios iniciales. Fila 24, columnas 2-39, color claro $0F; mantener 1/40 y fila 25.
- Transición negro/gris/reveal en etapa de arranque; evitar hooks extra en la IRQ por los fallos anteriores.
- Arte actualizado por `FAIRLIGHT TRIBUTE BORDER VER 2.prg`: 376 bytes de cambios preservados.
- El completo NO instala el apagado negro al final; continúa animando con scroll repetido.
- No hay pipeline completo de fuente reconstruible (el ejecutable, descomprimido y referencia visual constituyen los artefactos preservados).