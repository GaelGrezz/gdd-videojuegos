# Controles

## Descripción de la sección

Define la relación entre las acciones del jugador y las entradas físicas del dispositivo.

## Mapa de controles

| Acción                  | Teclado                                                       | Mouse                 |
| ----------------------- | ------------------------------------------------------------- | --------------------- |
| Mover                   | W, A, S, D o flechas                                          | —                     |
| Apuntar arma y linterna | —                                                             | Movimiento del cursor |
| Dash                    | Shift izquierdo, mantenido                                    | —                     |
| Interactuar con objetos | E breve para registros, mantenida para generadores y terminal | —                     |
| Disparar                | Enter durante la partida                                      | Clic izquierdo        |
| Recargar                | R                                                             | —                     |
| Abrir menú de mejoras   | Apertura automática al subir de nivel                         | —                     |
| Abrir menú de pausa     | ESC                                                           | —                     |

La plataforma es PC con teclado y mouse.

## Principios de control

- El movimiento utiliza W, A, S, D o las flechas desde la perspectiva de la cámara. El dash sustituye la acción de caminar que se activaba con Shift izquierdo. La duración, la distancia y el enfriamiento se documentarán al verificar la versión de Unity que lo incorpora.
- El apuntado sigue la posición del cursor y orienta a la vez el arma y la linterna. La bala sale de la boca del arma hacia el punto bajo el cursor, y durante la partida el cursor no puede salir de la ventana.
- La linterna no tiene tecla de encendido: permanece activa durante toda la partida.
- La interacción con objetos utiliza E y muestra una indicación cuando hay una acción disponible. Para reparar se mantiene E.
- Las acciones frecuentes deben poder ejecutarse sin combinaciones complejas.
- Cada entrada debe producir una respuesta visible o sonora que permita reconocer su resultado.
- Mientras un menú captura las entradas, los clics destinados a su interfaz no deben provocar disparos.
## Reasignación

No disponible: la pantalla de Opciones muestra los controles pero no permite cambiarlos. Se propone permitir la reasignación de las teclas de movimiento, interacción, cambio de arma y apertura de menús.

## Entrada y retroalimentación

| Entrada                               | Respuesta del juego                                    | Retroalimentación                                                            |
| ------------------------------------- | ------------------------------------------------------ | ---------------------------------------------------------------------------- |
| Presionar W, A, S o D                 | El soldado se desplaza en la dirección correspondiente | Movimiento y animación del personaje                                         |
| Mover el cursor                       | Cambia la dirección de apuntado                        | Orientación del soldado, del cono de luz y del indicador de apuntado         |
| Hacer clic izquierdo                  | El arma dispara si puede hacerlo                       | Animación, efecto visual y sonido del disparo                                |
| Presionar R                           | El arma se recarga; también ocurre al vaciar el cargador | Indicador de recarga en la interfaz                                          |
| Presionar E cerca de un objeto válido | Se inicia la interacción disponible                    | Indicación visual de la acción y, cuando corresponda, progreso de reparación |
| Abrir el menú de mejoras              | Se muestran las opciones disponibles                   | Panel con la descripción y los efectos de cada mejora                        |
| Abrir el menú de pausa                | Se muestra el menú de pausa                            | Panel de opciones y señal visual de pausa                                    |

## Estado en Unity

La copia local revisada conserva `Player/Sprint` en `InputHandler`. Con la configuración actual, mantener Shift reduce la velocidad de 5 a 1.8 m/s. El mapa de arriba recoge la decisión del dash. Su activación queda pendiente de verificar en la versión que lo integre.

## Cobertura de dispositivos

El asset contiene asignaciones de mando para acciones como movimiento y ataque. El apuntado actual lee el mouse, por lo que la plataforma documentada sigue siendo PC con teclado y mouse. La partida usa un único rifle.


> **Navegación:** [[00 - Índice]] · ← [[03 - Sistemas]] · [[05 - Progresión]] →
