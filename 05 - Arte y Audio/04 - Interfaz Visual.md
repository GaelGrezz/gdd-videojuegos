# Interfaz Visual

## Descripción de la sección

Documenta la información que el juego muestra al jugador y las reglas visuales de la interfaz.

## HUD

Elementos:

- **Vida:** barra arriba a la izquierda.
- **Energía:** batería de la linterna, por diseñar.
- **Munición:** abajo a la derecha. Las balas restantes van en un número grande y rojo junto al total del cargador, con el aviso «R Recargar».
- **Objetivo:** reloj hasta la llegada del Ascendido (arriba al centro) y estado de cada generador (a la izquierda).
- **Mapa:** no se incluye.
- **Recursos:** nivel, cristales (gemas violetas), racha y potenciadores, arriba a la derecha.
- **Indicadores contextuales:** mira, interacción con E y su progreso, aviso de recarga y mensajes de Enlace.

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
| Seleccionado | Opción en negrita con destellos; carta con borde claro y botón rojo | — |
| Éxito (generador operativo) | Texto blanco «Operativo» | Verde suave `#8CCB9B` |
| Advertencia (batería baja) | Por diseñar | Ámbar `#F2B85B` |
| Peligro (generador averiado) | Texto e icono rojos | Rojo intenso `#FF5964` |
| Daño | Por diseñar | Rojo intenso `#FF5964` |
| Cristales | Gemas violetas, apagadas cuando faltan | Violeta `#C18AFF` |

## Convenciones

**Tipografía:** *Kdam Thmor* para el logotipo. *Kelly Slab* para títulos, números y nombres (PAUSA, ELIGE UNA MEJORA, el reloj, la munición, los generadores y las cartas). *Inter* (Bold y Regular) para etiquetas, opciones de menú y mensajes de Enlace.

**Iconografía:** Rayo para los generadores (rojo si están averiados), gemas para los cristales, teclas dentro de un recuadro (E, R), retícula circular y el emblema del lobo de Cerberus en el menú principal.

**Tamaños mínimos:** Por definir. Las etiquetas del HUD miden 12 px a 1080p y las del resumen de la pausa, 10 px.

**Contraste:** Fondo negro. Texto principal en `#F2F2F2`, etiquetas en `#8A8A8A` y acentos en rojo `#C1121F`.

**Animaciones:** Por definir.

## Pantallas

- Menú principal: diseñada.
- HUD: diseñado, sin la batería.
- Elige una mejora: diseñada.
- Pausa: diseñada.
- Configuración: por diseñar.
- Inventario: no se incluye.
- Mapa: no se incluye.
- Victoria: por diseñar.
- Derrota: por diseñar.

Las pantallas y su navegación están en [[02 - UI y Menús]].

## Decisiones pendientes

- Diseñar el indicador de batería con sus estados normal, baja y vacía, esta última con cuenta regresiva.
- El rojo marca tanto el peligro como la racha, los potenciadores y los botones. Falta decidir si el peligro necesita además un icono o una animación.
- El estado operativo no usa el verde de la paleta jugable.
- Definir un tamaño mínimo de texto; la regla visual 10 de [[01 - Dirección de Arte]] pide no reducir la legibilidad.


> **Navegación:** [[00 - Índice]] · ← [[03 - Entornos]] · [[05 - Audio y Música]] →
