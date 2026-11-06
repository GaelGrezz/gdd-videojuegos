# Audio y Música

## Descripción de la sección

Define la identidad sonora y cómo el audio comunica información al jugador.

## Música

**Estilo:** Por definir.

**Instrumentación:** Por definir.

**Temas principales:** Tema de la partida, `gameplay.mp3`. Los temas del menú, del combate contra el Ascendido, de la victoria y de la derrota están por definir.

**Música dinámica:** Sí / No. Por definir.

## Efectos de sonido

| Evento | Sonido | Propósito |
|---|---|---|
| Disparo del arma inicial | `Disparo.m4a`, `Disparo2.m4a` y `Disparo3.m4a` | Confirmar el disparo, como pide [[04 - Controles]] |
| Golpe a un Vimer | `Veemers_Daño.m4a` | Confirmar el impacto |
| Daño recibido | `Daño_Jugador.mp3` y `Jugador_Daño.m4a` | Avisar que el soldado perdió salud |
| Pasos de los Vimers | `Veemer_Caminando.m4a` y `veemers_Caminando.m4a` | Indicar que un Vimer se acerca |
| Vimers | `veemers.m4a` y `veemers2.m4a` | Por definir |
| Generador dañado | `Generador_Dañado.m4a` | Avisar que un generador está recibiendo daño |
| Generador | `Generador1.m4a` | Por definir |
| Disparo del taser | `DisparoTaser.mp3` | Por definir |
| Batería baja | Por definir | Avisar que la linterna se está quedando sin carga |
| Sin asignar | `UT Cancún.m4a` y `UT Cancún 14.m4a` | Por definir |

## Audio espacial

¿Se utilizará audio posicional?

Por definir.

## Voz

**Narración:** Por definir.

**Diálogos hablados:** Por definir. Las comunicaciones de Nicolás e Issac deben entenderse mediante texto, como indica [[04 - Diálogos y Narrativa]].

**Idiomas:** Por definir. Los textos del juego están en español.

## Mezcla

Define prioridades, volumen relativo y comportamiento de la música ante eventos importantes.

El jugador ajusta por separado el volumen general, la música, los efectos y las voces en Opciones ([[02 - UI y Menús]]). Las comunicaciones de Nicolás no se superponen con otras voces ([[03 - Enemigos y NPC]]). Las prioridades y el comportamiento de la música ante eventos están por definir.

## Decisiones pendientes

- Elegir entre `Daño_Jugador.mp3` y `Jugador_Daño.m4a` para el daño recibido.
- Asignar un evento a `Generador1.m4a`, `veemers.m4a`, `veemers2.m4a`, `UT Cancún.m4a` y `UT Cancún 14.m4a`.
- `DisparoTaser.mp3` no corresponde a ningún arma del GDD.
- Faltan el aviso de batería baja, los sonidos de la interfaz y los del Ascendido, como la absorción que describe [[04 - Diálogos y Narrativa]].
- Los nombres de los archivos dicen *Veemer*; el [[01 - Glosario]] usa *Vimer*.


> **Navegación:** [[00 - Índice]] · ← [[04 - Interfaz Visual]] · [[01 - UX y Flujo del Jugador]] →
