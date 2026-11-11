# UI y Menús

## Descripción de la sección

Define la estructura funcional de las interfaces y menús.

## Mapa de navegación

```text
Menú principal
├── Iniciar despliegue → Carga → Partida
├── Opciones
├── Créditos
└── Abandonar sistema → Salir del juego

Carga
└── Error de carga → Reintentar / Menú principal

Partida
├── ESC → Pausa
│   ├── Reanudar
│   ├── Opciones
│   ├── Reiniciar partida → Confirmación → Carga
│   └── Abandonar sistema → Confirmación → Menú principal
├── Archivo del jugador
├── Cristales completos → Elige una mejora → Partida
├── Game Over → Reintentar / Menú principal
└── Victoria → Menú principal
```

## Pantallas

### Menú principal

**Propósito:** Iniciar la partida, consultar opciones o salir del juego.

**Elementos:** Emblema del lobo de CERBERUS sobre el logotipo *AFTER LIGHT* («LIGHT» en rojo), el lema «La oscuridad te espera», un haz de luz diagonal, partículas y la ayuda de controles (↑ ↓ seleccionar, Enter confirmar).

![[UI - Menú principal.png]]

**Acciones disponibles:** Iniciar despliegue, Opciones, Créditos y Abandonar sistema.

**Estados:** La opción seleccionada aparece en negrita, en un tono claro y con dos destellos a los lados; las demás, en gris y entre guiones.

**Transiciones:** Iniciar despliegue → Carga → Jugando. Opciones → Opciones. Créditos → Créditos. Abandonar sistema → Salir del juego.

### HUD

**Propósito:** Mantener visible durante la partida la información necesaria para decidir.

**Elementos:** Vida, batería, generadores (nombre, estado y porcentaje), reloj hasta la llegada del Ascendido, nivel, cristales, racha, potenciadores, mira, indicación de interacción con E y su progreso, munición con aviso de recarga, avisos de generador bajo ataque y de arma sin munición, y mensajes de Enlace.

![[UI - HUD.png]]

![[UI - HUD en riesgo.png]]

![[UI - Contacto con Issac.png]]

**Acciones disponibles:** Ninguna directa; muestra el resultado de las acciones del jugador.

**Estados:** Vida normal y en regeneración; batería normal, baja, vacía con cuenta regresiva y en recarga; generador operativo, en reparación, averiado, bajo ataque, destruido o con espera antes de poder reparar; daño recibido; aviso de recarga cuando queda poca munición; indicación de interacción cuando hay un generador cerca; barra del Ascendido durante el combate final y panel de contacto con Issac.

**Transiciones:** ESC → Pausa. Cristales completos → Elige una mejora. Fin de la partida → Victoria o Game Over.

### Elige una mejora

**Propósito:** Elegir una mejora al subir de nivel. La partida permanece en pausa.

**Elementos:** Título «Subida de nivel / Elige una mejora», tres cartas (categoría, nombre, nivel actual sobre el máximo, efecto y botón Elegir) y el mensaje de Enlace.

![[UI - Elige una mejora.png]]

**Acciones disponibles:** Elegir una de las tres cartas.

**Estados:** Carta seleccionada (borde claro y botón rojo) o sin seleccionar.

**Transiciones:** Elegir → se aplica la mejora, el contador de cristales vuelve a cero y la partida continúa.

### Pausa

**Propósito:** Detener la simulación y permitir consultar opciones, reiniciar o abandonar la partida.

**Elementos:** Título «Sistema en espera / Pausa», el lema «La partida espera en la oscuridad», las opciones, un resumen de la partida (tiempo hasta el Ascendido, nivel, racha y generadores operativos) y la ayuda de controles (↑ ↓ seleccionar, Enter confirmar, ESC reanudar).

![[UI - Pausa.png]]

**Acciones disponibles:** Reanudar, Opciones, Reiniciar partida y Abandonar sistema.

**Estados:** Igual que el menú principal: opción seleccionada en negrita con destellos; las demás, en gris.

**Transiciones:** Reanudar o ESC → Jugando. Opciones → Opciones. Reiniciar partida → Confirmación → Carga. Abandonar sistema → Confirmación → Menú principal.

### Carga

**Propósito:** Preparar la partida y acompañar la espera con un mensaje de Enlace.

**Elementos:** Título «Centro científico de Hades / Preparando despliegue», barra de progreso y mensaje de Enlace. La carga es asíncrona, permanece al menos 1.5 s y termina con un fundido de 0.35 s. El mensaje actual es «Eco-10, ilumina al objetivo antes de abrir fuego».

![[UI - Carga.png]]

![[UI - Error de carga.png]]

**Acciones disponibles:** Ninguna mientras carga. Si falla, Reintentar y Menú principal.

**Estados:** Cargando o error de carga, con el título «Despliegue interrumpido» y el aviso de que faltan elementos indispensables.

**Transiciones:** Carga completa → Jugando. Reintentar → Carga. Menú principal → Menú principal.

### Opciones

**Propósito:** Ajustar el audio, el video, los controles y la accesibilidad.

**Elementos:** Título «Configuración / Opciones» y cuatro paneles: Audio (volumen general, música, efectos y voces), Video (resolución, pantalla completa, filtro VHS y brillo), Controles (mover, interactuar, recargar, disparar y pausa) y Accesibilidad (subtítulos y tamaño de texto).

![[UI - Opciones.png]]

**Acciones disponibles:** Cambiar de sección con ← →, elegir un ajuste con ↑ ↓ y Volver.

**Estados:** Ajuste seleccionado; los volúmenes y el brillo muestran su valor en una barra.

**Transiciones:** Volver o ESC → pantalla anterior.

### Créditos

**Propósito:** Mostrar a los responsables del proyecto.

**Elementos:** Título «AfterLight / Créditos», responsable del proyecto, equipo, guía del GDD y el botón Volver.

![[UI - Créditos.png]]

**Acciones disponibles:** Volver.

**Estados:** No aplica.

**Transiciones:** Volver o ESC → Menú principal.

### Archivo del jugador

**Propósito:** Consultar los registros recuperados de los operativos fallecidos.

**Elementos:** Título «Registros recuperados / Archivo» con el conteo sobre 28, lista de registros con nombre y cargo, y panel con el registro seleccionado.

![[UI - Archivo del jugador.png]]

**Acciones disponibles:** Seleccionar con ↑ ↓, leer con Enter y volver con ESC.

**Estados:** Registro seleccionado, con fondo rojo y borde claro; recuperado; o sin recuperar, en gris.

**Transiciones:** ESC → pantalla anterior.

### Victoria

**Propósito:** Cerrar la partida con el final obtenido.

**Elementos:** Fondo negro, encabezado «Operación Umbral completada», título del final, mensaje de Enlace o de Issac y resumen de tiempo, nivel, registros recuperados y generadores operativos.

**Información recuperada**

![[UI - Victoria.png]]

**Ni uno más**

![[UI - Victoria - Ni uno más.png]]

**Acciones disponibles:** Volver al menú.

**Estados:** *Información recuperada* o *Ni uno más*.

**Transiciones:** Volver al menú → Menú principal.

### Game Over

**Propósito:** Mostrar la causa de la derrota y ofrecer un nuevo intento.

**Elementos:** Fondo negro, encabezado «Game Over», título y explicación de la causa, resumen de tiempo, nivel, registros recuperados y generadores operativos.

**Operativo caído**

![[UI - Game Over.png]]

**Sin luz**

![[UI - Game Over - Sin luz.png]]

**Acciones disponibles:** Reintentar y Menú principal.

**Estados:** *Operativo caído* si la salud llega a cero y *Sin luz* si la batería agota el periodo de tolerancia.

**Transiciones:** La derrota abre directamente Game Over. Reintentar carga una partida nueva. Menú principal regresa al menú.

## Confirmaciones

Documenta acciones destructivas o irreversibles y cómo se confirman.

| Acción | Pantalla | Confirmación |
| --- | --- | --- |
| Abandonar la partida | Pausa | Diálogo que avisa que se perderá el progreso; *Cancelar* es la opción predeterminada |
| Reiniciar la partida | Pausa | Igual que abandonar: se pierden el tiempo, las mejoras y los cristales |
| Salir del juego | Menú principal | Opcional; no hay progreso que perder |

Reintentar desde Game Over no requiere confirmación.

![[UI - Confirmación.png]]

## Estado en Unity

`CentroHades.unity` incorpora HUD, pausa, selección de mejoras, comunicaciones de Issac, Game Over y Victoria. El prefab `FinPartida` muestra ambos desenlaces con el resumen de la sesión. Opciones, Créditos y Carga tienen prefabs propios.

Los 28 registros se recogen en el escenario y se leen en el panel de comunicaciones durante la partida. El panel encola los textos de Issac y los registros y ajusta su duración a la longitud del mensaje. La pantalla independiente del Archivo del jugador queda para versiones posteriores. En la primera versión se consulta cada registro al recogerlo.

## Decisiones pendientes

- Definir cómo se abre el Archivo del jugador durante la partida.
- Usar textos distintos para *Abandonar sistema*: en el menú principal cierra el juego y en la pausa regresa al menú.
- El logotipo dice *AFTER LIGHT*; el [[01 - Glosario]] pide *AfterLight*.


> **Navegación:** [[00 - Índice]] · ← [[01 - UX y Flujo del Jugador]] · [[03 - Accesibilidad]] →
