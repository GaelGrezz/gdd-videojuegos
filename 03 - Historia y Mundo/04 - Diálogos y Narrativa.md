# Diálogos y Narrativa

## Descripción de la sección

Define cómo se presenta la historia al jugador y cómo funcionan los diálogos.

## Métodos narrativos

- Diálogo
- Secuencias narrativas
- Texto ambiental
- Objetos
- Exploración
- Audio
- Narración
## Secuencias narrativas

### Inicio del despliegue

El jugador selecciona **Iniciar despliegue**. Al terminar la carga, empieza la partida en el centro científico de Hades y el jugador recibe el control de Eco-10. El mensaje implementado de Enlace aparece durante la carga: «Eco-10, ilumina al objetivo antes de abrir fuego».

El primer mensaje de Nicolás aparece en el panel de comunicaciones al terminar la carga, mientras el jugador controla a Eco-10.

> **Nicolás:** «Eco-10, aquí Enlace. Confirma recepción… Te recibo. Has cruzado el acceso. Mantén la luz sobre lo que se mueva y revisa el sector. Necesitamos recuperar la energía».

Para el tutorial propuesto, las instrucciones posteriores aparecerían cuando correspondiera realizar cada acción.

### Jefe final: Muerte del Ascendido

El **Ascendido** es el jefe final. Al recibir el daño que lo derrota, pierde la estabilidad y su halo de cristal comienza a atraer su cuerpo.

Sus brazos suspendidos son arrastrados hacia el halo. Después, el torso y las extremidades se contraen y son absorbidos hasta desaparecer en su interior. El sonido de la absorción aumenta y se interrumpe bruscamente cuando el cuerpo desaparece.

El resplandor del halo disminuye y la imagen funde a negro, dando paso al desenlace correspondiente.

### Victoria: Información recuperada

Tras derrotar al Ascendido, la pantalla de Victoria muestra el encabezado «Operación Umbral completada», el título **Información recuperada** y el mensaje de Enlace.

> **Nicolás:** «Eco-10, objetivo neutralizado. Información asegurada. Procede al punto de extracción».

### Victoria: Ni uno más

Si el jugador derrotó al Ascendido y completó las peticiones de Issac, la pantalla de Victoria muestra el título **Ni uno más** y el mensaje de Issac.

> **Issac:** «La copia está fuera de su alcance. Ya no podrán decir que no lo sabían».

Ambos resultados muestran el tiempo, el nivel, los registros recuperados y los generadores operativos, con la opción Volver al menú.

### Derrota: Game Over

La partida se detiene y abre directamente Game Over. Si la salud llega a cero, muestra **Operativo caído** y la explicación «La salud del soldado llegó a cero». Si se agota el periodo de tolerancia de la batería, muestra **Sin luz** y la explicación «La batería agotó el periodo de tolerancia». El jugador puede consultar el resumen, reintentar o volver al menú principal.

## Estructura de diálogo

### Escena / Conversación

**Participantes:**

**Objetivo de la conversación:**

**Contexto:**

**Opciones del jugador:**

**Consecuencias:**

### Conversación: Primer contacto

**Participantes:** Nicolás y el protagonista.

**Objetivo de la conversación:** Establecer el enlace y presentar la primera tarea.

**Contexto:** El soldado acaba de entrar al complejo.

**Opciones del jugador:** Puede leer el mensaje mientras se desplaza. El mensaje no requiere una respuesta ni detiene la partida.

**Consecuencias:** El mensaje presenta la primera tarea de recuperar la energía en Hades.

### Conversación: Instrucciones de campo

**Participantes:** Nicolás y el protagonista.

**Objetivo de la conversación:** Explicar el uso de la linterna, la reparación y la defensa de generadores.

**Contexto:** Se activa al encontrar por primera vez la situación correspondiente.

**Opciones del jugador:** Ejecutar la acción cuando las condiciones lo permitan.

**Consecuencias:** La instrucción se considera completada cuando el jugador realiza la acción.

**Ejemplos de tono:**

> «Dirige la luz hacia el infectado. Aprovecha mientras esté debilitado».

> «Ese generador puede recuperarse. Asegura el área antes de empezar».

> «Están atacando la instalación. Revisa su estado».

### Conversación: Contacto con Issac

**Participantes:** Issac y el protagonista.

**Objetivo de la conversación:** Introducir una perspectiva distinta de la versión oficial y presentar sus peticiones.

**Contexto:** El jugador recupera el registro de Lucía Ferrán, que guarda la frecuencia del canal cifrado de Issac. Sus mensajes llegan al comunicador del soldado y se leen en el panel de comunicaciones.

**Opciones del jugador:** Participar en el contenido opcional de Issac y atender sus peticiones.

**Consecuencias:** Se habilita una línea de investigación que puede conducir al final **Ni uno más**.

**Propuesta de diálogo:**

> **Issac:** «Antes de que sigas, necesito saber qué te dijeron sobre este lugar».

> **Issac:** «Busca los informes originales. No te pido que me creas; te pido que los leas».

> **Issac:** «Necesito tres archivos: los informes que llevaba el cabo Ocampo, la cronología del mayor Valcárcel y las órdenes de la comandante Alcázar».

> **Issac:** «Con esto basta: siguieron enviando gente después de conocer los riesgos».

> **Issac:** «Guardarlo aquí no sirve de nada. Hay una terminal de comunicaciones en el Archivo; prepara desde ahí una copia».

> **Issac:** «La copia está preparada. En cuanto salgas, la sacaré de aquí».

### Secuencia: Registro de un operativo fallecido

**Participantes:** Autor del registro; el jugador actúa como receptor.

**Objetivo de la conversación:** Reconstruir un acontecimiento y aportar una perspectiva personal.

**Contexto:** El jugador recupera un archivo de un cuerpo o equipo.

**Opciones del jugador:** Consultar el registro o dejar su revisión para después.

**Consecuencias:** Se incorpora información al archivo del jugador. Algunos registros podrán contribuir a las peticiones de Issac.

Los registros no permiten responder a su autor. Su contenido debe respetar lo que el personaje sabía antes de morir.

**Textos de los registros:**

> **Tomás Rivas, soldado de infantería (Vestíbulo):** «Hola, campeón. Papá está bien, de verdad. Aquí dentro hace frío y casi no hay luz, pero pronto vuelvo y te cuento todo... Espera. Algo se mueve detrás de esa puerta».

> **Lidia Castañeda, soldado de infantería (Enfermería):** «Mi escuadra siguió hacia el Vestíbulo. Yo me quedé con un compañero que ya no puede caminar. Si alguien oye esto, estamos en la Enfermería. No lo voy a dejar solo».

> **Joel Navarro, soldado de infantería (Anillo):** «Parte de guardia, sexto turno. Tres ataques anoche y cinco esta mañana, cada vez más seguidos. El relevo iba a llegar el segundo día. Ya van cuatro».

> **Abril Fuentes, soldado de seguridad (Cuarentena):** «Los ruidos pararon a las cuatro. A las cinco declararon el sector seguro. Nadie entró a revisar. Yo tampoco quiero ser la primera».

> **Samuel Paredes, soldado de apoyo logístico (Almacén):** «Otra entrega incompleta: la mitad de las baterías y ninguna caja de munición. Me ordenan repartir el mismo equipo entre tres unidades que operan en sectores distintos. Que alguien me explique cómo».

> **Nora Beltrán, soldado de infantería (Galería):** «Para quien siga a mi unidad: vamos por la Galería hacia el Muelle, la ruta norte está despejada. Dejamos marcas rojas en cada esquina. Los esperamos allá».

> **Iván Salcedo, soldado de reserva (Talleres):** «En el entrenamiento la luz los detenía en seco y cada pasillo tenía salida. Aquí la luz apenas los debilita y los pasillos acaban en muros. Nada funciona como nos lo enseñaron».

> **Elena Cruz, soldado de escolta (Muelle):** «Íbamos a evacuar al personal técnico por el Muelle. En el último momento cambiaron la prioridad: primero las cajas selladas del laboratorio. Los heridos se quedaron esperando el siguiente transporte. No hubo siguiente transporte».

> **Celia Duarte, soldado especialista, sanitaria (Enfermería):** «Tercer operativo con fiebre, temblores y manchas violetas en la piel, y ninguno tiene heridas de combate. Pedí una evaluación médica hace dos días. Sigo sin respuesta».

> **Renata Solís, soldado especialista, reconocimiento (Contención):** «Llevo horas observándolos. Rodean las zonas iluminadas y esperan a que la luz se apague; en la oscuridad se mueven sin prisa. Si tienen linterna, no la dejen apagarse».

> **Hugo Cárdenas, soldado especialista, zapador (Procesamiento):** «Cargas colocadas en el acceso de Procesamiento. La orden es cerrar la ruta ahora. Hace una hora se oían golpes del otro lado; no sé si eran ellos o los nuestros. Cumplo la orden».

> **Mara Soria, cabo, operadora de campo (Sala de Máquinas):** «Última posición conocida: Alfa en el Vestíbulo, Bravo junto al Pozo, Delta rumbo al Muelle. Perdí contacto con las tres en menos de diez minutos. Sigo llamando».

> **Bruno Leal, cabo, técnico de mantenimiento (Sala de Máquinas):** «Reparé este generador por tercera vez con piezas de otros equipos. Avisé que la red no soportaría la carga del Pozo y me ordenaron mantenerla funcionando. Esto no es una reparación, es un parche».

> **Óscar Valdés, cabo, jefe de equipo (Almacén):** «Dejé mi posición para buscar agua y raciones; mis soldados llevan dos días sin comer. Si me reportan por abandonar el puesto, que conste por qué lo hice».

> **Julián Ocampo, cabo, custodio de documentación (Archivo):** «Me entregaron estos informes sellados con una sola orden: sacarlos de aquí sin abrirlos. Si no lo consigo, que alguien los lleve por mí».

> **Mateo Orduña, sargento de infantería (Vestíbulo):** «Bajas de la unidad: catorce. Solicitud de relevo número cinco. Respuesta: mantener la posición. Anoto sus nombres en la lista para que alguien los lea».

> **Vera Santillán, sargento, especialista en riesgos extranormales (Pozo):** «Lecturas junto al Pozo: cuatro veces el límite de exposición autorizado. El protocolo ordena evacuar al doble. Informé las cifras y me ordenaron recalibrar el equipo».

> **Gabriel Téllez, sargento, sanitario de combate (Cuarentena):** «Comparé los casos uno por uno: los mismos síntomas en operativos que nunca fueron heridos ni tocados por un infectado. No se contagian por contacto. Es algo de este lugar».

> **Andrés Neri, sargento, armero (Talleres):** «Ajusté las miras y reforcé los cerrojos otra vez. Contra los que conservan forma humana bastan unas ráfagas; a los de cuatro extremidades hay que vaciarles el cargador. Mantengan la luz encima antes de disparar».

> **Paula Esquivel, subteniente de reconocimiento (Galería):** «Los planos que nos entregaron no muestran este acceso, ni la sala de atrás, ni el pasillo que encontramos ayer. Alguien sabía que existían y decidió no incluirlos».

> **Damián Robles, subteniente de seguridad (Contención):** «Registro de accesos: tres personas con autorización entraron en Contención, un sector clausurado desde el primer día. No eran de los nuestros. Salieron con cajas».

> **Inés Roldán, teniente de infantería (Anillo):** «Solicitud de retirada rechazada por tercera vez. Mis soldados cumplieron cada orden que recibieron. Si esto termina mal, la responsabilidad no es de ellos, sino de quien decidió dejarnos aquí».

> **Darío Mena, teniente de operaciones (Laboratorio Oeste):** «Informe sobre la respuesta de los infectados a la luz, cuarta versión. Las tres anteriores me las devolvieron corregidas y en cada una faltaba un párrafo. Guardo aquí la original».

> **Lucía Ferrán, teniente, enlace científico (Laboratorio Oeste):** «Los investigadores pidieron suspender el procedimiento y el mando lo mantuvo. El doctor Issac Ferrer guarda copia de todo. Dejo en este equipo la frecuencia de su canal; sigue abierto para quien quiera escuchar».

> **Adela Voss, capitana de contención (Muelle):** «La orden era cerrar el corredor del Muelle. Lo mantuve abierto dos horas más para sacar a los técnicos que quedaban. Lo volvería a hacer. Que me juzgue quien haya estado aquí».

> **Esteban Arce, capitán de intervención (Procesamiento):** «El informe previo hablaba de una contención menor; lo que encontramos es otra cosa. Solicito identificar a quien autorizó este despliegue con esa información».

> **Rodrigo Valcárcel, mayor, coordinador de intervención (Laboratorio Este):** «Primera advertencia sobre la exposición: día 3. Autorización del segundo despliegue: día 9. Dejo la cronología completa en este equipo».

> **Beatriz Alcázar, comandante de seguridad del complejo (Pozo):** «Primera orden: limitar la exposición del personal. Segunda orden, con la misma fecha: mantener la extracción en el Pozo. No se pueden cumplir las dos».

## Tono

El lenguaje es sobrio, directo y acorde con una operación militar en un entorno desconocido. La tensión surge de la información incompleta, el deterioro de las instalaciones y las contradicciones entre testimonios.

|Fuente|Estilo|
|---|---|
|Nicolás|Profesional y preciso. Su preocupación aparece en pausas y cambios de tono|
|Issac|Analítico y cauteloso. Explica sus hallazgos sin convertir cada conversación en una exposición científica|
|Soldados|Lenguaje cotidiano, referencias a compañeros y preocupaciones inmediatas|
|Oficiales|Informes estructurados, órdenes y justificaciones de decisiones|
|Documentos institucionales|Lenguaje técnico e impersonal que contrasta con las consecuencias humanas|
El humor, si aparece, será ocasional y propio de la convivencia entre operativos. No debe quitar peso a las muertes ni interrumpir las revelaciones importantes.
## Decisiones narrativas

| Decisión                          | Opciones                                                       | Consecuencia                                                                 |
| --------------------------------- | -------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| Consultar registros               | Leerlos o continuar                                            | Amplía el conocimiento sobre las operaciones anteriores                      |
| Explorar el contenido de Issac    | Atender sus peticiones o seguir únicamente la misión principal | Determina la posibilidad de acceder al final alternativo                     |
| Completar las peticiones de Issac | Cumplirlas todas o dejarlas incompletas                        | Al vencer al Ascendido, determina el final de victoria                                   |
Los finales dependen de las acciones realizadas durante la partida. No se requiere una elección de diálogo al terminar para decidir qué desenlace se muestra.
## Localización

**Propuesta inicial:** Español como idioma principal. Inglés como posible localización posterior.

Los textos de interfaz, subtítulos, registros y pantallas de resultado deben mantenerse separados de las imágenes para facilitar su traducción.

Los nombres propios **Hades**, **Vimer** y **CERBERUS** se conservan. Los rangos, objetivos e indicaciones se adaptan al idioma correspondiente.

Las formas del nombre de **CERBERUS** en español e inglés son:
Comando de Emergencias, Recuperación Biológica, Exploración, Resguardo Urbano y Seguridad.
Centralized Emergency Response Bureau for Extranormal Recovery & Urban Security.

La disponibilidad de voces y doblaje está por definir. Toda información narrativa esencial debe ser comprensible mediante texto.


> **Navegación:** [[00 - Índice]] · ← [[03 - Personajes]] · [[01 - Estructura del Contenido]] →
