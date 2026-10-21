# Enemigos y NPC

## Descripción de la sección

Documenta las entidades controladas por el juego y su comportamiento.

## Reglas generales de los enemigos

- Cada enemigo regular tiene un costo de aparición en tickets, pendiente de balance.
- El director solo puede generar enemigos cuyo costo pueda cubrir.
- La cantidad máxima de enemigos simultáneos y las reglas de aparición están por definir.
- Los enemigos deben comunicar sus ataques mediante señales visuales o sonoras.
- La linterna aplica efectos debilitantes según sus propiedades y mejoras.
- Los efectos de la luz deben ser visibles y consistentes.
- La pausa y la selección de mejoras detienen sus movimientos, ataques y tiempos de recarga.
- Los enemigos eliminados pueden soltar cristales; cantidades y reglas de aparición pendientes de definición.
- Cada muerte se registra una sola vez para otorgar recursos y aumentar la racha.
- La selección entre atacar al jugador o a los generadores debe definirse por tipo de enemigo.

## Enemigos regulares

### Cáscara

**Rol de combate:**

Enemigo básico de persecución. Presiona al jugador mediante el acercamiento y obliga a mantener distancia mientras utiliza la linterna y el arma.

**Comportamiento:**

Detecta al jugador, se aproxima e intenta atacarlo al entrar en alcance. Su comportamiento sencillo permite aprender las reglas básicas del combate.

Conserva una silueta claramente humana. Su cuerpo presenta los primeros signos de control de la infección, con crecimientos cristalinos violetas todavía limitados.

**Vida:**

Baja en comparación con las otras variantes. Valor por definir.

**Daño:**

Bajo por impacto individual; peligroso si varios enemigos alcanzan al jugador. Valor por definir.

**Defensas:**

Sin blindaje especializado. Las resistencias concretas están por definir.

**Velocidad:**

Velocidad base de referencia para los enemigos. Debe permitir al jugador aprender a crear distancia; valor por definir.

**Rango de detección:**

Por definir. Una vez adquirido el objetivo, intenta acercarse siguiendo rutas transitables.

**Ataques:**

Golpe cuerpo a cuerpo con una preparación breve y reconocible. Alcance, frecuencia y duración por definir.

**Debilidades:**

- Efectos debilitantes de la linterna.
- Necesidad de acercarse para causar daño.
- Exposición durante la recuperación de su ataque.

**Recompensa:**

Cristales según la tabla de recompensas que se establezca. Cuenta como una eliminación para la racha.

**Estados de IA:**

|Estado|Acción|Transición|
|---|---|---|
|Adquirir objetivo|Identifica al jugador|Pasa a Perseguir cuando obtiene un objetivo válido|
|Perseguir|Se acerca al objetivo|Pasa a Preparar ataque al entrar en alcance|
|Preparar ataque|Anticipa el golpe|Pasa a Atacar al terminar la preparación|
|Atacar|Ejecuta el golpe|Pasa a Recuperarse|
|Recuperarse|Completa la animación posterior al ataque|Vuelve a perseguir o prepara otro ataque según la distancia|
|Buscar|Se dirige a la última posición conocida|Retoma la persecución al detectar al jugador|
|Morir|Reproduce su muerte y entrega las recompensas correspondientes|Estado terminal|

La búsqueda solo será necesaria si el sistema de detección permite perder al objetivo.

### Quimera

**Rol de combate:**

Enemigo pesado y resistente que obliga al jugador a ajustar el apuntado y anticipar su evasión.

**Comportamiento:**

Avanza lentamente hacia su objetivo. Cuando recibe luz y su habilidad está disponible, realiza un desplazamiento rápido hacia la izquierda o la derecha para intentar salir del cono de iluminación.

Su cuerpo está formado por cuatro torsos que funcionan como extremidades, conectados a un núcleo cristalino central. Un ojo de cristal frontal refuerza la dirección de su mirada.

**Vida:**

Elevada respecto a la Cáscara. Valor por definir.

**Daño:**

Se propone daño alto por golpe, compensado con una preparación visible y una recuperación prolongada.

**Defensas:**

Blindaje elevado. Su reducción de daño y la interacción con las mejoras de la linterna están por definir.

**Velocidad:**

Baja durante la persecución y alta durante el desplazamiento evasivo. Distancia y duración de la evasión por definir.

**Rango de detección:**

Por definir. La reacción a la luz requiere que el enemigo esté efectivamente dentro del área iluminada.

**Ataques:**

Se propone un golpe pesado a corta distancia con una de sus extremidades.

El desplazamiento evasivo tiene una función defensiva; no causa daño por sí mismo salvo que posteriormente se defina esa propiedad.

**Debilidades:**

- Movimiento ordinario lento.
- Intervalo sin evasión mientras la habilidad se recarga.
- Preparación y recuperación visibles de su ataque.
- Efectos debilitantes de la luz mientras permanece iluminado.

El cristal central no se considera automáticamente un punto débil; esa propiedad está pendiente de definición.

**Recompensa:**

Cristales. Se propone una recompensa superior a la Cáscara por el esfuerzo necesario para eliminarlo. Cuenta como una eliminación para la racha.

**Estados de IA:**

|Estado|Acción|Transición|
|---|---|---|
|Adquirir objetivo|Identifica un objetivo válido|Pasa a Perseguir|
|Perseguir|Avanza lentamente|Prepara un ataque al entrar en alcance o evalúa una evasión al recibir luz|
|Evaluar evasión|Comprueba recarga y espacio lateral disponible|Pasa a Evadir si existe una dirección válida|
|Evadir|Realiza el desplazamiento lateral|Activa la recarga y vuelve a Perseguir|
|Preparar ataque|Anticipa el golpe pesado|Pasa a Atacar|
|Atacar|Ejecuta el golpe|Pasa a Recuperarse|
|Recuperarse|Completa la recuperación|Vuelve a Perseguir|
|Morir|Finaliza su comportamiento y entrega recompensas|Estado terminal|

**Reglas de evasión:**

- La recarga comienza al ejecutar la habilidad.
    
- Si un lado está bloqueado, evalúa el otro.
    
- Si ambos lados están bloqueados, permanece en su comportamiento normal.
    
- No atraviesa paredes, generadores ni obstáculos sólidos.
    
- La evasión no concede invulnerabilidad por defecto.
    
- La posibilidad de interrumpir un ataque para evadir está por definir.
    
- La recarga transcurre en paralelo a los demás estados y se detiene durante la pausa.

## Jefe final

### Ascendido

**Rol de combate:**

Jefe final del nivel. Representa la mayor amenaza individual y exige combinar movimiento, linterna, armas y mejoras.

**Comportamiento:**

Aparece al alcanzar el tiempo establecido de supervivencia. Conserva una estructura humanoide musculosa, cuatro brazos suspendidos cerca de los hombros y un halo de cristal en la espalda.

Su rostro presenta ojos violetas y facciones cubiertas. A diferencia de otras variantes, tiene pocos cristales sobresalientes.

Se propone que alterne ataques de sus brazos y periodos de recuperación, ofreciendo señales claras antes de cada acción.

**Vida:**

Superior a la de los enemigos regulares. Valor por definir según la duración deseada del enfrentamiento.

**Daño:**

Elevado, con valores independientes para cada ataque. Ningún ataque debe carecer de una oportunidad comprensible de respuesta.

**Defensas:**

Resistencias por definir. No se presupone inmunidad a la linterna.

**Velocidad:**

Por definir. El cuerpo y los brazos pueden tener velocidades diferentes según el ataque.

**Rango de detección:**

Debe poder adquirir al jugador al iniciar el enfrentamiento. Las restricciones por distancia y obstáculos están por definir.

**Ataques propuestos:**

|Ataque|Descripción|Señal previa|Respuesta del jugador|
|---|---|---|---|
|Golpe dirigido|Un brazo se proyecta hacia la posición señalada del jugador|El brazo retrocede y se orienta antes de salir|Desplazarse fuera de la trayectoria|
|Barrido|Un brazo recorre un arco a corta distancia|El brazo se extiende hacia un costado|Alejarse del área de alcance|
|Impacto convergente|Los brazos golpean una zona anunciada|Los brazos se separan y el área objetivo se señala|Abandonar la zona antes del impacto|

El repertorio definitivo, sus tiempos y el orden de selección se establecerán durante las pruebas del jefe.

**Debilidades:**

- Periodos de recuperación después de sus ataques.
    
- Efectos de la linterna según las reglas específicas que se definan.
    
- Trayectorias y áreas de ataque anticipadas que permiten reposicionarse.
    

Los brazos son entidades separadas vinculadas al jefe. Está por definir si pueden recibir daño, destruirse o deshabilitarse. El halo tampoco se considera un punto débil sin una regla explícita.

**Recompensa:**

Su derrota completa el objetivo principal y activa el final correspondiente:

- **Información recuperada:** si las peticiones de Issac están incompletas.
    
- **Ni uno más:** si se cumplieron todas las peticiones requeridas.
    

No se establece una recompensa de recursos posterior al combate, ya que la partida concluye.

**Estados de IA:**

| Estado             | Acción                                                  | Transición                                 |
| ------------------ | ------------------------------------------------------- | ------------------------------------------ |
| Aparición          | Presenta al jefe y prepara el encuentro                 | Pasa a Adquirir objetivo                   |
| Adquirir objetivo  | Localiza al jugador                                     | Pasa a Posicionarse                        |
| Posicionarse       | Ajusta la ubicación del cuerpo y los brazos             | Pasa a Seleccionar ataque                  |
| Seleccionar ataque | Escoge una acción disponible según distancia y recargas | Pasa a Preparar ataque                     |
| Preparar ataque    | Muestra la señal correspondiente                        | Pasa a Ejecutar ataque                     |
| Ejecutar ataque    | Coordina el cuerpo y los brazos participantes           | Pasa a Recuperarse                         |
| Recuperarse        | Mantiene una ventana de respuesta para el jugador       | Vuelve a Posicionarse o Seleccionar ataque |
| Morir              | El cuerpo y los brazos son absorbidos por el halo       | Da paso a la cinemática de victoria        |
|                    |                                                         |                                            |

**Reglas particulares:**

- Aparece una sola vez por partida.
- Su aparición depende del tiempo y no de reparar un número de generadores.
- El cuerpo coordina los brazos para evitar ataques simultáneos no previstos.
- Al morir, se cancelan sus acciones y las de sus brazos.
- La animación de absorción se reproduce una sola vez.
- Durante este combate el director permanece en pausa. Las entidades que invoque el propio Ascendido están por definir.

## NPC

### Nicolás Varela — «Enlace»

**Nombre:** Nicolás Varela.

**Función:** Guiar al jugador, explicar las mecánicas y transmitir órdenes de los altos mandos.

**Ubicación:** Fuera del escenario jugable; participa mediante comunicaciones.

**Interacción:** Mensajes activados por eventos, objetivos y situaciones relevantes. No requiere un personaje físico en el mapa.

**Diálogos:** Breves, profesionales y orientados a la acción.

> «Eco-10, aquí Enlace. Has cruzado el acceso. Revisa el sector».

> «Asegura el área antes de reparar».

**Condiciones:**

- Establece contacto al terminar la entrada al complejo.
- Presenta cada instrucción cuando la mecánica correspondiente está disponible.
- Evita repetir mensajes de forma continua.
- Sus comunicaciones no se superponen con otras voces.

**Recompensas / información:**

Proporciona instrucciones, objetivos y avisos. No entrega recursos directamente.

### Doctor Issac Ferrer

**Nombre:** Issac Ferrer.

**Función:** Representar al sector científico de Cerberus y ofrecer una investigación opcional relacionada con los riesgos de los cristales.

**Ubicación:** Por definir. También está pendiente si el contacto es presencial, remoto o combina ambos medios.

**Interacción:** Conversaciones condicionadas y peticiones opcionales.

**Diálogos:** Analíticos, cautelosos y progresivamente más comprometidos con las revelaciones.

> «No te pido que me creas; te pido que leas los informes».

**Condiciones:**

- El jugador debe cumplir requisitos específicos para establecer contacto.
- Las conversaciones dependen del progreso de sus peticiones.
- Los requisitos deben poder completarse dentro del tiempo de la partida.
- Sus conversaciones no contienen instrucciones indispensables para aprender los controles básicos.

**Recompensas / información:**

Aporta información sobre Vimer y las decisiones de Cerberus. Completar sus peticiones habilita el final **Ni uno más** si el jugador derrota al Ascendido.

No se han definido recompensas adicionales de armas o mejoras.

## Entidades narrativas sin IA activa

Los operativos fallecidos se documentan en la sección **Personajes**. Sus cuerpos y equipos permiten recuperar registros, pero no patrullan, combaten ni responden al jugador.

Los dirigentes de Cerberus, el consejo y los operativos que combaten fuera del área del protagonista pertenecen al trasfondo. No requieren IA dentro del nivel mientras no se defina una participación directa.

## Decisiones pendientes

- Valores de vida, daño, velocidad, alcance y recarga.
- Costos en tickets y recompensas por enemigo.
- Tipos de enemigos que atacan generadores y reglas para cambiar de objetivo.
- Detección, pérdida de objetivo y búsqueda.
- Efectos concretos de la linterna sobre cada variante.
- Ataques definitivos del Ascendido e interacción con sus brazos.
- Entidades invocadas por el Ascendido.
- Ubicación, condiciones de contacto y peticiones de Issac.

> **Navegación:** [[00 - Índice]] · ← [[02 - Niveles]] · [[04 - Objetos y Coleccionables]] →
