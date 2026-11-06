# Datos y Persistencia

## Descripción de la sección

Define qué información necesita conservar el juego y cómo se estructura.

## Datos persistentes

- Progreso: No aplica. Cada partida empieza desde cero.
- Configuración: Ajustes de audio, video, controles y accesibilidad de [[04 - Guardado y Configuración]].
- Inventario: No aplica. El arma, las mejoras y los cristales se pierden al terminar la partida.
- Estadísticas: No aplica. El resumen de la partida solo se muestra en Victoria y Game Over.
- Desbloqueos: No aplica.
- Otros: Por definir si los registros recuperados se conservan entre partidas.

## Modelo de datos

Describe las entidades y relaciones.

- **Configuración del jugador:** Se conserva entre ejecuciones. Agrupa audio (volumen general, música, efectos y voces), video (resolución, pantalla completa, filtro VHS y brillo), controles y accesibilidad (subtítulos y tamaño de texto).
- **Datos de balance:** Estadísticas del jugador, armas, enemigos, mejoras, generadores y oleadas en `ScriptableObject`, como indica [[01 - Arquitectura Técnica]]. Forman parte del juego y no cambian durante la ejecución. Sus valores salen de `AfterLight_Stats.xlsx`.
- **Estado de la partida:** Tiempo, salud, batería, nivel, cristales, mejoras elegidas, racha, generadores, enemigos y tickets del director. Permanece en memoria y se descarta al reiniciar, abandonar o terminar la partida.

## Formato

**Formato de guardado:** Por definir. Se propone `PlayerPrefs`, que el prototipo ya usa para recordar el modo del filtro VHS.

**Ubicación:** Por definir.

**Versionado de datos:** Por definir.

## Migraciones

¿Qué ocurre si cambia la estructura de los datos entre versiones?

Por definir. Como solo se conserva la configuración, se propone restablecer los valores predeterminados de un ajuste que no pueda leerse.


> **Navegación:** [[00 - Índice]] · ← [[03 - Requisitos Técnicos]] · [[05 - Seguridad y Riesgos Técnicos]] →
