# Seguridad y Riesgos Técnicos

## Descripción de la sección

Documenta riesgos técnicos y medidas para reducir fallos, pérdida de datos o abuso de sistemas.

## Riesgos

| Riesgo | Probabilidad | Impacto | Mitigación |
|---|---|---|---|
| Los valores del prototipo no coinciden con `AfterLight_Stats.xlsx` | Ya ocurre | El balance probado no corresponde al documentado | Decidir la escala del xlsx y separar los valores en `ScriptableObject` |
| Unity no importa los sonidos en M4A | Ya ocurre | 13 sonidos no pueden usarse en el juego | Convertirlos a WAV u OGG |
| El kit de escenario, el soldado y el plano usan escalas distintas | Ya ocurre | Las piezas no encajan al montar el nivel | Elegir una escala común, como pide [[03 - Entornos]] |
| No hay un objetivo de rendimiento | Por definir | No puede comprobarse si el juego corre bien en el equipo objetivo | Definir los FPS objetivo de [[03 - Requisitos Técnicos]] y medir en cada versión |
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
