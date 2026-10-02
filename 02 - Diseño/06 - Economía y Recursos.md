# Economía y Recursos

## Descripción de la sección

Documenta cualquier recurso cuantificable: dinero, vida, energía, munición, experiencia, materiales, tiempo, puntos, etc.

## Recursos
| Recurso                       | Obtención                                              | Uso                                                 | Límite                                    | Pérdida                                                                                        |
| ----------------------------- | ------------------------------------------------------ | --------------------------------------------------- | ----------------------------------------- | ---------------------------------------------------------------------------------------------- |
| Salud del soldado             | Principalmente botiquines y efectos de mejoras         | Permite resistir ataques                            | Salud máxima por definir                  | Disminuye al recibir daño; llegar a cero provoca derrota                                       |
| Batería de la linterna        | Estar cerca de un generador                            | Alimenta la linterna y sus efectos                  | Entre 0 % y 100 %                         | Se consume durante su uso; permanecer al 0 % durante el tiempo límite provoca derrota          |
| Integridad de los generadores | Se recupera al repararlos                              | Mantiene los generadores en funcionamiento          | Entre 0 % y 100 %                         | Disminuye al recibir ataques; al llegar a cero, el generador queda destruido y puede repararse |
| Cristales                     | Los sueltan los enemigos al ser eliminados             | Permiten subir de nivel y escoger una mejora        | Cantidad requerida por nivel, por definir | El contador se reinicia al escoger una mejora                                                  |
| Moneda —nombre provisional—   | La sueltan los enemigos al ser eliminados              | Permite comprar armas y mejoras en la tienda        | Sin limite                                | Se descuenta el precio de cada compra                                                          |
| Racha de eliminaciones        | Eliminaciones consecutivas sin recibir daño            | Permite alcanzar umbrales que otorgan potenciadores | Sin límite                                | Se reinicia cuando el jugador recibe daño                                                      |
| Tickets del director          | Asignación inicial y obtención conforme pasa el tiempo | Permiten al director seleccionar y generar enemigos | Presupuesto máximo por definir            | Se descuentan al generar enemigos                                                              |
Los tickets pertenecen al director de enemigos. El jugador no puede obtenerlos, gastarlos ni intercambiarlos.

El tiempo transcurrido también se registra: determina el crecimiento del presupuesto del director y la aparición del jefe final. No funciona como una moneda ni se consume al realizar acciones.
## Fuentes y sumideros

**Fuentes:**

- Los botiquines son la principal fuente de recuperación de salud.
- Algunas mejoras permiten recuperar salud al cumplir condiciones específicas. Por ejemplo, completar la reparación de un generador destruido.
- La reparación recupera la integridad de los generadores.
- Los enemigos eliminados sueltan cristales y moneda.
- Las eliminaciones sin recibir daño incrementan la racha.
- El director recibe tickets conforme transcurre el tiempo.
- La batería de la linterna se recupera al estar cerca de un generador.

**Sumideros:**
- Los ataques reducen la salud del soldado o la integridad de los generadores.
- Utilizar la linterna consume batería.
- Elegir una mejora tras subir de nivel reinicia los cristales acumulados.
- Comprar armas y mejoras consume moneda.
- Recibir daño reinicia la racha de eliminaciones.
- Generar enemigos consume tickets del director.

## Reglas

### Salud y batería

- La salud y la batería permanecen entre cero y sus respectivos valores máximos.
- Los botiquines recuperan una cantidad de salud por definir, sin superar la salud máxima.
- La curación asociada a una mejora solo se activa si el jugador posee esa mejora y cumple su condición.
- Llegar a cero de salud provoca una derrota inmediata.
- Llegar al 0 % de batería inicia un periodo de tolerancia. Si el jugador permanece sin carga durante ese tiempo, pierde la partida.
- La duración del periodo de tolerancia y el comportamiento del contador al recuperar batería están por definir.

### Generadores

- Reparar un generador recupera su integridad hasta el máximo establecido.
- Un generador destruido puede volver a funcionar tras su reparación.
- Su destrucción interrumpe sus beneficios hasta recuperarlo; no provoca una derrota directa.
- Las condiciones para interrumpir la reparación es recibir daño.

### Cristales y subida de nivel

- Los cristales recogidos aumentan el progreso hacia el siguiente nivel del jugador.
- Al alcanzar la cantidad requerida, el jugador puede escoger una mejora.
- Al confirmar la selección, se aplica la mejora y el contador de cristales vuelve a cero.
- Los requisitos de cristales para cada nivel aumentan conforme al nivel.
- La subida de nivel del jugador ocurre durante la partida y es independiente del tiempo que determina la aparición del jefe final.

### Moneda y tienda

- La moneda recogida se acumula en el saldo del jugador.
- Las compras solo pueden completarse si tiene suficiente moneda.
- Cada compra descuenta su precio y entrega el arma o aplica la mejora correspondiente.
- Los precios, el catálogo y la forma de acceder a la tienda están por definir.

### Rachas y potenciadores

- La racha aumenta con cada eliminación válida y no tiene un límite máximo.
- Recibir daño reinicia la racha a cero.
- Los potenciadores se otorgan al alcanzar umbrales definidos.
- Una racha ilimitada no implica que los beneficios aumenten sin límite.
-  perder la racha anula los potenciadores.

### Tickets del director

- El director recibe tickets conforme transcurre el tiempo.
- Cada tipo de enemigo tiene un costo.
- El director solo puede generar enemigos que pueda pagar con su presupuesto disponible.
- El costo se descuenta una sola vez por enemigo generado.

### Recolección de recursos

- Las cantidades y probabilidades de aparición de cristales y moneda dependen de la dificultad del enemigo.
- Los recursos tienen un tiempo limite y desaparecen si no son recogidos a tiempo.

## Balance

**¿Qué comportamiento queremos incentivar?**

- Eliminar enemigos y recoger sus recursos para fortalecer al personaje.
- Usar la linterna de forma intencional y vigilar la batería.
- Evitar daño para conservar la racha y alcanzar nuevos umbrales.
- Buscar botiquines cuando sea necesario.
- Reparar y defender generadores para mantener sus beneficios.
- Elegir mejoras y compras que complementen la estrategia del jugador.
- Equilibrar la búsqueda de recursos con la supervivencia y la defensa.

**¿Qué comportamiento queremos evitar?**

- Que conservar batería obligue a pasar la mayor parte de la partida sin utilizar la linterna.
- Que quedarse sin carga provoque una derrota inevitable sin oportunidad de recuperarse.
- Que dejar destruir un generador para repararlo y recuperar salud sea más conveniente que defenderlo.
- Que reparar generadores ocupe tanto tiempo que impida combatir.
- Que una única arma o combinación de mejoras sea siempre la opción más conveniente.
- Que perder una racha deje al jugador sin opciones para recuperarse.
- Que la curación sea tan abundante que recibir daño deje de importar.
- Que la acumulación de tickets produzca aumentos repentinos de dificultad imposibles de afrontar.

> **Navegación:** [[00 - Índice]] · ← [[05 - Progresión]] · [[07 - Reglas y Estados del Juego]] →
