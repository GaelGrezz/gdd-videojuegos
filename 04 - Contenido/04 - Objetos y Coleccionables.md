# Objetos y Coleccionables

## Descripción de la sección

Define objetos que el jugador puede recoger, utilizar, equipar, vender, intercambiar o descubrir.

## Plantilla

### Nombre

**Tipo:**

**Descripción:**

**Función:**

**Cómo se obtiene:**

**Cómo se utiliza:**

**Cantidad máxima:**

**Valor:**

**Rareza:**

**Restricciones:**

**Interacciones:**

**Representación visual:**

## Objetos

### Cristal

**Tipo:** Recurso de progresión.

**Descripción:** Fragmento violeta que dejan los enemigos eliminados durante la partida.

**Función:** Aumentar el progreso hacia el siguiente nivel para escoger una mejora.

**Cómo se obtiene:** Lo sueltan los enemigos al ser eliminados. La cantidad depende de la dificultad del enemigo; se propone 1 por Cáscara y 4 por Quimera. El Ascendido no suelta cristales.

**Cómo se utiliza:** Se recoge al entrar en el radio de recolección y suma al contador de nivel. Al alcanzar la cantidad requerida, el jugador escoge una mejora.

**Cantidad máxima:** La requerida por nivel. Se proponen 5 cristales para el primer nivel y 3 más por cada nivel siguiente.

**Valor:** Cada cristal suma 1 al contador.

**Rareza:** No aplica.

**Restricciones:** Desaparece si no se recoge a tiempo; se proponen 20 s. El contador vuelve a cero al confirmar la mejora, incluidos los cristales sobrantes.

**Interacciones:** *Recolector magnético* (CAR-020) amplía el radio de recolección. Los cristales no adelantan el reloj de partida.

**Representación visual:** Cristal violeta `#C18AFF` de caras geométricas. En el HUD se muestra como gemas. Se propone que parpadee durante sus últimos 5 s.

### Arma inicial

**Tipo:** Equipo.

**Descripción:** Rifle bullpup con el que el soldado comienza la partida. Su nombre oficial está por definir.

**Función:** Atacar a los infectados en la misma dirección que apunta la linterna.

**Cómo se obtiene:** El soldado comienza equipado con ella.

**Cómo se utiliza:** Se apunta con el cursor y se dispara con clic izquierdo. Se recarga con R o al vaciar el cargador.

**Cantidad máxima:** 1 arma y 12 balas en el cargador. La munición de reserva está por definir.

**Valor:** 20 de daño, 3 disparos/s y 1.8 s de recarga. El alcance depende de la escala: 28.8 m en `AfterLight_Stats.xlsx` y 12 m en el prototipo.

**Rareza:** No aplica.

**Restricciones:** No dispara mientras recarga. El prototipo no incluye tienda ni nuevas armas.

**Interacciones:** Los enemigos iluminados reciben +25 % de daño. Las cartas CAR-012 a CAR-016 y los potenciadores de racha modifican sus estadísticas.

**Representación visual:** Rifle bullpup de CERBERUS en las manos del soldado, con fogonazo al disparar. Modelo de 620 triángulos con textura de color de 256 px.

### Mejora

**Tipo:** Carta de mejora.

**Descripción:** Modificación que dura el resto de la partida. Su catálogo está en `AfterLight_Stats.xlsx`.

**Función:** Adaptar la estrategia del jugador mediante cambios en el soldado, la linterna, el arma o los generadores.

**Cómo se obtiene:** Se escoge una al subir de nivel con cristales. Se proponen 3 opciones por selección.

**Cómo se utiliza:** Se aplica al confirmarla, con la partida en pausa.

**Cantidad máxima:** Cada carta tiene un nivel máximo de 3 a 5. Al alcanzarlo deja de aparecer.

**Valor:** El efecto por nivel de cada carta.

**Rareza:** No aplica.

**Restricciones:** No se conserva entre partidas. CAR-006 y CAR-018 no aplican en el prototipo.

**Interacciones:** GEN-001 (*Carcasa reforzada*) y GEN-002 (*Bobinas de inducción*) son propuestas para mejorar los generadores.

**Representación visual:** Carta de la pantalla *Elige una mejora* ([[02 - UI y Menús]]).

## Coleccionables

### Registro

**Tipo:** Coleccionable narrativo.

**Descripción:** Archivo que conserva el testimonio de un operativo fallecido.

**Función:** Ampliar la historia y, en algunos casos, contribuir a las peticiones de Issac.

**Cómo se obtiene:** Se recupera del cuerpo o el equipo de cada operativo.

**Cómo se utiliza:** Se consulta al recuperarlo o después, desde el archivo del jugador.

**Cantidad máxima:** 28 propuestos. La cantidad final se ajustará al mapa.

**Valor:** Información. No entrega recursos.

**Rareza:** No aplica. Cada registro es un hallazgo independiente.

**Restricciones:** No se puede responder a su autor. Su contenido se limita a lo que el personaje sabía antes de morir.

**Interacciones:** Los registros de Lucía Ferrán, Julián Ocampo, Rodrigo Valcárcel y Beatriz Alcázar son necesarios para las peticiones de Issac y deben tener una disponibilidad garantizada. Los que se recojan antes de recibir la petición cuentan de forma retroactiva.

**Representación visual:** Restos de operativos con uniforme y equipo acordes con su función. El rango se reconoce por insignias o identificación.

## Decisiones pendientes

- Si todos los enemigos sueltan cristales siempre o según una probabilidad. [[06 - Economía y Recursos]], [[03 - Enemigos y NPC]] y [[01 - Glosario]] usan criterios distintos; en el prototipo caen siempre.
- Munición de reserva: es infinita en el prototipo.
- Nombre oficial del arma inicial.
- Alcance del arma y radio de recolección según la escala de `AfterLight_Stats.xlsx`.
- Formato de los registros, si leerlos pausa la partida y si se conservan entre partidas.


> **Navegación:** [[00 - Índice]] · ← [[03 - Enemigos y NPC]] · [[05 - Misiones y Desafíos]] →
