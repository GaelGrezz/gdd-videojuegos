# UX y Flujo del Jugador

## Descripción de la sección

UX (experiencia de usuario) describe qué tan comprensible, cómoda y coherente resulta la interacción con el videojuego.

## Flujo principal

```text
Inicio → Menú → Nueva partida → Tutorial → Juego → Pausa → Juego → Final
```

**Flujo del proyecto:**

```text
Menú principal → Iniciar despliegue → Carga → Entrada al complejo → Introducción con Nicolás → Supervivencia → Ascendido → Victoria o Derrota → Game Over → Menú principal
```

Durante la supervivencia y el combate final, ESC abre la pausa y reunir los cristales requeridos abre Elige una mejora; ambas regresan a la partida. Los detalles de cada pantalla están en [[02 - UI y Menús]].

## Primeros minutos

Documenta exactamente qué descubre y aprende el jugador.

1. En el menú principal ve al soldado frente a las puertas del complejo y la luz que entra por la abertura, como describe [[04 - Diálogos y Narrativa]].
2. Al elegir Iniciar, el soldado abre las puertas, la cámara pasa a la vista superior y el jugador recibe el control. El reloj empieza a correr.
3. Nicolás establece comunicación y presenta la misión: mantener la luz sobre lo que se mueva y recuperar la energía.
4. El jugador aprende a moverse con W, A, S y D en una zona de visibilidad limitada y descubre que el cursor orienta a la vez el arma y la linterna.
5. Con el primer infectado aprende que la luz lo debilita y que el disparo lo elimina. Nicolás le indica que lo ilumine.
6. Al encontrar el primer generador averiado aprende a repararlo con E y ve el progreso de la reparación.
7. Descubre que la batería se consume siempre y que se recarga junto a un generador operativo.
8. Con los primeros cristales sube de nivel y elige su primera mejora con la partida en pausa.

Cada instrucción de Nicolás aparece cuando corresponde realizar la acción, sin concentrar el tutorial en una sola conversación. La duración de la introducción está por definir.

## Retroalimentación

Para cada acción importante define:

**Entrada → Respuesta visual → Respuesta sonora → Resultado**

- **Disparar:** Clic izquierdo → fogonazo, bala e impacto → sonido del disparo → el arma gasta una bala del cargador.
- **Golpear a un Vimer:** Impacto de la bala → efecto de impacto y muerte del Vimer → sonido del golpe → el Vimer pierde salud y, al morir, suelta cristales.
- **Iluminar a un Vimer:** Mover el cursor → el cono de luz cubre al Vimer y este muestra que está debilitado → por definir → el Vimer recibe los efectos de la linterna.
- **Recargar:** R o cargador vacío → indicador de recarga en el HUD → por definir → el cargador vuelve a estar lleno.
- **Reparar un generador:** E cerca de un generador → indicación de E, barra de progreso y estado del generador → por definir → el generador queda operativo.
- **Recibir daño:** Ataque de un Vimer → indicación de daño recibido y barra de vida → sonido de daño recibido → el soldado pierde salud y la racha se reinicia.
- **Defender un generador:** Un Vimer ataca el generador → estado «bajo ataque» en el HUD → sonido del generador dañado → el generador pierde integridad.
- **Quedarse sin batería:** La batería llega al 0 % → batería vacía con cuenta regresiva → por definir → si no se recarga a tiempo, derrota por *Sin luz*.
- **Subir de nivel:** Reunir los cristales requeridos → pantalla Elige una mejora → por definir → se aplica la mejora y el contador de cristales vuelve a cero.

## Fricción intencional

¿Qué dificultad forma parte del diseño y qué dificultad es simplemente mala experiencia de usuario?

**Forma parte del diseño:**

- La baja visibilidad y el cono de luz limitado, que obligan a orientar la linterna.
- El consumo constante de batería, que obliga a volver a los generadores.
- La llegada de enemigos durante una reparación, que obliga a decidir cuándo volver al objetivo.
- El aumento de la presión del director conforme pasa el tiempo.
- La pérdida de la racha al recibir daño.

**Es mala experiencia de usuario:**

- Que la oscuridad oculte las señales necesarias para responder a un ataque.
- No saber dónde está un generador ni en qué estado se encuentra.
- Que un clic en un menú provoque un disparo.
- Perder sin entender la causa.
- Que el filtro VHS impida leer la interfaz.

## Descubrimiento

¿Cómo sabe el jugador:

- Qué hacer?
- Dónde ir?
- Qué puede interactuar?
- Qué ocurrió?
- Por qué ganó o perdió?

- **Qué hacer:** Por las comunicaciones de Nicolás, que aparecen al encontrar cada situación por primera vez, y por el reloj hasta la llegada del Ascendido.
- **Dónde ir:** Por el estado de los generadores en el HUD y las fuentes de luz del escenario. Las señales de ubicación de los generadores están por definir.
- **Qué puede interactuar:** Por la indicación de E que aparece cerca de un generador o de un objeto válido.
- **Qué ocurrió:** Por la retroalimentación de cada acción, los mensajes de Enlace y los estados del HUD.
- **Por qué ganó o perdió:** Por el título y la explicación de la pantalla final: *Operativo caído*, *Sin luz*, *Información recuperada* o *Ni uno más*, con el resumen de la partida.


> **Navegación:** [[00 - Índice]] · ← [[05 - Audio y Música]] · [[02 - UI y Menús]] →
