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

- **Configuración del jugador:** Se conserva entre ejecuciones. Agrupa audio (volumen general, música, efectos y voces), video (resolución, pantalla completa, filtro VHS y brillo) y accesibilidad (subtítulos y tamaño de texto).
- **Datos de balance:** Las cartas de mejora son `ScriptableObject`; las estadísticas del jugador, el arma, la Cáscara, el director y los generadores están en sus prefabs y en la escena. Forman parte del juego y no cambian durante la ejecución. Sus valores salen de `AfterLight_Stats.xlsx`.
- **Estado de la partida:** Tiempo, salud, batería, nivel, cristales, mejoras elegidas, racha, generadores, enemigos y tickets del director. Permanece en memoria y se descarta al reiniciar, abandonar o terminar la partida.

## Formato

**Formato de guardado:** `PlayerPrefs` de Unity, con una clave por ajuste: `AfterLight.VolumenGeneral`, `AfterLight.FiltroVHS`, etc.

**Ubicación:** El registro de Windows del usuario, donde Unity guarda `PlayerPrefs`.

**Versionado de datos:** Ninguno; cada clave guarda un solo valor.

## Migraciones

¿Qué ocurre si cambia la estructura de los datos entre versiones?

Un ajuste que no existe o no puede leerse toma su valor predeterminado. Como solo se conserva la configuración, no hay datos de partida que migrar.


> **Navegación:** [[00 - Índice]] · ← [[03 - Requisitos Técnicos]] · [[05 - Seguridad y Riesgos Técnicos]] →
