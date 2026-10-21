# Reglas y Estados del Juego

## Descripción de la sección

Define las reglas globales y los estados que puede atravesar el videojuego.

## Estados principales

| Estado         | Descripción                                                                                                                           |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Menú principal | Permite iniciar una partida, consultar opciones, acceder a los créditos o salir.                                                      |
| Carga          | Prepara el escenario, al jugador, los generadores y los sistemas necesarios.                                                          |
| Jugando        | El jugador combate, recoge recursos, obtiene mejoras y repara generadores. El director recibe y utiliza tickets.       |
| Pausa          | Detiene temporalmente la simulación y permite consultar opciones o abandonar la partida.                                              |
| Victoria       | Se alcanza al derrotar al jefe final después del periodo de supervivencia establecido.                                                |
| Derrota        | Se activa cuando la salud llega a cero o se supera el tiempo permitido con la batería al 0 %. Detiene la partida y registra la causa. |
| Game Over      | Muestra el resultado de la derrota y permite reintentar o regresar al menú principal.                                                 |
| Créditos       | Muestra a los integrantes y colaboradores del proyecto.                                                                               |

## Transiciones

| Estado origen       | Evento                                      | Estado destino      | Condición                                                            |
| ------------------- | ------------------------------------------- | ------------------- | -------------------------------------------------------------------- |
| Menú principal      | Iniciar partida                             | Carga               | El jugador confirma el inicio                                        |
| Carga               | Finalizar preparación                       | Jugando             | Los elementos necesarios están listos                                |
| Jugando             | Alcanzar los cristales requeridos           | Selección de mejora | La partida sigue activa                                              |
| Selección de mejora | Confirmar una opción                        | Jugando             | Se aplica la mejora y se reinicia el contador de cristales           |
| Jugando             | Abrir pausa                                 | Pausa               | La partida no ha terminado                                           |
| Pausa               | Reanudar                                    | Jugando             | El jugador solicita continuar                                        |
| Pausa               | Abandonar partida                           | Menú principal      | El jugador confirma que desea salir                                  |
| Jugando             | Cumplir el tiempo de supervivencia          | Jugando: jefe final | El jefe todavía no ha aparecido y no existe una condición de derrota |
| Jugando             | Derrotar al jefe final                      | Victoria            | No se ha activado una condición de derrota                           |
| Jugando             | Salud del soldado igual a cero              | Derrota             | Se ha aplicado el daño correspondiente                               |
| Jugando             | Agotar el periodo de tolerancia sin batería | Derrota             | La batería permanece al 0 %                                          |
| Derrota             | Terminar la presentación de la derrota      | Game Over           | La causa y el resultado están registrados                            |
| Game Over           | Reintentar                                  | Carga               | El jugador inicia una nueva partida                                  |
| Game Over           | Salir                                       | Menú principal      | El jugador elige regresar                                            |
| Victoria            | Volver al menú                              | Menú principal      | El jugador confirma la opción                                        |
| Menú principal      | Consultar créditos                          | Créditos            | El jugador selecciona la opción                                      |
| Créditos            | Volver                                      | Menú principal      | El jugador cierra los créditos                                       |
## Reglas globales

1. La experiencia es para un solo jugador.
2. La partida avanza por tiempo. El director recibe tickets conforme transcurre y puede utilizarlos para introducir enemigos más peligrosos.
3. Cumplir el tiempo de supervivencia provoca la aparición del jefe final. La victoria requiere derrotarlo.
4. La salud del soldado al llegar a cero provoca una derrota.
5. La batería al llegar al 0 % inicia un periodo de tolerancia. Permanecer sin carga hasta agotarlo provoca una derrota.
6. Los generadores recuperan integridad al repararse. Un generador destruido puede recuperarse y su destrucción no provoca una derrota directa.
7. Los botiquines son la principal fuente de curación. Algunas mejoras permiten recuperar salud al cumplir condiciones específicas.
8. Los cristales permiten subir de nivel al jugador y escoger una mejora. El contador se reinicia al confirmar la selección.
9. La batería se recarga al permanecer cerca de un generador operativo. El prototipo no incluye moneda ni tienda.
10. La racha de eliminaciones no tiene límite máximo y se reinicia cuando el jugador recibe daño. Los potenciadores dependen de umbrales definidos.
11. Durante la pausa se detienen los enemigos, los proyectiles, las reparaciones, el consumo de batería, los efectos temporales, la generación de tickets y el reloj de partida.
12. Cada partida puede registrar un único resultado final. Tras una victoria o derrota, se detiene la simulación.
13. Durante la selección se detienen los enemigos, proyectiles, reparaciones, consumo de batería, efectos temporales, generación de tickets y reloj de partida.
## Casos especiales

### Salud del jugador y del jefe llegan a cero simultáneamente

La derrota tiene prioridad si ambas condiciones ocurren en la misma actualización del juego. Esta prioridad también aplica si se agota el tiempo sin batería al derrotar al jefe.

### Se cumple el tiempo de supervivencia mientras el jugador está en pausa

El reloj de partida permanece detenido. La aparición del jefe se evalúa al reanudar y alcanzar el tiempo requerido.

### Recuperación de batería durante el periodo de tolerancia

**Regla:** Recuperar carga por encima del 0 % cancela y reinicia el contador.

### Destrucción de uno o varios generadores

La partida continúa. Los generadores destruidos dejan de proporcionar sus beneficios hasta ser reparados. El jugador puede perder posteriormente por falta de salud o batería, pero no por la destrucción en sí.

### Pérdida de una racha

Recibir daño reinicia el contador de eliminaciones y los potenciadores.

### Cristales adicionales antes de elegir una mejora

El contador se reinicia al confirmar la mejora.

### Menú de mejoras

Es una interfaz disponible durante la partida en la que el juego debe estar en pausa.

### Comportamiento del director durante el jefe final

El director no recibe tickets ni genera enemigos mientras el jefe esté vivo. El jefe puede invocar sus propias entidades; su repertorio está por definir.

### Reinicio de partida

Reintentar restablece el tiempo, los enemigos, los generadores, la racha, las mejoras, los cristales y el resultado de la partida.

### Error durante la carga

La partida no comienza si faltan elementos indispensables. Debe mostrarse un mensaje y permitir reintentar la carga o regresar al menú principal.

> **Navegación:** [[00 - Índice]] · ← [[06 - Economía y Recursos]] · [[01 - Premisa y Trama]] →
