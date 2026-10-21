# Mecánicas

## Descripción de la sección
## Mecánicas principales

### Mecánica 01: Linterna y batería

**Propósito:** La linterna permite al jugador debilitar a los infectados y controlar las amenazas dentro de un entorno de visibilidad limitada. Su batería añade una condición de supervivencia.

**Activación:** La linterna permanece encendida durante toda la partida y no puede apagarse. Se orienta con el cursor, el mismo que apunta el arma: la luz siempre cubre la dirección de disparo.

**Reglas:**

- La linterna proyecta un cono de luz.
- Los infectados dentro del cono reciben los efectos debilitantes que tenga equipada la linterna.
- Consume batería de forma continua mientras tenga carga.
- La batería se recarga al permanecer cerca de un generador operativo.
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


**Entrada:** Movimiento con teclado y apuntado con el ratón; el apuntado también orienta la linterna.

**Estado inicial:** Soldado equipado con un arma inicial y salud completa.

**Estado final:** El enemigo es eliminado, deja de estar al alcance, el jugador interrumpe el ataque o termina la partida.

**Recursos utilizados:** balas en el cargador.

**Recompensa:** Eliminación de amenazas, protección de los objetivos y posible avance de la racha de eliminaciones.

**Penalización:** Combatir expone al soldado a recibir daño y puede apartarlo de la reparación de los generadores.

**Interacciones con otras mecánicas:** Los efectos de la linterna influyen en los enfrentamientos. Las mejoras modifican las armas o al soldado. El director de enemigos determina qué amenazas pueden aparecer con el paso del tiempo.

**Casos límite:** Si un enemigo muere, este debe de dejar de tener un collider. Toda muerte de un enemigo incrementa la racha; recibir daño la reinicia (ver [[06 - Economía y Recursos]]).

### Mecánica 03: Reparación y defensa de generadores

**Propósito:** Da al jugador objetivos que debe atender mientras sobrevive. Los generadores sostienen la infraestructura y proporcionan fuentes de luz que pueden mejorar las propiedades de la linterna.

**Activación:** El jugador se acerca a un generador e inicia su reparación. La defensa ocurre al combatir a los infectados que lo amenazan.

**Reglas:**
- La reparación aumenta su progreso hasta alcanzar el estado operativo.
- Los infectados pueden dañar los generadores.
- El jugador puede invertir mejoras en los generadores.

**Entrada:** Acción de interacción cerca del generador; tecla "E". 

**Estado inicial:** Generador averiado; puede conservar progreso de reparación previo.

**Estado final:** Generador reparado y operativo, o destruido.

**Recursos utilizados:** Tiempo de reparación.

**Recompensa:** Mientras está operativo, permite recargar la batería de la linterna al permanecer cerca, ofrece una fuente de luz y otorga los beneficios asociados al generador.

**Penalización:** Reparar requiere tiempo y puede dejar al soldado expuesto

**Interacciones con otras mecánicas:** La linterna y las armas permiten despejar la zona para reparar. Las mejoras pueden reforzar el generador. Los enemigos seleccionados por el director pueden obligar al jugador a abandonar temporalmente la reparación para defenderlo.

**Casos límite:** el progreso de reparación se conserva, un generador operativo puede volver a dañarse, el generador se vuelve invulnerable durante unos segundos al ser reparado completamente.

### Mecánica 04: Director de enemigos y tickets

**Propósito:** Incrementa la dificultad durante la partida y permite variar la composición de las amenazas sin utilizar niveles como medida de progreso.

**Activación:** Funciona automáticamente mientras la partida está activa; no requiere una acción del jugador.

**Reglas:**

- El director recibe tickets conforme transcurre el tiempo.
- Cada tipo de enemigo tiene un costo en tickets.
- El director utiliza sus tickets disponibles para seleccionar enemigos que puede introducir en la partida.
- Al disponer de más tickets, puede elegir enemigos más peligrosos o modificar la composición de los grupos.
- Al cumplirse el tiempo establecido para la partida, se inicia el enfrentamiento con el jefe final.


**Entrada:** Tiempo transcurrido y estado actual de la partida.

**Estado inicial:** Un presupuesto inicial de tickets.

**Estado final:** La partida termina por victoria o derrota.

**Recursos utilizados:** Tickets del director.

**Recompensa:** No otorga una recompensa directa; genera variedad y una dificultad creciente para el jugador.

**Penalización:** La presión aumenta con el tiempo y puede dificultar el combate y la defensa de los generadores.

**Interacciones con otras mecánicas:** Determina las amenazas que el jugador enfrenta con la linterna y las armas, así como la presión ejercida sobre los generadores.

**Casos límite:** los enemigos dejan de aparecer si hay una cantidad enorme de entidades en el mapa. Mientras el jefe final está vivo, el director se pausa: no recibe tickets ni genera enemigos. El jefe puede invocar sus propias entidades (por definir).

## Mecánicas secundarias
- **Mejoras:** Permiten modificar la linterna, las armas o las defensas según las opciones disponibles durante la partida. Se obtienen al subir de nivel con cristales. En el prototipo no hay tienda.
- **Rachas de eliminaciones:** Las eliminaciones consecutivas pueden otorgar potenciadores acumulables. Recibir daño interrumpe la racha y anula los potenciadores. Falta definir qué potenciadores existen, sus umbrales y cuánto duran.
- **Encuentro con el jefe final:** Comienza al cumplirse el tiempo de supervivencia establecido. Derrotar al jefe es necesario para ganar la partida; sobrevivir hasta su aparición no constituye una victoria por sí solo.


> **Navegación:** [[00 - Índice]] · ← [[01 - Jugabilidad]] · [[03 - Sistemas]] →
