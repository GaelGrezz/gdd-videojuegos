# Audio y Música

## Descripción de la sección

Define la identidad sonora y cómo el audio comunica información al jugador.

## Música

**Estilo:** genero Dubstep.

**Instrumentación:** Bass, graves y armonizacion .

**Temas principales:** Tema de la partida, `Musica_Gameplay.mp3`. Los temas del menú, del combate contra el Ascendido, de la victoria y de la derrota están por definir.

**Música dinámica:**  No, Se propone que no, como en el prototipo: el tema de la partida se repite en bucle desde que empieza la escena, con una entrada de 2 s.

## Efectos de sonido

| Evento                   | Sonido                                     | Propósito                                                                                                       |
| ------------------------ | ------------------------------------------ | --------------------------------------------------------------------------------------------------------------- |
| Disparo del arma inicial | Variantes WAV en `Assets/Audio/Sound/Arma` | Confirmar el disparo, como pide [[04 - Controles]]                                                              |
| Golpe a un Vimer         | Variantes WAV `Vimer_Dano_*`               | Confirmar el impacto                                                                                            |
| Daño recibido            | Variantes WAV `Jugador_Dano_*`             | Avisar que el soldado perdió salud                                                                              |
| Pasos de los Vimers      | Variantes WAV `Vimer_Pasos_*`              | Indicar que un Vimer se acerca                                                                                  |
| Vimers                   | Variantes WAV `Vimer_Voz_*`                | Se proponen como gruñidos al preparar el golpe y cada 4 a 9 s mientras persiguen o buscan, como en el prototipo |
| Generador dañado         | Variantes WAV `Generador_Dano_*`           | Avisar que un generador está recibiendo daño                                                                    |
| Generador                | `Generador_Zumbido.wav`                    | Se propone como zumbido en bucle mientras el generador está operativo, como en el prototipo                     |
| Batería baja             | Bateria_Baja.mp3                           | Avisar que la linterna se está quedando sin carga                                                               |
|                          |                                            |                                                                                                                 |
| Jefe final               | JefeFinal.mp3                              | Musica que acompaña de fondo de ambiente del juego cuando se enfrenta con el jefe final                         |
|                          |                                            |                                                                                                                 |


## Audio espacial

¿Se utilizará audio posicional?

Se propone que sí, como en el prototipo: los sonidos de los Vimers se oyen desde su posición hasta 18 m y los del generador hasta 14 m. La música, el arma y el daño del soldado no son posicionales.

## Voz

**Narración:** sin narrador.

**Diálogos hablados:** no hay.

**Idiomas:** No hay.

## Mezcla

Define prioridades, volumen relativo y comportamiento de la música ante eventos importantes.

El jugador ajusta por separado el volumen general, la música, los efectos y las voces en Opciones ([[02 - UI y Menús]]). Las comunicaciones de Nicolás no se superponen con otras voces ([[03 - Enemigos y NPC]]). Las prioridades y el comportamiento de la música ante eventos están por definir. Se propone que la pausa y la selección de mejoras detengan los efectos y dejen sonar la música, como en el prototipo.

## Decisiones pendientes

- Verificar en partida los golpes de cada enemigo y la mezcla con el resto de efectos.


> **Navegación:** [[00 - Índice]] · ← [[04 - Interfaz Visual]] · [[01 - UX y Flujo del Jugador]] →
