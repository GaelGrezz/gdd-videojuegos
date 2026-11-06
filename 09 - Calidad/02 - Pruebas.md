# Pruebas

## Descripción de la sección

Define cómo se comprobará que el videojuego funciona como fue diseñado.

## Tipos de prueba

### Pruebas funcionales

Comprueban que una característica haga lo que debe.

Linterna y batería, arma inicial, generadores, director, enemigos, cristales y mejoras, racha y regeneración de la salud, según las reglas de [[03 - Sistemas]] y [[02 - Mecánicas]].

### Pruebas de integración

Comprueban que varios sistemas funcionen correctamente juntos.

Las transiciones de [[07 - Reglas y Estados del Juego]]: que la pausa y la selección de mejora detengan la simulación, que el director se detenga durante el combate contra el Ascendido y que reintentar restablezca la partida.

### Pruebas de usabilidad

Comprueban si los jugadores entienden y pueden utilizar el sistema.

Que un jugador sin experiencia en el género complete los primeros minutos de [[01 - UX y Flujo del Jugador]] y pueda explicar el objetivo y la causa de su derrota. La forma de realizarlas está por definir.

### Pruebas de rendimiento

Comprueban FPS, memoria, tiempos de carga y estabilidad.

Por definir hasta fijar los objetivos de [[03 - Requisitos Técnicos]].

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

## Casos del proyecto

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

### Derrota por salud

**Objetivo:** Comprobar la derrota *Operativo caído*.

**Precondiciones:** Partida en curso.

**Pasos:**

1. Dejar que los Vimers ataquen al soldado.
2. Esperar a que la salud llegue a cero.

**Resultado esperado:** Se presenta la derrota según el atacante y después Game Over con el título *Operativo caído*, el resumen de la partida, Reintentar y Menú principal.

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


> **Navegación:** [[00 - Índice]] · ← [[01 - Criterios de Calidad]] · [[03 - Bugs y Seguimiento]] →
