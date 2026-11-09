# Gestión de Cambios

## Descripción de la sección

El diseño de un videojuego cambia. Esta sección evita que las modificaciones importantes se pierdan o aparezcan sin evaluar sus consecuencias.

## Solicitud de cambio

**Fecha:**

**Cambio propuesto:**

**Motivo:**

**Beneficio esperado:**

**Costo estimado:**

**Impacto en otros sistemas:**

**Decisión:**

**Responsable:**

## Registro

| Fecha | Cambio | Motivo | Impacto | Estado |
|---|---|---|---|---|
| 2026-10-20 | Tienda y moneda fuera del prototipo; las mejoras se obtienen solo al subir de nivel | Decisión del equipo | Economía y Recursos, Progresión y `AfterLight_Stats.xlsx` | Aprobado |
| 2026-10-20 | La linterna permanece encendida y se orienta con el cursor del arma | Decisión del equipo | Mecánicas, Controles y Sistemas | Aprobado |
| 2026-11-02 | Las balas dejan de ser un recurso; el cargador es una característica del arma | Decisión del equipo | Economía y Recursos y Mecánicas | Aprobado |
| 2026-11-02 | El jugador se mueve con `Rigidbody` | Decisión del equipo | Arquitectura Técnica; el prototipo usa `CharacterController` | Reemplazado por el cambio del 2026-11-07 |
| 2026-11-02 | El juego tiene un solo nivel de 10 minutos y el Ascendido aparece al cumplirse | Decisión del equipo | Estructura del Contenido y director; el director de Unity escala durante 10 minutos, pero el Ascendido aún no existe | Aprobado; falta el Ascendido en Unity |
| 2026-11-02 | Se quitan los botiquines y la salud se regenera con el tiempo | Decisión del equipo | Objetos y Coleccionables, Sistemas y Reglas | Aprobado |
| 2026-11-07 | El jugador se mueve con `CharacterController` en lugar de `Rigidbody` | Decisión del equipo; es lo que usa el prototipo | Arquitectura Técnica y Backlog | Aprobado |
| 2026-11-08 | Los valores implementados en Unity dejan de ser propuestas y pasan a ser los del juego; el soldado corre por defecto y camina con Shift a 1.8 m/s | Que el GDD y `AfterLight_Stats.xlsx` coincidan con Unity | Mecánicas, Economía y Recursos, Enemigos y NPC, Objetos y Coleccionables, Controles y el xlsx | Aprobado |


> **Navegación:** [[00 - Índice]] · ← [[04 - Backlog del Proyecto]] · [[01 - Criterios de Calidad]] →
