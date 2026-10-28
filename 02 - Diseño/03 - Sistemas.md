# Sistemas del Juego

## Descripción de la sección

Los sistemas son conjuntos de reglas y componentes que trabajan juntos: combate, inventario, IA, diálogo, progresión, economía, misiones, etc.

## Inventario de sistemas

| Sistema                          | Propósito                                                        | Dependencias                                       | Estado |
| -------------------------------- | ---------------------------------------------------------------- | -------------------------------------------------- | ------ |
| Jugador y supervivencia          | Gestionar salud, batería y derrota                               | Linterna, combate, objetivos                       | Prototipo |
| Linterna y efectos de luz        | Debilitar infectados mediante un cono de luz                     | Jugador, enemigos, mejoras, generadores            | Prototipo |
| Combate                          | Resolver ataques, daño y eliminaciones                           | Jugador, enemigos, linterna                        | Prototipo |
| Generadores                      | Gestionar reparación, daño, defensa y beneficios                 | Jugador, combate, enemigos                         | Prototipo |
| Director de enemigos             | Seleccionar amenazas mediante tickets que aumentan con el tiempo | Tiempo, catálogo de enemigos, estado de la partida | Prototipo |
| Mejoras y potenciadores          | Modificar las herramientas y capacidades del jugador             | Linterna, combate, generadores, rachas             | Prototipo parcial |
| Objetivos y resultado de partida | Determinar la aparición del jefe final, la victoria y la derrota | Todos los sistemas anteriores                      | Prototipo parcial |

## Relaciones entre sistemas

## Sistema: Jugador y supervivencia

**Objetivo:** Mantener el estado del soldado y determinar si puede continuar la partida.

**Entradas:** Daño recibido, carga y consumo de batería, recuperación de batería por cercanía a generadores operativos.

**Procesamiento / reglas:** La salud disminuye al recibir daño. La batería disminuye al utilizar la linterna. Si la salud llega a cero, la partida termina. Si la batería permanece al 0 % durante el tiempo límite, también termina.

**Salidas:** Salud y batería actuales, avisos de peligro y evento de derrota.

**Estados posibles:** Activo, sin batería, derrotado.

**Dependencias:** Combate, linterna, generadores y sistema de objetivos.

**Interacciones:** Recibe daño del combate y el estado de batería de la linterna; comunica una derrota al sistema de objetivos.

**Datos que necesita:** Salud máxima y actual, capacidad y carga de batería, tiempo permitido al 0 %.

**Datos que genera:** Cambios de salud y batería, tiempo acumulado sin carga y causa de derrota.

**Riesgos:** Que el jugador no perciba cuándo está cerca de perder por falta de batería.

**Criterios de aceptación:** La interfaz refleja los valores actuales; llegar a cero de salud causa una derrota; recuperar carga antes del límite evita la derrota por batería.

## Sistema: Linterna y efectos de luz

**Objetivo:** Determinar qué enemigos reciben la luz y qué efectos debilitantes se les aplican.

**Entradas:** Posición del jugador, orientación del cursor (compartida con el arma), batería disponible, posición de los enemigos y mejoras equipadas.

**Procesamiento / reglas:** El sistema calcula el cono de luz y detecta a los enemigos alcanzados. Aplica los efectos correspondientes y consume batería de forma continua, ya que la linterna permanece siempre encendida. Sin carga, no aplica efectos.

**Salidas:** Enemigos afectados, efectos activos, consumo de batería y respuesta visual de la luz.

**Estados posibles:** Encendida, sin batería.

**Dependencias:** Jugador, enemigos, batería y mejoras.

**Interacciones:** Envía efectos al sistema de combate. Recibe modificaciones del sistema de mejoras y beneficios de los generadores cuando corresponda.

**Datos que necesita:** Alcance y ángulo del cono, consumo de batería, efectos disponibles y estadísticas modificadas por mejoras.

**Datos que genera:** Enemigos iluminados, inicio y fin de efectos, batería consumida.

**Riesgos:** Que no sea evidente si un enemigo está dentro del cono o qué efecto recibió.

**Criterios de aceptación:** Solo los enemigos alcanzados reciben el efecto; el efecto coincide con las mejoras equipadas; la batería se consume según la regla establecida; los enemigos afectados muestran una señal reconocible.

## Sistema: Combate

**Objetivo:** Resolver los ataques del jugador y los enemigos, el daño y las eliminaciones.

**Entradas:** Órdenes de ataque, estadísticas de armas y enemigos, efectos de la linterna y posiciones de los participantes.

**Procesamiento / reglas:** Verifica si un ataque alcanza a su objetivo, calcula sus efectos y actualiza la salud correspondiente. Registra las eliminaciones para el sistema de rachas.

**Salidas:** Daño, eliminaciones y señales visuales o sonoras de impacto.

**Estados posibles:** Sin combate, combate activo.

**Dependencias:** Jugador, enemigos, linterna y armas.

**Interacciones:** Puede causar daño al jugador o a los generadores. Informa las eliminaciones al sistema de mejoras y potenciadores.

**Datos que necesita:** Salud, daño, alcance, frecuencia de ataque y efectos activos de cada participante.

**Datos que genera:** Daño causado y recibido, eliminaciones y eventos de ataque.

**Riesgos:** Que la respuesta de los ataques sea poco clara o que un efecto debilitante se aplique más veces de las previstas.

**Criterios de aceptación:** Los ataques válidos producen resultados consistentes; la salud se actualiza correctamente; una eliminación se registra una sola vez.

## Sistema: Generadores

**Objetivo:** Administrar la reparación, integridad y funcionamiento de los generadores que el jugador debe defender.

**Entradas:** Interacción del jugador, tiempo dedicado a reparar, daño enemigo y mejoras elegidas.

**Procesamiento / reglas:** Aumenta el progreso de reparación mientras se cumplen las condiciones de interacción. Reduce la integridad cuando el generador recibe daño. Al estar operativo, proporciona los beneficios de luz definidos para ese generador. Mientras está operativo, recarga la batería del jugador cercano. Si queda destruido, pierde sus beneficios y la recarga hasta repararse, sin provocar una derrota. Al completar su reparación es invulnerable durante unos segundos.

**Salidas:** Progreso de reparación, integridad, estado operativo, beneficios activos y avisos de ataque.

**Estados posibles:** Averiado, en reparación, operativo, bajo ataque, destruido.

**Dependencias:** Jugador, combate, enemigos, mejoras y objetivos.

**Interacciones:** Sus fuentes de luz pueden mejorar las propiedades de la linterna. Los enemigos pueden dañarlos y el jugador puede protegerlos mediante el combate.

**Datos que necesita:** Progreso requerido, integridad máxima y actual, radio y velocidad de recarga de batería, duración de la invulnerabilidad tras repararse y beneficios otorgados.

**Datos que genera:** Cambios de progreso e integridad, activación de beneficios y evento de destrucción.

**Riesgos:** Que el jugador no sepa si una reparación está avanzando o cuál generador requiere atención.

**Criterios de aceptación:** La reparación y el daño actualizan el estado visible del generador; sus beneficios se activan solo cuando corresponde; su destrucción interrumpe beneficios y recarga sin provocar una derrota.

## Sistema: Director de enemigos

**Objetivo:** Aumentar y variar la presión sobre el jugador conforme transcurre la partida.

**Entradas:** Tiempo transcurrido, tickets disponibles, catálogo, costo de enemigos, enemigos presentes y estado de la partida.

**Procesamiento / reglas:** Recibe tickets con el paso del tiempo. Selecciona enemigos que puede pagar con su presupuesto y descuenta su costo al introducirlos. Conforme aumenta la cantidad de tickets disponible, puede seleccionar amenazas más peligrosas.

**Salidas:** Órdenes de aparición de enemigos y presupuesto restante.

**Estados posibles:** Inactivo y generando amenazas.

**Dependencias:** Reloj de partida, catálogo de enemigos y sistema de aparicion.

**Interacciones:** Envía amenazas al combate y ejerce presión sobre el jugador y los generadores.

**Datos que necesita:** Tickets iniciales, tasa de obtención, costo de cada enemigo, lugares válidos de aparición y límite de enemigos simultáneos.

**Datos que genera:** Tickets acumulados y gastados, enemigos seleccionados y eventos de aparición.

**Riesgos:** Apariciones imposibles de afrontar, acumulación excesiva de enemigos o situaciones en las que no exista un lugar válido para generarlos.

**Criterios de aceptación:** El director nunca gasta más tickets de los disponibles; cada enemigo generado tiene un costo válido; respeta los límites y las zonas de aparición; deja de generar amenazas al finalizar la partida.

## Sistema: Mejoras y potenciadores

**Objetivo:** Permitir que el jugador adapte su estrategia durante la partida.

**Entradas:** Selección de mejoras, equipo actual, rachas de eliminaciones y condiciones de obtención de potenciadores.

**Procesamiento / reglas:** Aplica las modificaciones elegidas a la linterna, las armas o los generadores. Detecta cuándo una racha cumple la condición para otorgar un potenciador y aplica sus efectos según las reglas definidas.

**Salidas:** Estadísticas actualizadas, efectos activos y opciones mostradas al jugador.

**Estados posibles:** Sin selección pendiente, selección disponible, potenciador activo.

**Dependencias:** Linterna, combate, generadores y registro de eliminaciones.

**Interacciones:** Modifica las capacidades utilizadas por los demás sistemas sin cambiar sus reglas básicas de interacción.

**Datos que necesita:** Catálogo de mejoras, condiciones de desbloqueo, límites de acumulación y duración de cada efecto.

**Datos que genera:** Mejoras seleccionadas, potenciadores activos y estadísticas resultantes.

**Riesgos:** Combinaciones que vuelvan imposible perder o que impidan enfrentar a ciertos enemigos sin una mejora específica.

**Criterios de aceptación:** Cada mejora muestra su efecto antes de seleccionarse; al elegirla se aplica una sola vez conforme a sus reglas; los efectos temporales terminan cuando corresponde.

## Sistema: Objetivos y resultado de partida

**Objetivo:** Controlar la duración de la supervivencia, iniciar el encuentro final y determinar el resultado.

**Entradas:** Tiempo transcurrido, salud y batería del jugador, estado de los generadores y salud del jefe final.

**Procesamiento / reglas:** Mientras no se cumpla el tiempo establecido, la partida continúa. Al cumplirse, aparece el jefe final. La victoria se concede al derrotarlo. La derrota ocurre si la salud del soldado llega a cero o si permanece demasiado tiempo sin batería.

**Salidas:** Aparición del jefe final y resultado de victoria o derrota.

**Estados posibles:** Supervivencia, combate contra el jefe final, victoria, derrota.

**Dependencias:** Reloj de partida, jugador, generadores, combate y director de enemigos.

**Interacciones:** Recibe los eventos de los demás sistemas y comunica cuándo deben detenerse al terminar la partida.

**Datos que necesita:** Tiempo necesario para que aparezca el jefe, tiempo límite sin batería y estado del jefe.

**Datos que genera:** Tiempo restante, estado del objetivo y resultado final.

**Riesgos:** Que dos condiciones de finalización ocurran al mismo tiempo o que el jefe aparezca cuando la partida ya terminó.

**Criterios de aceptación:** El jefe aparece una sola vez al cumplirse el tiempo; sobrevivir hasta ese momento no concede la victoria; derrotar al jefe concede la victoria solo si el jugador no ha perdido; la partida registra un único resultado final.

## Relaciones entre sistemas

El **sistema de objetivos** recibe el tiempo transcurrido y los estados del jugador, los generadores y el jefe para decidir si la partida continúa o termina. El **director** utiliza el tiempo y su presupuesto de tickets para ordenar la aparición de enemigos.

Durante el combate, la **linterna** informa qué enemigos reciben efectos debilitantes. El **sistema de combate** utiliza esos efectos para resolver los enfrentamientos y registra las eliminaciones. Las eliminaciones alimentan el sistema de **rachas y potenciadores**.

Los **generadores** reciben daño del combate y progreso de reparación del jugador. Cuando están operativos, comunican sus beneficios al sistema de linterna. El sistema de **mejoras** modifica las propiedades de la linterna, las armas y los generadores según las elecciones del jugador.

> **Navegación:** [[00 - Índice]] · ← [[02 - Mecánicas]] · [[04 - Controles]] →
