# Interfaz Visual

## Descripción de la sección

Documenta la información que el juego muestra al jugador y las reglas visuales de la interfaz.

## HUD

Elementos:

- **Vida:** barra arriba a la izquierda.
- **Energía:** batería de la linterna bajo la vida, en 10 celdas, con aviso de batería baja y cuenta regresiva al 0 %.
- **Munición:** abajo a la derecha. Las balas restantes van en un número grande y rojo junto al total del cargador, con el aviso «R Recargar».
- **Objetivo:** reloj hasta la llegada del Ascendido (arriba al centro) y estado de cada generador (a la izquierda).
- **Mapa:** no se incluye.
- **Recursos:** nivel, cristales (gemas violetas), racha y potenciadores, arriba a la derecha.
- **Indicadores contextuales:** mira, interacción con E y su progreso, aviso de recarga, mensajes de Enlace y contacto con Issac. Durante el combate final, la barra del Ascendido sustituye al reloj. Al aparecer el Ascendido, un aviso arriba al centro indica la zona y la distancia, y un rombo rojo con su distancia lo sigue durante todo el combate; si queda fuera de la pantalla, se pega al borde con una flecha hacia él.

## Jerarquía visual

¿Qué información debe verse primero, segundo y tercero?

1. Vida, batería y mira: lo que puede causar la derrota.
2. Reloj del Ascendido, estado de los generadores y munición.
3. Nivel, cristales, racha, potenciadores y mensajes de Enlace.

## Estados

Documenta estados normales, advertencias, daño, éxito, error y bloqueo.

| Estado | Señal en el diseño | Color en [[01 - Dirección de Arte]] |
| --- | --- | --- |
| Normal | Texto blanco y etiquetas grises | Blanco suave `#ECEAE4` |
| Seleccionado | Opción en negrita con destellos; carta con borde claro y botón rojo | Rosa claro `#FFD9DC` |
| Éxito (generador operativo) | Texto «Operativo» y rayo en verde | Verde suave `#8CCB9B` |
| En progreso (reparación, recarga y regeneración) | Barra y texto de estado en rosa claro | Rosa claro `#FFD9DC` |
| Advertencia (batería baja) | Celdas y porcentaje en ámbar, con el aviso «Batería baja» | Ámbar `#F2B85B` |
| Peligro (generador averiado o bajo ataque) | Texto y rayo rojos; bajo ataque, además, fila con marco rojo | Rojo intenso `#FF5964` |
| Sin batería | Celdas vacías con borde rojo, barra de tolerancia y cuenta regresiva | Rojo intenso `#FF5964` |
| Daño | Viñeta roja en los bordes de la pantalla, debajo del HUD | Rojo intenso `#FF5964` |
| Error (carga fallida) | Pantalla «Error de carga» con Reintentar y Menú principal | Rojo intenso `#FF5964` |
| Bloqueo (registro sin recuperar) | Texto «Registro sin recuperar» en gris | Gris medio `#8A8A8A` |
| Cristales | Gemas violetas, apagadas cuando faltan | Violeta `#C18AFF` |

## Convenciones

**Tipografía:** *Kdam Thmor* para el logotipo. *Kelly Slab* para títulos, números y nombres. *Inter* (Bold y Regular) para etiquetas, botones, opciones de menú y mensajes de Enlace. Cada texto usa uno de estos estilos, medidos a 1920 × 1080:

| Uso | Fuente | Tamaño |
| --- | --- | --- |
| Logotipo | Kdam Thmor | 150 y 84 px |
| Título de pantalla | Kelly Slab | 150 y 96 px |
| Munición | Kelly Slab | 92 px |
| Reloj, nivel y racha | Kelly Slab | 52 px |
| Subtítulo y pregunta de confirmación | Kelly Slab | 44 px |
| Total del cargador y nombres de los créditos | Kelly Slab | 32 px |
| Nombre de mejora, de registro y del Ascendido | Kelly Slab | 24 px |
| Generadores, valores y porcentajes | Kelly Slab | 18 px |
| Estados y potenciadores | Kelly Slab | 14 px |
| Opción seleccionada y resumen de partida | Inter Bold | 26 px |
| Antetítulo | Inter Bold | 22 px |
| Botón | Inter Bold | 16 px |
| Etiqueta | Inter Bold | 14 px |
| Opción de menú y diálogo destacado | Inter Regular | 22 px |
| Mensajes de Enlace y descripciones | Inter Regular | 20 px |
| Texto secundario | Inter Regular | 16 px |
| Ayuda de controles y detalle | Inter Regular | 14 px |

**Iconografía:** Rayo de 16 × 30 px para los generadores (verde si están operativos, rosa claro en reparación y rojo si están averiados), gemas de 67 × 58 px para los cristales, teclas dentro de un recuadro (E, R), retícula circular de 48 × 48 px y el emblema del lobo de CERBERUS en el menú principal.

**Tamaños mínimos:** La interfaz se diseña a 1920 × 1080. El texto mínimo es de 14 px y solo se usa en etiquetas, estados y ayudas; los textos de lectura miden 20 px. Los márgenes de pantalla son de 64 px. Medidas de cada elemento:

| Elemento | Posición | Tamaño |
| --- | --- | --- |
| Vida | x 64, y 64 | 330 × 46 px |
| Batería | x 64, y 134 | 330 × 44 px |
| Generadores | x 56, y 326, una fila cada 56 px | 300 × 57 px |
| Reloj del Ascendido | Centrado, y 24 | 240 px de ancho, cifras de 34 px |
| Nivel, cristales y racha | x 1444, y 64 | 412 px de ancho |
| Potenciadores | Bajo la racha, alineados a la derecha hasta x 1856, y 136 | Texto rojo de 14 px |
| Munición | El número termina en x 1696 y el cargador va de x 1706 a 1856, en y 833 | Según el número |
| Aviso de recarga | x 1720, y 777, encima de la munición | 136 × 40 px |
| Interacción | x 794, y 792 | Tecla de 40 × 40 px y barra de 260 px |
| Mensaje de Enlace | Centrado, y 952 | Según el texto, centrado |
| Barra del Ascendido | Centrada | 640 × 72 px |
| Botón | Según la pantalla | 280 × 48 px |
| Carta de mejora | Tres desde x 280, y 382, con 40 px entre ellas | 400 × 500 px |
| Diálogo de confirmación | Centrado | 720 × 317 px |
| Panel | Relleno blanco al 3 %, borde blanco al 14 % y radio de 3 px | Según la pantalla |
| Línea inferior y ayuda de controles | y 1040 e y 1055 | 1920 px de ancho |

**Contraste:** Fondo negro `#000000`. El texto alcanza al menos 4.5:1; los números de 44 px o más y las formas, al menos 3:1. Texto principal `#ECEAE4` (17.5:1), secundario `#C9C9C9` (12.7:1), etiquetas y ayudas `#8A8A8A` (6.1:1) y texto rojo `#FF5964` (6.9:1). El Rojo institucional `#B52D3A` (3.4:1) se reserva para botones, rellenos, el logotipo y los números grandes; sobre él, el texto `#ECEAE4` alcanza 5.1:1.

**Animaciones:** Por definir. Se proponen las del prototipo: la viñeta roja destella con cada golpe, acompañada de una sacudida breve de la cámara, y late con la vida baja; el aviso «R RECARGAR» late con poca munición, se llena una barra al recargar y, al disparar sin balas, el aviso se sacude y la munición parpadea; la pantalla se oscurece desde los bordes por debajo del 25 % de batería y la etiqueta «BATERÍA BAJA» parpadea en ámbar por debajo del 20 %; la alerta de batería vacía entra un poco más grande y su título late en rojo y blanco; los marcadores de los generadores bajo ataque parpadean; el mensaje de Enlace aparece y desaparece con un fundido de 0.5 s, y la pantalla de carga sale con un fundido de 0.35 s.

## Pantallas

- Menú principal: Iniciar despliegue abre la pantalla de carga y después comienza la partida.
- Carga: diseñada, con su pantalla de error.
- HUD: diseñado, con batería, daño, generadores en riesgo, combate contra el Ascendido y contacto con Issac.
- Elige una mejora: diseñada.
- Pausa: diseñada.
- Configuración: diseñada como pantalla de Opciones.
- Archivo del jugador: diseñada.
- Créditos: diseñada.
- Confirmaciones: diseñadas para abandonar y reiniciar.
- Inventario: no se incluye.
- Mapa: no se incluye.
- Victoria en Unity: fondo negro, encabezado rojo, título claro y mensaje de Enlace en *Información recuperada* o de Issac en *Ni uno más*.
- Game Over en Unity: fondo negro, encabezado rojo, causa y resumen. Aparece directamente al perder con *Operativo caído* o *Sin luz*.

Las pantallas y su navegación están en [[02 - UI y Menús]].

## Decisiones pendientes

- El rojo marca tanto el peligro como la racha, los potenciadores y los botones. Falta decidir si el peligro necesita además un icono o una animación.
- Definir las animaciones de la interfaz.
- Llevar a Figma los cambios del prototipo: el reloj del Ascendido más pequeño y pegado arriba (y 24, cifras de 34 px; el diseño lo tiene en y 64 con cifras de 52 px), el panel de comunicaciones centrado en la pantalla (x 480; el diseño lo tiene en x 440), con el texto centrado en vertical y el fondo algo transparente (el diseño es opaco), la munición y el aviso de recarga más a la derecha, con el aviso encima de la munición, para no tapar el panel (el diseño los tiene en x 1444 y x 1720, y 858), y el mensaje de Enlace centrado (el diseño lo tiene en x 592).
- El prototipo de Unity muestra debajo del reloj del Ascendido los avisos «Generador bajo ataque», con el nombre, la integridad y la distancia del generador, y «Sin munición», con el avance de la recarga; el diseño de Figma no incluye esos avisos.


> **Navegación:** [[00 - Índice]] · ← [[03 - Entornos]] · [[05 - Audio y Música]] →
