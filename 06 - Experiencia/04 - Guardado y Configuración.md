# Guardado y Configuración

## Descripción de la sección

Define cómo se conserva el progreso y qué opciones puede modificar el jugador.

## Guardado

**Tipo:** Guardado automático de preferencias. Cada partida empieza desde cero.

**Cuándo se guarda:** Cada ajuste se guarda en el momento en que el jugador lo cambia. Solo se conserva la configuración, como indica [[01 - Arquitectura Técnica]].

**Qué datos se guardan:** Los ajustes de audio, video y accesibilidad; la resolución y la pantalla completa las recuerda Unity. El tiempo, el nivel, las mejoras, los cristales y los registros de una partida no se guardan.

**Cantidad de ranuras:** No aplica.

**Valores predeterminados:** `Configuracion` carga el valor predeterminado de cada preferencia que aún no existe en `PlayerPrefs`.

## Configuración

| Categoría | Opciones |
|---|---|
| Audio | Volumen general (80 %), música (60 %), efectos (90 %) y voces (100 %); entre paréntesis, el valor predeterminado |
| Video | Resolución, pantalla completa, filtro VHS (activado) y brillo (50 %) |
| Controles | Se muestran mover, interactuar, recargar, disparar y pausa; no pueden reasignarse |
| Accesibilidad | Subtítulos (activados) y tamaño de texto (normal) |
| Jugabilidad | No aplica |

En Unity se aplican el volumen general, la música, los efectos, la resolución y el modo de pantalla. Brillo, filtro VHS, voces, subtítulos y tamaño de texto se guardan como preferencias y queda pendiente aplicar sus efectos.

## Restablecimiento

¿Qué opciones pueden volver a valores predeterminados?

Ninguna. La pantalla de Opciones de [[02 - UI y Menús]] no tiene una opción para restablecer los valores predeterminados.


> **Navegación:** [[00 - Índice]] · ← [[03 - Accesibilidad]] · [[01 - Arquitectura Técnica]] →
