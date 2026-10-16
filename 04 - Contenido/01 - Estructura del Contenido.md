# Estructura del Contenido

## Descripción de la sección

Organiza el contenido del videojuego en unidades manejables: mundos, capítulos, zonas, niveles, misiones y desafíos.

## Estructura

| Unidad                                  |Contenido|Forma de progresión|
| --------------------------------------- | ------------------------------------------------------------- | --------------------------------------------------------------- |
| Inicio                                  |Menú del soldado frente a las puertas y cinemática de entrada|El jugador selecciona Iniciar|
| Nivel único: Centro científico de Hades |Combate, exploración, reparación y defensa de generadores|Tiempo de juego transcurrido|
| Introducción                            |Contacto con Nicolás y presentación de las mecánicas|Primeros momentos de la partida y acciones del jugador|
| Supervivencia                           |Aumento de la presión mediante los tickets del director|El director recibe presupuesto conforme pasa el tiempo|
| Contenido opcional                      |Registros de operativos fallecidos y peticiones de Issac|Exploración y cumplimiento de condiciones específicas|
| Enfrentamiento final                    |Aparición del Ascendido dentro del mismo nivel|Alcanzar el tiempo establecido|
| Desenlace                               |Victoria normal, victoria «Ni uno más» o derrota|Resultado del combate y cumplimiento de las peticiones de Issac|

La introducción, la supervivencia y el enfrentamiento final son momentos de una misma partida, sin cambios de nivel ni pantallas de carga entre ellos.

### Progresión temporal

- El reloj comienza cuando el jugador recibe el control.
- Conforme transcurre el tiempo, el director obtiene tickets para generar enemigos y combinaciones más exigentes.
- Alcanzar el tiempo establecido provoca la aparición del Ascendido.
- La victoria requiere derrotarlo; cumplir el tiempo por sí solo no termina la partida.
- La pausa y la selección de mejoras detienen el reloj y la simulación.
- La duración total prevista, los intervalos de dificultad y el comportamiento del director durante el jefe están por definir.

### Progresión del personaje

La progresión temporal de la partida y la subida de nivel del soldado son sistemas distintos.

Los cristales obtenidos de los enemigos permiten subir de nivel y seleccionar mejoras. La moneda permite comprar armas y mejoras en la tienda. Estas acciones fortalecen al jugador, pero no adelantan el reloj ni desbloquean niveles de escenario.

### Contenido opcional

La exploración permite recuperar registros y cumplir las peticiones de Issac mientras se desarrolla la partida.

Completar estas peticiones habilita el final **Ni uno más**, siempre que el jugador también sobreviva y derrote al Ascendido. No completarlas permite obtener la victoria normal.

Los requisitos de Issac deben poder cumplirse dentro de la duración prevista de la partida.

## Cantidad estimada

| Tipo                                | Cantidad                                                                          |
| ----------------------------------- | --------------------------------------------------------------------------------- |
| Mundos                              | 1: Hades                                                                          |
| Niveles                             | 1: centro científico                                                              |
| Zonas internas                      | Por definir dentro del mismo mapa                                                 |
| Misiones principales                | 1 operación de intervención y supervivencia                                       |
| Peticiones secundarias              | Cadena de eventos "ni uno menos"; cantidad por definir                            |
| Tipos de enemigos regulares         | Cáscaras                                                                          |
| Enemigos por partida                | Variable según el tiempo, los tickets y los límites del director                  |
| Jefes                               | 1: el Ascendido                                                                   |
| NPC con interacción narrativa       | 2: Nicolás e Issac                                                                |
| Personajes fallecidos con registros | 28 propuestos; cantidad final ajustable al mapa                                   |
| Generadores                         | Por definir                                                                       |
| Objetos y equipo                    | Cristales, moneda, botiquines, armas y mejoras; cantidades y catálogo por definir |
| Finales de victoria                 | 2: Información recuperada y Ni uno más                                            |

Los operativos fallecidos son elementos narrativos del escenario, no NPC activos. Los dirigentes de Cerberus y el consejo pertenecen al trasfondo y no requieren encuentros propios.

## Dependencias

|Contenido|Debe existir antes|Motivo|
|---|---|---|
|Entrada desde el menú|Puertas, soldado y transición de cámara|Conectar el menú con el escenario jugable|
|Primer contacto con Nicolás|Entrada completada y control habilitado|Presentar la misión al comenzar la partida|
|Tutorial de combate|Movimiento, apuntado, linterna y ataque|Explicar acciones que el jugador ya puede ejecutar|
|Reparación y defensa|Generadores funcionales y sistema de daño|Permitir recuperar y proteger la infraestructura|
|Escalada de dificultad|Reloj, tickets y enemigos con costos definidos|Regular la presión durante la supervivencia|
|Selección de mejoras|Obtención de cristales y opciones de mejora|Ofrecer progresión al personaje y pausar hasta confirmar|
|Tienda|Moneda, catálogo y precios|Permitir compras coherentes con la economía|
|Registros recuperables|Autores, textos e interacción de recogida|Presentar testimonios y conservar la información descubierta|
|Peticiones de Issac|Condiciones de contacto y objetivos definidos|Permitir completar su contenido opcional|
|Aparición del Ascendido|Tiempo objetivo y espacio de combate preparado|Iniciar el enfrentamiento final dentro del nivel|
|Victoria normal|Derrota del Ascendido|Resolver la operación principal|
|Victoria Ni uno más|Derrota del Ascendido y peticiones de Issac completadas|Seleccionar el desenlace alternativo|
|Animaciones de derrota|Causa de muerte identificada|Reproducir la variante correspondiente y pasar a Game Over|

## Reglas de alcance

- No hay capítulos ni niveles adicionales.
- Las áreas del complejo no representan fases que deban superarse en un orden obligatorio.
- Reparar generadores no adelanta el tiempo ni cambia de escenario.
- Las mejoras por cristales no dependen de terminar una oleada.
- Los encuentros aumentan de dificultad dentro de la misma partida.
- La exploración opcional comparte escenario con la misión principal.
- Ambos finales de victoria reutilizan el mismo nivel y una puesta en escena breve.


> **Navegación:** [[00 - Índice]] · ← [[04 - Diálogos y Narrativa]] · [[02 - Niveles]] →
