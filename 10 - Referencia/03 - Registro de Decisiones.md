# Registro de Decisiones

## Descripción de la sección

Esta sección conserva las decisiones importantes del proyecto y el razonamiento detrás de ellas.

## Decisión

**Fecha:**

**Tema:**

**Problema:**

**Opciones consideradas:**

1.
2.
3.

**Decisión tomada:**

**Motivo:**

**Consecuencias:**

**Responsable:**

## Registro

| Fecha      | Tema                       | Decisión                                                                                                                                                                                                 | Responsable |
| ---------- | -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- |
| 2026-10-20 | Linterna                   | Permanece encendida toda la partida y se orienta con el mismo cursor que el arma; no tiene tecla de encendido                                                                                            |             |
| 2026-10-20 | Tienda y moneda            | Fuera del prototipo; las mejoras se obtienen solo al subir de nivel con cristales                                                                                                                        |             |
| 2026-10-20 | Plataforma                 | Solo PC con teclado y mouse; se descartan móvil, control y pantalla táctil                                                                                                                               |             |
| 2026-10-20 | Rachas                     | Se mantienen: recibir daño reinicia la racha y anula los potenciadores                                                                                                                                   |             |
| 2026-10-20 | Generadores                | Su destrucción no provoca derrota; interrumpe beneficios y recarga de batería hasta repararse                                                                                                            |             |
| 2026-10-20 | Batería                    | Se recarga al permanecer cerca de un generador operativo; recuperar carga reinicia el periodo de tolerancia                                                                                              |             |
| 2026-10-20 | Director y jefe            | El director se pausa mientras el Ascendido está vivo; el jefe puede invocar entidades propias                                                                                                            |             |
| 2026-10-20 | Nombres                    | Protagonista: Eco-10. Segundo enemigo: Quimera. Final normal: Información recuperada                                                                                                                     |             |
| 2026-11-02 | Balas                      | No son un recurso; el cargador es una característica del arma                                                                                                                                            |             |
| 2026-11-02 | Hades                      | Hades es un planeta                                                                                                                                                                                      |             |
| 2026-11-02 | Movimiento del jugador     | `PlayerController` usa `Rigidbody`                                                                                                                                                                       |             |
| 2026-11-02 | Duración                   | El juego tiene un solo nivel de 10 minutos                                                                                                                                                               |             |
| 2026-11-02 | Ascendido                  | Aparece al cumplirse los 10 minutos de supervivencia                                                                                                                                                     |             |
| 2026-11-02 | Curación                   | Se quitan los botiquines; la salud se regenera con el tiempo después de recibir daño                                                                                                                     |             |
| 2026-11-02 | Nombre de la organización  | CERBERUS es el nombre de la organización; C.E.R.B.E.R.U.S. es una variante gráfica                                                                                                                       |             |
| 2026-11-02 | Estilo de la interfaz      | Se diseña a 1920 × 1080 con texto mínimo de 14 px, una sola escala de estilos y los colores de la paleta                                                                                                 |             |
| 2026-11-04 | Escala del escenario       | El kit de CERBERUS y el generador se reducen ×0.4 a escala humana: 1 unidad de Blender = 1 unidad de Unity = 1 m, con un módulo de 2 m                                                                   |             |
| 2026-11-07 | Escala de las estadísticas | `AfterLight_Stats.xlsx` conserva los valores anteriores al ×2.4 (linterna 8 m, arma 12 m, movimiento 4.5 m/s), coherentes con la escala humana del escenario                                             |             |
| 2026-11-07 | Valores del prototipo      | `AfterLight_Stats.xlsx` adopta los valores de Unity: el soldado camina a 1.4 m/s y corre a 5 m/s con Shift, el arma inicial dispara 10 veces por segundo y no hay invulnerabilidad tras recibir un golpe |             |
| 2026-11-07 | Movimiento del jugador     | `PlayerController` usa `CharacterController` en lugar de `Rigidbody`, como el prototipo                                                                                                                  |             |
| 2026-11-08 | Valores de Unity           | Los valores implementados en Unity pasan a ser los del juego: Cáscara, director, generadores, cristales, regeneración y munición de reserva infinita. Lo que Unity aún no tiene sigue como propuesta |             |
| 2026-11-08 | Movimiento del jugador     | El soldado corre por defecto a 5 m/s y camina a 1.8 m/s mientras se mantiene Shift, al disparar o al moverse hacia atrás; reemplaza la decisión del 2026-11-07 |             |


> **Navegación:** [[00 - Índice]] · ← [[02 - Referencias e Inspiración]] · [[04 - Historial de Versiones]] →
