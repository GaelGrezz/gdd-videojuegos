# Mecánicas

## Descripción de la sección

Una mecánica es una regla o interacción mediante la cual el jugador puede actuar dentro del sistema del juego.

Documenta cada mecánica con suficiente detalle para que otro integrante pueda implementarla.

## Mecánicas principales

### Mecánica 01: Linterna y batería

**Propósito:** La linterna permite al jugador debilitar a los infectados y controlar las amenazas dentro de un entorno de visibilidad limitada. Su batería añade una condición de supervivencia.

**Activación:** La linterna permanece encendida durante toda la partida y no puede apagarse. Se orienta con el cursor, el mismo que apunta el arma: la luz siempre cubre la dirección de disparo.

**Reglas:**

- La linterna proyecta un cono de luz.
- Los infectados dentro del cono reciben los efectos debilitantes que tenga equipada la linterna.
- Consume batería de forma continua mientras tenga carga.
- La linterna tiene 8 m de alcance, un cono de 60° y requiere línea de visión. La debilidad aplica +25 % de daño recibido y dura 0.5 s después de salir del haz. Cada generador operativo añade 1 m y 5° al cono.
- La batería parte con 100 unidades, consume 0.5 por segundo fuera del radio de recarga y permite 5 s a cero antes de la derrota. Al agotarse, la luz conserva el 15 % de intensidad y el 50 % de alcance visual, y deja de aplicar debilidad.
- Cuando la batería llega al 0 %, la linterna deja de aplicar sus efectos pero sigue proyectando un poco de luz.
- Si permanece al 0 % durante el tiempo límite establecido, el jugador pierde la partida.
- Las mejoras pueden modificar las propiedades de la linterna y sus efectos sobre los enemigos.


**Entrada:** Movimiento del cursor, compartido con el apuntado del arma.
**Estado inicial:** Linterna disponible, con carga inicial y estadísticas base.
**Estado final:** La batería se agota o termina la partida.
**Recursos utilizados:** Carga de batería.
**Recompensa:** Los enemigos iluminados quedan debilitados, lo que facilita enfrentarlos.

**Penalización:** El consumo de batería es constante. Permanecer demasiado tiempo sin carga provoca una derrota.

**Interacciones con otras mecánicas:** La linterna facilita el combate; los generadores pueden mejorar sus propiedades; las mejoras elegidas por el jugador modifican su funcionamiento.

**Casos límite:** Si un enemigo sale del cono de luz, debe dejar de recibir el efecto directo de la linterna. La duración de cualquier efecto que permanezca después de iluminarlo depende del enemigo y la mejora. Recuperar batería por encima del 0 % cancela y reinicia el periodo de tolerancia.

### Mecánica 02: Combate contra infectados

**Propósito:** Permite al jugador sobrevivir, proteger los generadores y abrir oportunidades para repararlos.

**Activación:** El jugador apunta y utiliza un arma contra los infectados.

**Reglas:**
- Los ataques afectan a los enemigos según el daño y funcionamiento del arma utilizada.
- Los efectos de la linterna pueden modificar la vulnerabilidad de los enemigos.
- Los infectados pueden atacar al soldado o amenazar los generadores.
- Las eliminaciones consecutivas pueden activar potenciadores asociados a una racha.
- Si la salud del soldado llega a cero, la partida termina.


**Entrada:** Movimiento con teclado y apuntado con el mouse; el apuntado también orienta la linterna.

**Estado inicial:** Soldado equipado con un arma inicial y salud completa.

**Estado final:** El enemigo es eliminado, deja de estar al alcance, el jugador interrumpe el ataque o termina la partida.

**Recursos utilizados:** Ninguno.

**Recompensa:** Eliminación de amenazas, protección de los objetivos y posible avance de la racha de eliminaciones.

**Penalización:** Combatir expone al soldado a recibir daño y puede apartarlo de la reparación de los generadores.

**Interacciones con otras mecánicas:** Los efectos de la linterna influyen en los enfrentamientos. Las mejoras modifican las armas o al soldado. El Director de IA determina qué amenazas pueden aparecer con el paso del tiempo.

**Casos límite:** Si un enemigo muere, este debe dejar de tener un collider. Toda muerte de un enemigo incrementa la racha; recibir daño la reinicia (ver [[06 - Economía y Recursos]]).

### Mecánica 03: Reparación y defensa de generadores

**Propósito:** Da al jugador objetivos que debe atender mientras sobrevive. Los generadores sostienen la infraestructura y proporcionan fuentes de luz que pueden mejorar las propiedades de la linterna.

**Activación:** El jugador se acerca a un generador e inicia su reparación. La defensa ocurre al combatir a los infectados que lo amenazan.

**Reglas:**
- La reparación aumenta su progreso hasta alcanzar el estado operativo.
- Los infectados pueden dañar los generadores.
- El jugador puede invertir mejoras en los generadores: *Carcasa reforzada* (GEN-001) suma 25 de integridad máxima por nivel y *Bobinas de inducción* (GEN-002), 4 de energía por segundo a la recarga de la batería, hasta el nivel 4.

**Entrada:** Acción de interacción cerca del generador; tecla "E". 

**Estado inicial:** Generador averiado; puede conservar progreso de reparación previo.

**Estado final:** Generador reparado y operativo, o destruido.

**Recursos utilizados:** Tiempo de reparación.

**Recompensa:** Mientras está operativo, permite recargar la batería de la linterna al permanecer cerca, ofrece una fuente de luz y otorga los beneficios asociados al generador.

**Penalización:** Reparar requiere tiempo y puede dejar al soldado expuesto

**Interacciones con otras mecánicas:** La linterna y las armas permiten despejar la zona para reparar. Las mejoras pueden reforzar el generador. Los enemigos seleccionados por el director pueden obligar al jugador a abandonar temporalmente la reparación para defenderlo.

**Casos límite:** Recibir daño interrumpe la reparación y obliga a soltar y volver a pulsar E. Se conserva el progreso. También se puede restaurar la integridad de un generador operativo. Al completar una reparación o restauración, la siguiente intervención queda bloqueada durante 20 s. La destrucción bloquea la reparación durante 60 s. Al volver a quedar operativo, el generador es invulnerable durante 3 s. El HUD indica el tiempo de espera.

### Mecánica 04: Director de IA y tickets

**Propósito:** Incrementa la dificultad durante la partida y permite variar la composición de las amenazas sin utilizar niveles como medida de progreso.

**Activación:** Funciona automáticamente mientras la partida está activa; no requiere una acción del jugador.

**Reglas:**

- El director recibe tickets conforme transcurre el tiempo. Su ingreso crece de 0.25 a 1 ticket por segundo durante los 10 minutos de la partida.
- Cada tipo de enemigo tiene un costo en tickets.
- El director utiliza sus tickets disponibles para seleccionar enemigos que puede introducir en la partida. Decide cada 2 s y nunca gasta más de lo que tiene.
- Al disponer de más tickets, puede elegir enemigos más peligrosos o modificar la composición de los grupos. Los grupos crecen de 1 a 4 enemigos durante la partida.
- Desde el segundo 180 el director da prioridad a una Quimera. Después de una aparición prioritaria vuelve a programarla a los 45 s. Cuando le toca, ahorra 3 tickets. La aparición espera si falta presupuesto, espacio dentro del tope de enemigos o un punto válido del NavMesh.
- El inicio es tranquilo para que el jugador explore: el director decide por primera vez a los 20 s y el tope de enemigos vivos sube de 3 a 12 durante los primeros 4 minutos.
- Al cumplirse el tiempo establecido para la partida, se inicia el enfrentamiento con el jefe final.


**Entrada:** Tiempo transcurrido y estado actual de la partida.

**Estado inicial:** Un presupuesto inicial de 3 tickets.

**Estado final:** La partida termina por victoria o derrota.

**Recursos utilizados:** Tickets del director.

**Recompensa:** No otorga una recompensa directa; genera variedad y una dificultad creciente para el jugador.

**Penalización:** La presión aumenta con el tiempo y puede dificultar el combate y la defensa de los generadores.

**Interacciones con otras mecánicas:** Determina las amenazas que el jugador enfrenta con la linterna y las armas, así como la presión ejercida sobre los generadores.

**Casos límite:** los enemigos dejan de aparecer si hay una cantidad enorme de entidades en el mapa; el máximo es de 12 enemigos vivos, que se alcanza a los 4 minutos; al empezar son 3. Mientras el jefe final está vivo, el director se pausa: no recibe tickets ni genera enemigos. Las invocaciones del jefe siguen como propuesta de diseño.

## Mecánicas secundarias
- **Mejoras:** Permiten modificar la linterna, las armas o las defensas según las opciones disponibles durante la partida. Se obtienen al subir de nivel con cristales. En el prototipo no hay tienda.
- **Rachas de eliminaciones:** Las eliminaciones consecutivas otorgan potenciadores acumulables: +15 % de daño a las 5, +15 % de cadencia a las 10 y +10 % de velocidad al correr a las 20. Duran mientras dure la racha: recibir daño la interrumpe y anula todos los potenciadores.
- **Regeneración de salud:** Después de recibir daño, la salud del soldado se recupera con el tiempo, sin superar la salud máxima. Empieza 5 s después del último golpe y recupera 2 PV/s; un nuevo golpe reinicia la espera.
- **Encuentro con el jefe final:** Comienza al cumplirse el tiempo de supervivencia establecido. Derrotar al jefe es necesario para ganar la partida; sobrevivir hasta su aparición no constituye una victoria por sí solo.

## Decisiones pendientes

- Efectos de la linterna: [[02 - Visión del Juego]] menciona diferentes debuffs; el prototipo aplica solo +25 % de daño.
- Estructuras de defensa: aparecen en [[02 - Visión del Juego]], [[04 - Pilares de Diseño]] y en la combinación Tower Defense, pero no tienen mecánica. Falta diseñarlas o quitarlas.


> **Navegación:** [[00 - Índice]] · ← [[01 - Jugabilidad]] · [[03 - Sistemas]] →
