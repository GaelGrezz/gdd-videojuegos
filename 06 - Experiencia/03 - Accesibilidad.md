# Accesibilidad

## Descripción de la sección

La accesibilidad busca que el mayor número posible de jugadores pueda comprender y utilizar el videojuego.

## Estado de las opciones en Unity

Las casillas indican qué apoyos están disponibles. Los ajustes que solo guardan una preferencia se describen por separado.

- [ ] Tamaño de texto. La opción guarda la preferencia y queda pendiente aplicarla a la interfaz.
- [x] Comunicaciones en texto. Los mensajes de Enlace e Issac se muestran en pantalla. La opción Subtítulos guarda la preferencia y queda pendiente conectarla a la presentación.
- [ ] Contraste
- [ ] Modo para daltonismo
- [ ] Reasignación de controles
- [ ] Sensibilidad
- [ ] Reducción de movimiento
- [ ] Reducción de destellos
- [ ] Asistencia de apuntado
- [x] Volumen independiente
- [ ] Indicadores visuales para sonidos importantes. Ya hay avisos visuales de batería y de generadores bajo ataque.

## Consideraciones

Documenta cualquier necesidad específica derivada del diseño del juego.

- El objetivo es un mínimo de 14 px a 1920 × 1080 y el contraste definido en [[04 - Interfaz Visual]].
- Los estados de la batería y de los generadores combinan color, texto e icono, como pide la regla 8 de [[01 - Dirección de Arte]].
- Opciones guarda la preferencia del filtro VHS. Su efecto visual queda pendiente.
- Las comunicaciones de Enlace e Issac siempre se muestran como texto en pantalla.
- El volumen general, la música y los efectos tienen controles independientes. El volumen de voces queda disponible para cuando se incorporen diálogos hablados.


## Revisión en Unity

- Los avisos de batería baja, batería agotada y generador bajo ataque incluyen texto. La cobertura de otros eventos sonoros y el contraste sobre el escenario quedan pendientes de prueba visual.
- La configuración aplica el volumen general al oyente de Unity. La música y los efectos consultan sus niveles por separado. Tamaño de texto, subtítulos, brillo guardan sus valores. Sus efectos quedan pendientes.
- El HUD contiene destellos de daño y parpadeos, y la cámara se sacude con impactos y al aparecer el Ascendido. Opciones no ofrece un control para reducirlos. La verificación visual y sonora en partida queda pendiente.


> **Navegación:** [[00 - Índice]] · ← [[02 - UI y Menús]] · [[04 - Guardado y Configuración]] →
