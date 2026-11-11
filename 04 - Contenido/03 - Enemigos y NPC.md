# Enemigos y NPC

## Descripción de la sección

Documenta las entidades controladas por el juego y su comportamiento.

## Reglas generales de los enemigos

- La Cáscara cuesta 1 ticket. La Quimera cuesta 3 y entra en el catálogo en el segundo 180. Tiene peso 0.5 frente al peso 1 de la Cáscara en el sorteo normal. El director le reserva una aparición prioritaria desde el minuto 3 y vuelve a programarla 45 s después de cada aparición prioritaria. Requiere tickets, cupo y una posición válida.
- El director solo puede generar enemigos cuyo costo pueda cubrir.
- El tope de enemigos vivos sube de 3 a 12 durante los primeros 4 minutos. El director hace su primer intento a los 20 s. Busca el centro del grupo alrededor del jugador en un radio de 12 a 22 m y comprueba una ruta por el NavMesh cuando localiza al jugador sobre él. El 35 % es la probabilidad de asignar el grupo al generador operativo más cercano a su punto de aparición, si existe. La Quimera puede buscar un generador por su cuenta.
- Los enemigos deben comunicar sus ataques mediante señales visuales o sonoras.
- La linterna aplica efectos debilitantes según sus propiedades y mejoras.
- Los efectos de la luz deben ser visibles y consistentes.
- La pausa y la selección de mejoras detienen sus movimientos, ataques y tiempos de recarga.
- Todo enemigo regular eliminado suelta cristales; la cantidad depende de su dificultad.
- Cada muerte se registra una sola vez para otorgar recursos y aumentar la racha.
- La selección entre atacar al jugador o a los generadores debe definirse por tipo de enemigo.

## Enemigos regulares

### Cáscara

**Rol de combate:**

Enemigo básico de persecución. Presiona al jugador mediante el acercamiento y obliga a mantener distancia mientras utiliza la linterna y el arma.

**Comportamiento:**

Detecta al jugador, se aproxima e intenta atacarlo al entrar en alcance. Su comportamiento sencillo permite aprender las reglas básicas del combate.

Conserva una silueta claramente humana. Su cuerpo presenta los primeros signos de control de la infección, con crecimientos cristalinos violetas todavía limitados.

![[Cáscara - Frente.png|250]]![[Cáscara - Lateral.png|250]]

**Vida:**

Baja en comparación con las otras variantes: 60 PV.

**Daño:**

Bajo por impacto individual; peligroso si varios enemigos alcanzan al jugador: 10 PV por golpe.

**Defensas:**

Sin blindaje especializado. Se propone que no reduzca el daño recibido, como en el prototipo. Las demás resistencias están por definir.

**Velocidad:**

Velocidad base de referencia para los enemigos. Debe permitir al jugador aprender a crear distancia. Se mueve a 3.2 m/s, entre la caminata y la carrera del soldado.

**Rango de detección:**

Detecta al jugador a 14 m con línea de visión y a 4 m aunque haya obstáculos. Una vez adquirido el objetivo, intenta acercarse siguiendo rutas transitables. Lo pierde a más de 20 m o tras 2.5 s sin verlo, y lo busca en su última posición conocida durante 4 s.

**Ataques:**

Golpe cuerpo a cuerpo con una preparación breve y reconocible. Empieza a prepararlo a 1.5 m, con 0.6 s de preparación, 0.2 s de golpe y 0.9 s de recuperación; el golpe conecta hasta 1.9 m en un arco de 70°, así que alejarse durante la preparación lo esquiva.

**Debilidades:**

- Efectos debilitantes de la linterna.
- Necesidad de acercarse para causar daño.
- Exposición durante la recuperación de su ataque.

**Recompensa:**

1 cristal. Cuenta como una eliminación para la racha.

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

Su prioridad es destruir los generadores. Se desplaza hacia su generador objetivo y, al alcanzarlo, lo ataca mientras el jugador permanezca fuera de su zona de peligro.

Esta zona se define mediante un radio esférico centrado en la Quimera y se desplaza junto con ella. Cuando el jugador entra en ese radio, la criatura interrumpe su acción contra el generador y concentra sus ataques en él.

En cuanto el jugador sale de la zona de peligro, la Quimera deja de perseguirlo y vuelve a enfocarse en el generador, retomando su desplazamiento o sus ataques según la distancia a la que se encuentre.

Su comportamiento obliga al jugador a decidir entre acercarse para distraerla y exponerse a sus ataques, o mantener la distancia y permitir que continúe dañando el generador.

Cuando recibe luz y su habilidad está disponible, realiza un desplazamiento rápido hacia la izquierda o la derecha para intentar salir del cono de iluminación.

Su cuerpo está formado por cuatro torsos que funcionan como extremidades, conectados a un núcleo cristalino central. Un ojo de cristal frontal refuerza la dirección de su mirada.

![[Quimera - Frente.png|250]]![[Quimera - Lateral.png|250]]

**Vida:**

Elevada respecto a la Cáscara: 300 PV.

**Daño:**

Alto por golpe, compensado con una preparación visible y una recuperación prolongada: 30 PV por golpe, también contra los generadores.

**Defensas:**

Blindaje elevado: reduce el 30 % del daño recibido. El daño extra de la linterna se multiplica por esa reducción: un disparo de 20 PV le quita 14 PV, o 17.5 PV si está iluminada. La interacción con las mejoras de la linterna está por definir.

**Velocidad:**

Baja durante la persecución y alta durante el desplazamiento evasivo: camina a 1 m/s y la evasión recorre 3 m en 0.35 s.

**Rango de detección:**

Su zona de peligro mide 6 m de radio; el jugador tiene que alejarse a más de 6.5 m para que vuelva al generador. Busca siempre el generador operativo más cercano y, si no queda ninguno, persigue al jugador como una Cáscara. La reacción a la luz requiere que el enemigo esté efectivamente dentro del área iluminada.

**Ataques:**

Golpe pesado a corta distancia con una de sus extremidades. Empieza a prepararlo a 2.4 m, con 0.8 s de preparación, 0.2 s de golpe y 1 s de recuperación; el golpe conecta hasta 3.1 m en un arco de 90°.

El desplazamiento evasivo tiene una función defensiva; no causa daño por sí mismo salvo que posteriormente se defina esa propiedad.

**Debilidades:**

- Movimiento ordinario lento.
- Intervalo sin evasión mientras la habilidad se recarga.
- Preparación y recuperación visibles de su ataque.
- Efectos debilitantes de la luz mientras permanece iluminado.

El cristal central no se considera automáticamente un punto débil; esa propiedad está pendiente de definición.

**Recompensa:**

4 cristales, más que la Cáscara por el esfuerzo necesario para eliminarla. Cuenta como una eliminación para la racha.

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

- La recarga dura 6 s y comienza al ejecutar la habilidad.
    
- Si un lado está bloqueado, evalúa el otro.
    
- Si ambos lados están bloqueados, permanece en su comportamiento normal.
    
- No atraviesa paredes, generadores ni obstáculos sólidos.
    
- La evasión no concede invulnerabilidad por defecto.
    
- No interrumpe un ataque para evadir: solo evade mientras persigue o se desplaza.
    
- La recarga transcurre en paralelo a los demás estados y se detiene durante la pausa.

## Jefe final

### Ascendido

**Rol de combate:**

Jefe final del nivel. Representa la mayor amenaza individual y exige combinar movimiento, linterna, armas y mejoras.

**Comportamiento:**

Aparece al alcanzar el tiempo establecido de supervivencia. Conserva una estructura humanoide musculosa, cuatro brazos suspendidos cerca de los hombros y un halo de cristal en la espalda.

Su rostro presenta ojos violetas y facciones cubiertas. A diferencia de otras variantes, tiene pocos cristales sobresalientes.

Alterna ataques de sus brazos y periodos de recuperación, con señales claras antes de cada acción.

**Vida:**

Superior a la de los enemigos regulares: 1500 PV.

**Daño:**

Elevado, con valores independientes para cada ataque. Ningún ataque debe carecer de una oportunidad comprensible de respuesta: 25 PV el golpe dirigido, 20 el barrido y 35 el impacto convergente.

**Defensas:**

No reduce el daño recibido y la linterna lo debilita como a los demás enemigos.

**Velocidad:**

El cuerpo se desplaza a 1.6 m/s; los brazos tienen la velocidad de cada ataque.

**Rango de detección:**

Siempre sabe dónde está el jugador y se acerca hasta 6 m de él.

**Ataques propuestos:**

|Ataque|Descripción|Señal previa|Respuesta del jugador|
|---|---|---|---|
|Golpe dirigido|Un brazo se proyecta hacia la posición señalada del jugador|El brazo retrocede y se orienta antes de salir|Desplazarse fuera de la trayectoria|
|Barrido|Un brazo recorre un arco a corta distancia|El brazo se extiende hacia un costado|Alejarse del área de alcance|
|Impacto convergente|Los brazos golpean una zona anunciada|Los brazos se separan y el área objetivo se señala|Abandonar la zona antes del impacto|

El golpe dirigido se elige entre 3 y 12 m, con 0.9 s de señal y 1.2 s de recuperación, y alcanza a 1.1 m de su trayectoria; el barrido, hasta 5.5 m, con 0.8 s de señal y 1 s de recuperación, y recorre 200° delante del cuerpo; el impacto convergente, hasta 14 m, con 1.3 s de señal y 1.6 s de recuperación, golpea una zona de 2.6 m de radio y no se repite antes de 10 s. La señal es una marca roja en el suelo: la trayectoria, el arco o la zona. Elige al azar, según su peso, entre los ataques cuya distancia y recarga lo permitan.

**Debilidades:**

- Periodos de recuperación después de sus ataques.
    
- La linterna lo debilita: recibe +25 % de daño mientras está iluminado.
    
- Trayectorias y áreas de ataque anticipadas que permiten reposicionarse.
    

Los brazos son entidades separadas vinculadas al jefe y no reciben daño. El halo tampoco se considera un punto débil sin una regla explícita.

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
| Morir              | El cuerpo y los brazos son absorbidos por el halo       | Da paso al fundido y a la pantalla de Victoria        |

**Reglas particulares:**

- Aparece una sola vez por partida.
- Su aparición depende del tiempo y no de reparar un número de generadores.
- El cuerpo coordina los brazos para evitar ataques simultáneos no previstos.
- Al morir, se cancelan sus acciones y las de sus brazos.
- La animación de absorción se reproduce una sola vez.
- Durante este combate el director permanece en pausa. Las invocaciones del Ascendido siguen como propuesta de diseño.

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

**Función:** Representar al sector científico de CERBERUS y ofrecer una investigación opcional relacionada con los riesgos de los cristales.

**Ubicación:** Fuera del centro científico, en una instalación de la facción científica de CERBERUS en Hades. No aparece en el mapa: el contacto es remoto, por un canal cifrado del comunicador del soldado, distinto del de Enlace. La frecuencia está en el registro de Lucía Ferrán y sus mensajes se leen en el panel de comunicaciones del HUD, con su retrato. La terminal de comunicaciones del Archivo solo sirve para preparar la copia de las pruebas.

**Interacción:** Conversaciones condicionadas y peticiones opcionales.

**Diálogos:** Analíticos, cautelosos y progresivamente más comprometidos con las revelaciones.

> «No te pido que me creas; te pido que leas los informes».

**Condiciones:**

- El jugador debe cumplir requisitos específicos para establecer contacto.
- Las conversaciones dependen del progreso de sus peticiones.
- Los requisitos deben poder completarse dentro del tiempo de la partida.
- Sus conversaciones no contienen instrucciones indispensables para aprender los controles básicos.

**Recompensas / información:**

Aporta información sobre la Violeta Mortífera y las decisiones de CERBERUS. Completar sus peticiones habilita el final **Ni uno más** si el jugador derrota al Ascendido.

No se han definido recompensas adicionales de armas o mejoras.

## Entidades narrativas sin IA activa

Los operativos fallecidos se documentan en la sección **Personajes**. Sus cuerpos y equipos permiten recuperar registros, pero no patrullan, combaten ni responden al jugador.

Los dirigentes de CERBERUS, el consejo y los operativos que combaten fuera del área del protagonista pertenecen al trasfondo. No requieren IA dentro del nivel mientras no se defina una participación directa.

## Decisiones pendientes

- Tipos de enemigos que atacan generadores y reglas para cambiar de objetivo.
- Detección, pérdida de objetivo y búsqueda.
- Efectos concretos de la linterna sobre cada variante.
- Entidades invocadas por el Ascendido.


> **Navegación:** [[00 - Índice]] · ← [[02 - Niveles]] · [[04 - Objetos y Coleccionables]] →
