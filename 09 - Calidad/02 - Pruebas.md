# Pruebas

## Descripción de la sección

Define cómo se comprobará que el videojuego funciona como fue diseñado.

## Tipos de prueba

### Pruebas funcionales

Comprueban que una característica haga lo que debe.

Linterna y batería, arma inicial, generadores, director, enemigos, cristales y mejoras, racha y regeneración de la salud, según las reglas de [[03 - Sistemas]] y [[02 - Mecánicas]]. Comprobar la reproducción de la música y los efectos ya integrados, incluidos disparo, impacto, daño del jugador y daño del generador.

### Pruebas de integración

Comprueban que varios sistemas funcionen correctamente juntos.

Las transiciones de [[07 - Reglas y Estados del Juego]]: que la pausa y la selección de mejora detengan la simulación, que el director se detenga durante el combate contra el Ascendido y que reintentar restablezca la partida.

### Pruebas de usabilidad

Comprueban si los jugadores entienden y pueden utilizar el sistema.

Que un jugador sin experiencia en el género complete los primeros minutos de [[01 - UX y Flujo del Jugador]] y pueda explicar el objetivo y la causa de su derrota. La forma de realizarlas está por definir.

### Pruebas de rendimiento

Comprueban FPS, memoria, tiempos de carga y estabilidad.

Usar una compilación de Windows y los dos perfiles de [[03 - Requisitos Técnicos]]. Medir la carga desde Iniciar despliegue hasta recibir el control. Registrar FPS y pico de memoria durante una partida que llegue al Ascendido. Anotar equipo, resolución, API gráfica y versión de la compilación junto con los resultados.

## Caso de prueba

### Nombre

**Objetivo:**

**Precondiciones:**

**Pasos:**

1.
2.
3.

**Resultado esperado:**

**Resultado obtenido:**

**Estado:** Correcto / Incorrecto

## Atajos de desarrollo

En el editor y en compilaciones de desarrollo, F8 adelanta el reloj hasta 5 s antes del Ascendido. F9 abre *Operativo caído* y F10 abre *Información recuperada*. Los atajos de resultado permiten revisar la interfaz. Para validar las reglas hay que provocar la derrota o vencer al jefe en partida.

## Casos del proyecto

La revisión del GDD verificó conexiones en la escena, los prefabs y los scripts. Los casos siguientes quedan pendientes de ejecución en Unity.

### La pausa detiene la simulación

**Objetivo:** Comprobar que la pausa detiene la partida.

**Precondiciones:** Partida en curso con enemigos en pantalla y un generador en reparación.

**Pasos:**

1. Presionar ESC.
2. Esperar unos segundos.
3. Presionar ESC de nuevo.

**Resultado esperado:** Mientras la pausa está abierta no avanzan los enemigos, los proyectiles, la reparación, el consumo de batería ni el reloj. Al reanudar, todo continúa desde el mismo punto.

**Resultado obtenido:** Por definir.

**Estado:** Por definir.

### Espera de reparación del generador

**Precondiciones:** Partida en CentroHades y un generador averiado accesible.

**Pasos:**

1. Reparar el generador y observar el aviso de disponibilidad.
2. Dejar que pierda integridad e intentar restaurarlo antes y después de los 20 s.
3. Dejar que quede destruido e intentar repararlo antes y después de los 60 s.

**Resultado esperado:** La primera restauración queda disponible al terminar los 20 s. Tras la destrucción, la reparación queda disponible al terminar los 60 s y el generador pierde sus beneficios hasta volver a operar.

**Estado:** Pendiente de ejecución.

### Derrota por salud

**Objetivo:** Comprobar la derrota *Operativo caído*.

**Precondiciones:** Partida en curso.

**Pasos:**

1. Dejar que los Vimers ataquen al soldado.
2. Esperar a que la salud llegue a cero.

**Resultado esperado:** Se abre directamente Game Over con el título *Operativo caído*, el resumen de la partida, Reintentar y Menú principal.

**Resultado obtenido:** Por definir.

**Estado:** Por definir.

### Derrota sin batería

**Objetivo:** Comprobar la derrota *Sin luz* y la cancelación del periodo de tolerancia.

**Precondiciones:** Partida en curso con la batería cerca del 0 %.

**Pasos:**

1. Esperar a que la batería llegue al 0 %.
2. Volver a un generador operativo antes de que termine la cuenta regresiva.
3. Repetir sin volver al generador.

**Resultado esperado:** Al recuperar carga, la cuenta regresiva se cancela y se reinicia. Si se agota, la partida termina con *Sin luz*.

**Resultado obtenido:** Por definir.

**Estado:** Por definir.

### Selección de mejora

**Objetivo:** Comprobar la subida de nivel.

**Precondiciones:** Partida en curso con cristales cerca del requisito.

**Pasos:**

1. Recoger los cristales requeridos.
2. Elegir una de las tres cartas.

**Resultado esperado:** La partida queda en pausa mientras se elige. Se aplica la mejora, el contador de cristales vuelve a cero y la partida continúa.

**Resultado obtenido:** Por definir.

**Estado:** Por definir.

### Reintentar restablece la partida

**Objetivo:** Comprobar que una nueva partida empieza desde cero.

**Precondiciones:** Game Over abierto después de subir de nivel y reparar generadores.

**Pasos:**

1. Elegir Reintentar.

**Resultado esperado:** Se restablecen el tiempo, los enemigos, los generadores, la racha, las mejoras, los cristales y el resultado de la partida.

**Resultado obtenido:** Por definir.

**Estado:** Por definir.


### Victoria y final de Issac

**Objetivo:** Verificar la aparición del Ascendido y los dos desenlaces en la escena CentroHades.

**Precondiciones:** Partida iniciada desde el menú principal. Para probar el combate en el editor o en una compilación de desarrollo, F8 adelanta el reloj a 5 s de la aparición. La prueba del tiempo normal requiere esperar los 600 s de partida.

**Pasos:**

1. Verificar el aviso del HUD al aparecer el Ascendido y que el director deje de generar enemigos.
2. Derrotarlo sin completar las peticiones de Issac.
3. En otra partida, recuperar el registro de Lucía Ferrán y las tres pruebas, completar la terminal del Archivo y derrotar al Ascendido.

**Resultado esperado:** Se abre Victoria con *Información recuperada* en la primera partida y *Ni uno más* en la segunda. El resumen muestra el tiempo, el nivel, los registros y los generadores de cada sesión.

**Estado:** Pendiente de ejecución.

### Persistencia de opciones

**Objetivo:** Verificar que las opciones aplicadas se conservan entre ejecuciones y que los datos de partida se reinician.

**Pasos:**

1. Cambiar el volumen de música y efectos, la resolución y el modo de pantalla.
2. Iniciar una partida, recuperar un registro y volver al menú.
3. Cerrar el juego, abrirlo de nuevo y consultar Opciones.
4. Iniciar otra partida y verificar el conteo de registros, el reloj y el nivel.

**Resultado esperado:** Las preferencias conservan los valores elegidos. La nueva partida empieza con cero registros recuperados y con el reloj y el nivel iniciales.

**Estado:** Pendiente de ejecución.

> **Navegación:** [[00 - Índice]] · ← [[01 - Criterios de Calidad]] · [[03 - Bugs y Seguimiento]] →
