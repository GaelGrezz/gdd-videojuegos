# Economía y Recursos

## Descripción de la sección

Documenta cualquier recurso cuantificable: dinero, vida, energía, munición, experiencia, materiales, tiempo, puntos, etc.

## Recursos
| Recurso                       | Obtención                                              | Uso                                                 | Límite                                    | Pérdida                                                                                        |
| ----------------------------- | ------------------------------------------------------ | --------------------------------------------------- | ----------------------------------------- | ---------------------------------------------------------------------------------------------- |
| Salud del soldado             | Regeneración tras recibir daño y efectos de mejoras    | Permite resistir ataques                            | 100 PV                                    | Disminuye al recibir daño; llegar a cero provoca derrota                                       |
| Batería de la linterna        | Permanecer cerca de un generador operativo             | Alimenta la linterna y sus efectos                  | Entre 0 % y 100 %                         | Se consume durante su uso; permanecer al 0 % durante el tiempo límite provoca derrota          |
| Integridad de los generadores | Se recupera al repararlos                              | Mantiene los generadores en funcionamiento          | Entre 0 % y 100 %                         | Disminuye al recibir ataques; al llegar a cero, el generador queda destruido y puede repararse |
| Cristales                     | Los sueltan los enemigos al ser eliminados             | Permiten subir de nivel y escoger una mejora        | 5 para el primer nivel y 3 más por cada nivel siguiente | El contador se reinicia al escoger una mejora                                                  |
| Racha de eliminaciones        | Eliminaciones consecutivas sin recibir daño            | Permite alcanzar umbrales que otorgan potenciadores | Sin límite                                | Se reinicia cuando el jugador recibe daño                                                      |
| Tickets del director          | Asignación inicial y obtención conforme pasa el tiempo | Permiten al director seleccionar y generar enemigos | Un máximo que crece de 4 a 20 tickets durante la partida | Se descuentan al generar enemigos                                                              |
Los tickets pertenecen al Director de IA. El jugador no puede obtenerlos, gastarlos ni intercambiarlos.

El tiempo transcurrido también se registra: determina el crecimiento del presupuesto del director y la aparición del jefe final. No funciona como una moneda ni se consume al realizar acciones.
## Fuentes y sumideros

**Fuentes:**

- La salud se regenera con el tiempo después de recibir daño.
- Algunas mejoras permiten recuperar salud al cumplir condiciones específicas. Por ejemplo, completar la reparación de un generador destruido.
- La reparación recupera la integridad de los generadores.
- Los enemigos eliminados sueltan cristales.
- Las eliminaciones sin recibir daño incrementan la racha.
- El director recibe tickets conforme transcurre el tiempo.
- La batería de la linterna se recupera al permanecer cerca de un generador operativo.

**Sumideros:**
- Los ataques reducen la salud del soldado o la integridad de los generadores.
- Utilizar la linterna consume batería.
- Elegir una mejora tras subir de nivel reinicia los cristales acumulados.
- Recibir daño reinicia la racha de eliminaciones.
- Generar enemigos consume tickets del director.

## Reglas

### Salud y batería

- La salud y la batería permanecen entre cero y sus respectivos valores máximos.
- La regeneración no supera la salud máxima. Empieza 5 s después del daño y recupera 2 PV/s; un nuevo golpe reinicia la espera.
- La curación asociada a una mejora solo se activa si el jugador posee esa mejora y cumple su condición.
- Llegar a cero de salud provoca una derrota inmediata.
- Llegar al 0 % de batería inicia un periodo de tolerancia. Si el jugador permanece sin carga durante ese tiempo, pierde la partida.
- Recuperar batería por encima del 0 % cancela y reinicia el periodo de tolerancia de 5 s. Dentro del radio de un generador operativo se aplica la recarga sin consumo simultáneo. Si coinciden varios radios, se usa un solo generador.

### Generadores

- Reparar un generador recupera su integridad hasta el máximo establecido. Tiene 100 de integridad y necesita 100 puntos de reparación, 10 s a la velocidad base.
- Mientras está operativo, recarga la batería del soldado cercano. Recarga 10 unidades por segundo a menos de 5 m.
- Después de reparar o restaurar a tope, el generador queda 20 s sin poder volver a repararse. Tras la destrucción queda bloqueado 60 s. Los tres empiezan averiados y pueden repararse desde el inicio.
- Su destrucción interrumpe sus beneficios hasta recuperarlo; no provoca una derrota directa.
- La reparación se interrumpe si el soldado recibe daño.

### Cristales y subida de nivel

- Los cristales recogidos aumentan el progreso hacia el siguiente nivel del jugador.
- Al alcanzar la cantidad requerida, el jugador puede escoger una mejora.
- Al confirmar la selección, se aplica la mejora y el contador de cristales vuelve a cero.
- Los requisitos de cristales para cada nivel aumentan conforme al nivel.
- La subida de nivel del jugador ocurre durante la partida y es independiente del tiempo que determina la aparición del jefe final.

### Moneda y tienda

Fuera del prototipo. No existen moneda ni tienda; las mejoras se obtienen únicamente al subir de nivel con cristales. Ver [[03 - Registro de Decisiones]].

### Rachas y potenciadores

- La racha aumenta con cada eliminación válida y no tiene un límite máximo.
- Recibir daño reinicia la racha a cero.
- Los potenciadores se otorgan al alcanzar umbrales: +15 % de daño a las 5 eliminaciones, +15 % de cadencia a las 10 y +10 % de velocidad al correr a las 20. Se suman a las mejoras y duran mientras dure la racha.
- Una racha ilimitada no implica que los beneficios aumenten sin límite.
- Perder la racha anula los potenciadores.

### Tickets del director

- El director recibe tickets conforme transcurre el tiempo. Empieza con 3 tickets y su ingreso crece de 0.25 a 1 ticket por segundo durante los 10 minutos.
- Cada tipo de enemigo tiene un costo: la Cáscara cuesta 1 ticket.
- El director solo puede generar enemigos que pueda pagar con su presupuesto disponible.
- El costo se descuenta una sola vez por enemigo generado.

### Recolección de recursos

- Todo enemigo regular eliminado suelta cristales; la cantidad depende de su dificultad.
- Los recursos tienen un tiempo límite y desaparecen si no son recogidos a tiempo. Los cristales duran 20 s y parpadean durante los últimos 5 s.

## Balance

**¿Qué comportamiento queremos incentivar?**

- Eliminar enemigos y recoger sus recursos para fortalecer al personaje.
- Orientar la luz con intención y vigilar la batería para regresar a tiempo a un generador operativo.
- Evitar daño para conservar la racha y alcanzar nuevos umbrales.
- Reparar y defender generadores para mantener sus beneficios.
- Elegir mejoras que complementen la estrategia del jugador.
- Equilibrar la búsqueda de recursos con la supervivencia y la defensa.

**¿Qué comportamiento queremos evitar?**

- Que el consumo constante de la linterna obligue a permanecer junto a los generadores la mayor parte de la partida.
- Que quedarse sin carga provoque una derrota inevitable sin oportunidad de recuperarse.
- Que dejar destruir un generador para repararlo y recuperar salud sea más conveniente que defenderlo.
- Que reparar generadores ocupe tanto tiempo que impida combatir.
- Que una única arma o combinación de mejoras sea siempre la opción más conveniente.
- Que perder una racha deje al jugador sin opciones para recuperarse.
- Que la curación sea tan abundante que recibir daño deje de importar.
- Que la acumulación de tickets produzca aumentos repentinos de dificultad imposibles de afrontar.

> **Navegación:** [[00 - Índice]] · ← [[05 - Progresión]] · [[07 - Reglas y Estados del Juego]] →
