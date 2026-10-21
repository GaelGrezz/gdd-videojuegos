# Niveles

## Descripción de la sección

Cada nivel debe documentar su propósito jugable, estructura, dificultad, contenido y condiciones de entrada/salida.
## Nivel único: Centro científico de Hades

**Objetivo principal:**

Sobrevivir durante el tiempo establecido y derrotar al Ascendido cuando aparezca. Mantener los generadores operativos y mejorar el equipo facilita la supervivencia, pero no sustituye estas condiciones de victoria.

**Objetivos secundarios:**

- Reparar y defender los generadores para conservar sus beneficios.
- Recuperar registros de los operativos fallecidos.
- Cumplir las condiciones para establecer contacto con Issac.
- Completar las peticiones de Issac para acceder al final **Ni uno más**.
- Obtener cristales para fortalecer al personaje.

**Duración estimada:**

Por definir mediante pruebas de juego. La duración comprende el periodo de supervivencia y el combate contra el Ascendido.

El reloj de partida se detiene durante la pausa y la selección de mejoras. Por ello, el tiempo real de una sesión puede ser mayor que el tiempo registrado por el juego.

**Dificultad:**

Creciente conforme transcurre el tiempo. El director recibe tickets que utiliza para generar enemigos según sus costos y las reglas de aparición.

La dificultad combina cantidad de amenazas, variedad de comportamientos y presión sobre el jugador y los generadores. Los valores, intervalos y límites de enemigos simultáneos están por definir.

**Mecánicas introducidas:**

- Movimiento y orientación.
- Uso de la linterna para debilitar infectados.
- Ataque con armas.
- Reparación y defensa de generadores.
- Recolección de cristales.
- Selección de mejoras al subir de nivel.
- Recuperación de salud mediante botiquines.
- Consulta de registros e interacción narrativa.

Nicolás presenta las acciones esenciales mediante comunicaciones asociadas a las primeras situaciones en que se necesitan.

**Mecánicas utilizadas:**

- Gestión de salud y batería.
- Posicionamiento para evitar ataques y cercos.
- Priorización de enemigos y generadores amenazados.
- Obtención de rachas de eliminaciones sin recibir daño.
- Elección de mejoras que complementen la estrategia.
- Exploración opcional mientras avanza la partida.
- Cumplimiento de las peticiones de Issac.

La batería se recarga al permanecer cerca de un generador operativo. El prototipo no incluye tienda.

**Enemigos / obstáculos:**

| Elemento                      | Función dentro del nivel                                                                                          |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Cáscara                       | Presenta la amenaza básica y presiona al jugador mediante el acercamiento                                         |
| Quimera                       | Combina resistencia elevada con un desplazamiento evasivo al recibir luz; su habilidad tiene un tiempo de recarga |
| Ascendido                     | Jefe final que exige aprovechar las herramientas y mejoras obtenidas                                              |
| Oscuridad                     | Limita la información visual y refuerza la importancia de orientar la linterna                                    |
| Infraestructura dañada        | Obliga a decidir cuándo reparar y cuándo priorizar la defensa                                                     |
| Pasillos y obstáculos físicos | Condicionan el movimiento, las rutas de escape y el posicionamiento                                               |

Los ataques concretos del Ascendido y las variantes adicionales de enemigos se documentarán en sus fichas correspondientes.

**Recompensas:**

- Cristales para subir de nivel y escoger mejoras.
- Potenciadores al alcanzar umbrales de racha.
- Recuperación de los beneficios de los generadores al repararlos.
- Registros que amplían el conocimiento sobre el complejo y Cerberus.
- Acceso al final alternativo al completar las peticiones de Issac y vencer al jefe.

No hay recompensas persistentes entre partidas .

**Puntos de guardado:**

Inexistentes

**Condición de entrada:**

El jugador selecciona **Iniciar** en el menú principal. El soldado termina de abrir las puertas, entra al complejo y la cámara adopta la perspectiva de juego.

Una vez que el escenario está preparado y se entrega el control, comienza el reloj de partida y Nicolás establece comunicación.

**Condición de salida:**

| Resultado                        | Condición                                                                                                   |
| -------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| Victoria: Información recuperada | Sobrevivir hasta la aparición del Ascendido y derrotarlo sin haber completado todas las peticiones de Issac |
| Victoria: Ni uno más             | Sobrevivir hasta la aparición del Ascendido, derrotarlo y haber completado las peticiones de Issac          |
| Derrota por salud                | La salud del soldado llega a cero                                                                           |
| Derrota por batería              | La batería permanece al 0 % hasta agotar el periodo de tolerancia                                           |
| Abandono                         | El jugador confirma que desea regresar al menú                                                              |

**Eventos narrativos:**

1. El soldado abre las puertas e ingresa al complejo.
2. Nicolás establece contacto y transmite las primeras instrucciones.
3. El jugador encuentra rastros de las intervenciones anteriores.
4. La exploración permite recuperar registros y, si se cumplen las condiciones, contactar con Issac.
5. Las peticiones de Issac ofrecen una investigación opcional durante la supervivencia.
6. Al alcanzar el tiempo establecido, aparece el Ascendido.
7. Tras su derrota, el cuerpo del Ascendido es absorbido por su halo de cristal.
8. Se reproduce la cinemática de victoria correspondiente. Si el jugador muere antes, se presenta la secuencia de derrota apropiada.

**Mapa / diagrama:**

La distribución definitiva está por diseñar. El mapa debe integrar las siguientes áreas funcionales dentro de un único escenario:

|Área|Propósito jugable|Criterio de diseño|
|---|---|---|
|Acceso principal|Presentar la entrada y los controles básicos|Espacio inicial legible para aprender a moverse|
|Áreas de combate y circulación|Sostener los enfrentamientos y conectar sectores|Ofrecer rutas alternativas y evitar bloqueos inevitables|
|Puntos de generadores|Concentrar decisiones de reparación y defensa|Permitir reconocer amenazas y valorar el riesgo de intervenir|
|Laboratorios y sectores secundarios|Alojar exploración y registros|Recompensar los desvíos sin imponer un recorrido obligatorio|
|Punto o medio de contacto con Issac|Dar acceso a su contenido opcional|Ubicación y requisitos pendientes de definición|
|Espacio de enfrentamiento final|Permitir combatir al Ascendido|Contar con espacio suficiente para interpretar y evitar sus ataques|

El área del jefe pertenece al mismo nivel. Su ubicación y la forma de iniciar el encuentro deben impedir que el jugador pierda tiempo buscando al Ascendido sin indicaciones.

## Flujo del nivel

|Momento|Actividad del jugador|Avance|
|---|---|---|
|Entrada|Cruza las puertas y recibe la comunicación de Nicolás|Se entrega el control y comienza el reloj|
|Introducción|Aprende a moverse, iluminar, atacar y reparar|Las instrucciones se activan según sus acciones|
|Supervivencia|Combate, gestiona recursos y mantiene generadores|El tiempo aumenta la presión del director|
|Desarrollo del personaje|Recoge cristales y elige mejoras|Ocurre durante la supervivencia, según los recursos obtenidos|
|Exploración opcional|Recupera registros y atiende las peticiones de Issac|Ocurre en paralelo a la misión principal|
|Enfrentamiento final|Combate al Ascendido|Se activa al alcanzar el tiempo establecido|
|Resolución|Obtiene una victoria o sufre una derrota|Se registra el resultado y se presenta el desenlace|

La reparación, las mejoras y la exploración se repiten según las necesidades de la partida. No constituyen etapas obligatorias de una secuencia lineal.

## Criterios de calidad

- El jugador comprende que debe sobrevivir hasta la aparición del Ascendido y derrotarlo.
- El reloj y las comunicaciones permiten reconocer el avance de la partida.
- Las mecánicas esenciales se presentan antes de exigir su uso combinado.
- La dificultad aumenta de forma perceptible y permite responder a las nuevas amenazas.
- Los generadores comunican claramente su integridad, funcionamiento y reparación.
- Los caminos y obstáculos permiten tomar decisiones de posicionamiento.
- La oscuridad mantiene la tensión sin ocultar las señales necesarias para responder a un ataque.
- Las peticiones de Issac pueden completarse dentro del tiempo disponible.
- El contenido opcional no bloquea la victoria normal.
- Los enemigos y jefes disponen de señales claras para su aparición y sus ataques.
- Las pausas y la selección de mejoras detienen correctamente el reloj y la simulación.
- El jugador puede identificar la causa de su derrota o los requisitos que cumplió para obtener su final.
> **Navegación:** [[00 - Índice]] · ← [[01 - Estructura del Contenido]] · [[03 - Enemigos y NPC]] →
