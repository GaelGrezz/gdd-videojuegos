# UI y Menús

## Descripción de la sección

Define la estructura funcional de las interfaces y menús.

## Mapa de navegación

```text
Menú principal
├── Iniciar despliegue → Carga → Partida
├── Opciones (por diseñar)
├── Créditos (por diseñar)
└── Abandonar sistema → Salir del juego

Partida
├── ESC → Pausa
│   ├── Reanudar
│   ├── Opciones (por diseñar)
│   ├── Reiniciar partida → Carga
│   └── Abandonar sistema → Menú principal
├── Cristales completos → Elige una mejora → Partida
├── Derrota → Game Over (por diseñar) → Reintentar / Menú principal
└── Victoria (por diseñar) → Menú principal
```

## Pantallas

### Menú principal

**Propósito:** Iniciar la partida, consultar opciones o salir del juego.

**Elementos:** Emblema del lobo de Cerberus sobre el logotipo *AFTER LIGHT* («LIGHT» en rojo), el lema «La oscuridad te espera», un haz de luz diagonal, partículas y la ayuda de controles (↑ ↓ seleccionar, Enter confirmar).

![[UI - Menú principal.png]]

**Acciones disponibles:** Iniciar despliegue, Opciones y Abandonar sistema.

**Estados:** La opción seleccionada aparece en negrita, en un tono claro y con dos destellos a los lados; las demás, en gris y entre guiones.

**Transiciones:** Iniciar despliegue → Carga → Jugando. Abandonar sistema → Salir del juego.

### HUD

**Propósito:** Mantener visible durante la partida la información necesaria para decidir.

**Elementos:** Vida, generadores (nombre, estado y porcentaje), reloj hasta la llegada del Ascendido, nivel, cristales, racha, potenciadores, mira, indicación de interacción con E y su progreso, munición con aviso de recarga y mensajes de Enlace.

![[UI - HUD.png]]

**Acciones disponibles:** Ninguna directa; muestra el resultado de las acciones del jugador.

**Estados:** Generador operativo, en reparación o averiado; aviso de recarga cuando queda poca munición; indicación de interacción cuando hay un generador cerca. Por diseñar: batería de la linterna (normal, baja y vacía con cuenta regresiva), generador bajo ataque y destruido, vida del Ascendido y daño recibido.

**Transiciones:** ESC → Pausa. Cristales completos → Elige una mejora. Fin de la partida → Victoria o Game Over.

### Elige una mejora

**Propósito:** Elegir una mejora al subir de nivel. La partida permanece en pausa.

**Elementos:** Título «Subida de nivel / Elige una mejora», tres cartas (categoría, nombre, nivel actual sobre el máximo, efecto y botón Elegir) y el mensaje de Enlace.

![[UI - Elige una mejora.png]]

**Acciones disponibles:** Elegir una de las tres cartas.

**Estados:** Carta seleccionada (borde claro y botón rojo) o sin seleccionar.

**Transiciones:** Elegir → se aplica la mejora, el contador de cristales vuelve a cero y la partida continúa.

### Pausa

**Propósito:** Detener la simulación y permitir consultar opciones, reiniciar o abandonar la partida.

**Elementos:** Título «Sistema en espera / Pausa», el lema «La partida espera en la oscuridad», las opciones, un resumen de la partida (tiempo hasta el Ascendido, nivel, racha y generadores operativos) y la ayuda de controles (↑ ↓ seleccionar, Enter confirmar, ESC reanudar).

![[UI - Pausa.png]]

**Acciones disponibles:** Reanudar, Opciones, Reiniciar partida y Abandonar sistema.

**Estados:** Igual que el menú principal: opción seleccionada en negrita con destellos; las demás, en gris.

**Transiciones:** Reanudar o ESC → Jugando. Reiniciar partida → Carga. Abandonar sistema → Menú principal.

## Confirmaciones

Documenta acciones destructivas o irreversibles y cómo se confirman.

| Acción | Pantalla | Confirmación |
| --- | --- | --- |
| Abandonar la partida | Pausa | Diálogo que avisa que se perderá el progreso; *Cancelar* es la opción predeterminada |
| Reiniciar la partida | Pausa | Igual que abandonar: se pierden el tiempo, las mejoras y los cristales |
| Salir del juego | Menú principal | Opcional; no hay progreso que perder |

Reintentar desde Game Over no requiere confirmación.

## Decisiones pendientes

- Diseñar las pantallas de carga, opciones, victoria (*Información recuperada* y *Ni uno más*), derrota, Game Over, créditos y los diálogos de confirmación.
- Agregar la opción Créditos al menú principal.
- Mostrar al soldado frente a las puertas del complejo en el menú principal, como propone [[01 - Estructura del Contenido]].
- Usar textos distintos para *Abandonar sistema*: en el menú principal cierra el juego y en la pausa regresa al menú.
- Permitir el uso del mouse en todos los menús, además de las flechas y Enter.
- Unificar los datos de ejemplo: la pausa muestra 0/3 generadores operativos y el HUD de la misma partida muestra uno.
- Las cartas usan los valores del prototipo (por ejemplo, *Recolector magnético* +0.5 m) y no los del xlsx actual (+1.2 m).


> **Navegación:** [[00 - Índice]] · ← [[01 - UX y Flujo del Jugador]] · [[03 - Accesibilidad]] →
