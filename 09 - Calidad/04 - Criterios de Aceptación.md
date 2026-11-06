# Criterios de Aceptación

## Descripción de la sección

Los criterios de aceptación permiten decidir objetivamente si una característica está lista.

## Plantilla

### Característica

**Dado que:** <!-- contexto inicial -->

**Cuando:** <!-- acción -->

**Entonces:** <!-- resultado esperado -->

## Características

### Linterna y batería

**Dado que:** La batería tiene carga.

**Cuando:** El jugador ilumina a un Vimer con el cono de luz.

**Entonces:** El Vimer muestra que está debilitado y recibe los efectos de la linterna mientras permanece en el cono.

### Periodo de tolerancia

**Dado que:** La batería está al 0 % y la cuenta regresiva está activa.

**Cuando:** El jugador recupera carga junto a un generador operativo.

**Entonces:** La cuenta regresiva se cancela y se reinicia. Si se agota sin recuperar carga, la partida termina con *Sin luz*.

### Generadores

**Dado que:** Un generador está destruido.

**Cuando:** La partida continúa.

**Entonces:** El generador deja de dar sus beneficios y de recargar la batería hasta repararse, y su destrucción no provoca una derrota.

### Selección de mejora

**Dado que:** El jugador reúne los cristales requeridos.

**Cuando:** Se abre Elige una mejora.

**Entonces:** La simulación y el reloj se detienen hasta que elige una carta; después se aplica la mejora y el contador de cristales vuelve a cero.

### Racha

**Dado que:** El jugador tiene una racha de eliminaciones y potenciadores activos.

**Cuando:** Recibe daño.

**Entonces:** La racha y los potenciadores se reinician.

### Victoria

**Dado que:** Se cumplieron los 10 minutos de supervivencia y apareció el Ascendido.

**Cuando:** El jugador lo derrota sin que se active una condición de derrota.

**Entonces:** Se muestra *Información recuperada*, o *Ni uno más* si completó las peticiones de Issac.

### Derrota simultánea

**Dado que:** La salud del soldado y la del Ascendido llegan a cero en la misma actualización.

**Cuando:** El juego resuelve el resultado.

**Entonces:** Tiene prioridad la derrota.

### Error de carga

**Dado que:** Faltan elementos indispensables para la partida.

**Cuando:** Termina la carga.

**Entonces:** La partida no comienza y se muestra *Despliegue interrumpido* con Reintentar y Menú principal.

## Criterios del proyecto

- [ ] El bucle principal funciona.
- [ ] Las condiciones de victoria y derrota funcionan.
- [ ] El progreso puede guardarse.
- [ ] Los sistemas principales están integrados.
- [ ] Las pruebas críticas están aprobadas.
- [ ] El rendimiento cumple el objetivo definido.
- [ ] No existen errores bloqueantes conocidos.


> **Navegación:** [[00 - Índice]] · ← [[03 - Bugs y Seguimiento]] · [[01 - Glosario]] →
