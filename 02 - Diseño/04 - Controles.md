# Controles

## Descripción de la sección

Define la relación entre las acciones del jugador y las entradas físicas del dispositivo.

## Mapa de controles

| Acción                      | Teclado     | Mouse                 | Táctil      |
| --------------------------- | ----------- | --------------------- | ----------- |
| Mover                       | W, A, S, D  | —                     | Por definir |
| Apuntar                     | —           | Movimiento del cursor | Por definir |
| Interactuar con generadores | E           | —                     | Por definir |
| Disparar                    | —           | Clic izquierdo        | Por definir |
| Abrir menú de mejoras       | Por definir | —                     | Por definir |
| Cambiar de arma             | Por definir | Por definir           | Por definir |
| Abrir menú de pausa         | ESC         | —                     | Por definir |
## Principios de control

- El movimiento utiliza W, A, S y D, correspondientes a arriba, izquierda, abajo y derecha desde la perspectiva de la cámara.
- El apuntado sigue la posición del cursor.
- La interacción con objetos utiliza E y muestra una indicación cuando hay una acción disponible.
- Las acciones frecuentes deben poder ejecutarse sin combinaciones complejas.
- Cada entrada debe producir una respuesta visible o sonora que permita reconocer su resultado.
- Mientras un menú captura las entradas, los clics destinados a su interfaz no deben provocar disparos.
## Reasignación

Por definir. Se propone permitir la reasignación de las teclas de movimiento, interacción, cambio de arma y apertura de menús.

## Entrada y retroalimentación

| Entrada                               | Respuesta del juego                                    | Retroalimentación                                                            |
| ------------------------------------- | ------------------------------------------------------ | ---------------------------------------------------------------------------- |
| Presionar W, A, S o D                 | El soldado se desplaza en la dirección correspondiente | Movimiento y animación del personaje                                         |
| Mover el cursor                       | Cambia la dirección de apuntado                        | Orientación del soldado y del indicador de apuntado                          |
| Hacer clic izquierdo                  | El arma dispara si puede hacerlo                       | Animación, efecto visual y sonido del disparo                                |
| Presionar E cerca de un objeto válido | Se inicia la interacción disponible                    | Indicación visual de la acción y, cuando corresponda, progreso de reparación |
| Abrir el menú de mejoras              | Se muestran las opciones disponibles                   | Panel con la descripción y los efectos de cada mejora                        |
| Cambiar de arma                       | Se equipa otra arma disponible                         | Actualización del arma visible y de su indicador en la interfaz              |
| Abrir el menú de pausa                | Se muestra el menú de pausa                            | Panel de opciones y señal visual de pausa                                    |

> **Navegación:** [[00 - Índice]] · ← [[03 - Sistemas]] · [[05 - Progresión]] →
