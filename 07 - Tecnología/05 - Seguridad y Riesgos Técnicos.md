# Seguridad y Riesgos Técnicos

## Descripción de la sección

Documenta riesgos técnicos y medidas para reducir fallos, pérdida de datos o abuso de sistemas.

## Riesgos

| Riesgo                                                             | Probabilidad | Impacto                                                           | Mitigación                                                                       |
| ------------------------------------------------------------------ | ------------ | ----------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| Unity no importa los sonidos en M4A                                | Resuelto     | Ninguno: los 13 sonidos ya están en WAV en el prototipo           | Se convirtieron a WAV                                                            |
| Rendimiento de la compilación de Windows pendiente de medir | Abierto | Los requisitos de hardware dependen de los resultados en partida | Medir FPS, carga y memoria con los perfiles de [[03 - Requisitos Técnicos]] |

## Datos sensibles

¿El juego almacena información personal, cuentas, estadísticas en línea u otros datos?

No. El juego no usa cuentas ni conexión y solo conserva la configuración del jugador en su equipo.

## Multijugador

Si existe conexión en red, documentar:

- Autenticación
- Validación
- Autoridad del servidor
- Comunicación
- Protección contra manipulación

No aplica. El juego es para un solo jugador y no requiere conexión.

## Recuperación

¿Qué ocurre ante corrupción de datos, pérdida de conexión o fallo del programa?

- **Error durante la carga:** La partida no comienza. Se muestra *Despliegue interrumpido* con las opciones Reintentar y Menú principal, como indica [[07 - Reglas y Estados del Juego]].
- **Corrupción de datos:** Por definir. Solo puede afectar a la configuración.
- **Pérdida de conexión:** No aplica.
- **Fallo del programa:** Se pierde la partida en curso, porque no se guarda. El comportamiento al volver a abrir el juego está por definir.


> **Navegación:** [[00 - Índice]] · ← [[04 - Datos y Persistencia]] · [[01 - Alcance]] →
