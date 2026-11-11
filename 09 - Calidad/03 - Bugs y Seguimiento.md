# Bugs y Seguimiento

## Descripción de la sección

Registra problemas encontrados durante las pruebas y permite darles seguimiento.

## Reporte de bug

**Título:**

**Versión:**

**Nivel / escena:**

**Pasos para reproducir:**

1.
2.
3.

**Resultado esperado:**

**Resultado actual:**

**Frecuencia:** Siempre / A veces / Rara vez

**Severidad:** Crítica / Alta / Media / Baja

**Evidencia:**

**Estado:** Abierto / En progreso / Resuelto / Cerrado

## Registro

La severidad es una estimación basada en el impacto. Los responsables se asignan por área para el seguimiento actual. La frecuencia queda por registrar cuando no hay datos. **Resuelto** indica que existe una corrección documentada. **Cerrado** se usa al registrar una comprobación posterior de la corrección.

| ID | Bug | Área | Severidad | Responsable | Estado |
|---|---|---|---|---|---|
| 1 | La culata atraviesa el pecho de Eco-10 | Arte y animación | Baja | Enrique Herrera Loeza | Abierto |
| 2 | El Ascendido aparecía a los 5 minutos | Combate final | Alta | Enrique Herrera Loeza, José Roberto Fuentes Salinas | Resuelto |
| 3 | Eco-10 caía al vacío en grietas y cerca del foso | Nivel y colisiones | Alta | Enrique Herrera Loeza, José Roberto Fuentes Salinas | Resuelto |
| 4 | Se veía el fondo negro bajo las grietas de cristal | Arte de entorno | Baja | Enrique Herrera Loeza | Resuelto |
| 5 | Los proyectiles atravesaban paredes finas y puertas al disparar pegado a ellas | Combate y colisiones | Alta | Enrique Herrera Loeza, José Roberto Fuentes Salinas | Resuelto |
| 6 | El menú principal cortaba opciones en ventanas más anchas que 16:9 | Interfaz | Media | Julián Hernández Primo | Resuelto |
| 7 | El haz de la linterna empezaba por delante del arma | Iluminación | Baja | Enrique Herrera Loeza | Resuelto |
| 8 | Los cristales del kit aparecían blancos al cambiar de rama | Importación de arte | Baja | Enrique Herrera Loeza | Resuelto |
| 9 | Unity no importaba los sonidos entregados en M4A | Importación de audio | Media | Diego Rubén Correa Chávez | Resuelto |
| 10 | La compilación arrancaba en la escena de prueba | Carga y compilación | Alta | Enrique Herrera Loeza, José Roberto Fuentes Salinas | Resuelto |
| 11 | La etiqueta del reloj del Ascendido quedaba por debajo del mínimo de texto | Accesibilidad | Baja | Julián Hernández Primo | Abierto |
| 12 | Los pies de Eco-10 patinaban al mezclar reposo y caminata | Animación | Baja | Enrique Herrera Loeza | Resuelto |

## Detalle y comprobación

### 1. La culata atraviesa el pecho de Eco-10

**Comprobación.** En `CentroHades`, acercar la vista al soldado y observar el contacto entre culata y pecho durante reposo, apuntado y las transiciones de animación para identificar la pose exacta.

**Esperado.** La culata queda fuera de la malla del torso. **Observado.** La culata se superpone con el pecho. La pose exacta y la frecuencia quedan por confirmar. Véase [[04 - Backlog del Proyecto]].

### 2. Aparición anticipada del Ascendido

**Comprobación.** Jugar en `CentroHades` sin usar F8. Observar el reloj a los 5 minutos y continuar hasta 10 minutos de juego activo.

**Esperado.** El Ascendido aparece a los 10 minutos. **Observado antes de la corrección.** Aparecía a los 5. La escena actual serializa `SegundosHastaAscendido: 600`. El historial del GDD registra la corrección en la versión 0.15.0. Queda pendiente registrar una partida que confirme el tiempo completo. Véase [[04 - Historial de Versiones]] y [[02 - Pruebas]].

### 3. Caída al vacío en grietas y foso

**Comprobación.** Recorrer las grietas del piso y el borde transitable de la losa del foso del Núcleo en `CentroHades`.

**Esperado.** Eco-10 conserva apoyo al pisar la zona transitable. **Observado antes de la corrección.** Las piezas decorativas carecían de colisión y el jugador podía caer. Se añadieron pisos invisibles con colisión y se rehízo el NavMesh. La escena actual contiene objetos `Suelo_Colision`. Git `63f2ad6`, 2026-11-05.

### 4. Fondo negro visible bajo grietas

**Comprobación.** Revisar las grietas de cristal desde la cámara de juego en `CentroHades`.

**Esperado.** Se ve el suelo de Hades bajo la grieta. **Observado antes de la corrección.** Se veía el fondo negro en lugares donde faltaban baldosas. Se añadieron las baldosas visibles. Git `bc064d6`, 2026-11-08.

### 5. Balas que atravesaban paredes y puertas

**Comprobación.** Colocar a Eco-10 junto a una pared delgada o puerta con colisión y disparar hacia el otro lado.

**Esperado.** El proyectil impacta contra el obstáculo. **Observado antes de la corrección.** La boca del arma podía quedar al otro lado y originar allí la bala. `PlayerCombat.SpawnPoint` comprueba el tramo desde el cuerpo hasta la salida del arma y, si encuentra un obstáculo, origina la bala desde el cuerpo. Git `cb5edf1`, 2026-11-05.

### 6. Opciones del menú fuera de pantalla

**Comprobación.** Abrir `MenuPrincipal` con una relación de aspecto más ancha que 16:9 y revisar las últimas opciones y la ayuda de controles.

**Esperado.** Las opciones y la ayuda quedan visibles. **Observado antes de la corrección.** Los elementos inferiores quedaban fuera de la pantalla. Se centró el bloque de menú y se ancló la ayuda al pie. Git `00f79c4`, 2026-11-08.

### 7. Origen del haz desplazado

**Comprobación.** Apuntar con Eco-10 y observar dónde empieza el cono visible respecto a la boca del rifle.

**Esperado.** El haz visible nace junto a la boca del arma. **Observado antes de la corrección.** El origen estaba desplazado hacia delante y quedaba un hueco. Se recolocó la luz y se ajustó el haz visual. Git `36e754a` y `22ac8e1`, 2026-11-08.

### 8. Cristales blancos después de cambiar de rama

**Comprobación.** Reimportar los FBX del kit CERBERUS y revisar sus piezas de cristal en `CentroHades`, especialmente después de cambiar de rama.

**Esperado.** Se conserva el material de cristal asignado. **Observado antes de la corrección.** Si el FBX se importaba antes que los materiales, algunos cristales quedaban blancos. La reasignación del material se guarda por GUID en los archivos `.meta`. Git `978e522`, 2026-11-08.

### 9. Sonidos M4A sin importar

**Comprobación.** Revisar los clips convertidos en el panel Project de Unity y previsualizar los WAV.

**Esperado.** Los clips están disponibles para asignación y reproducción. **Observado antes de la corrección.** Trece sonidos entregados en M4A quedaron fuera de la importación. Se convirtieron a WAV. Véanse [[05 - Seguridad y Riesgos Técnicos]] y [[04 - Backlog del Proyecto]].

### 10. La compilación abría SampleScene

**Comprobación.** Arrancar una compilación para Windows y comprobar que el primer menú permite elegir Iniciar despliegue y cargar Hades.

**Esperado.** El juego empieza en `MenuPrincipal.unity`. **Configuración anterior.** `SampleScene.unity` estaba primera en la lista de compilación. `EditorBuildSettings.asset` ahora ordena `MenuPrincipal.unity` antes de `CentroHades.unity`. Git `cb5edf1`, 2026-11-05.

### 11. Etiqueta del reloj por debajo del mínimo

**Comprobación.** Abrir `HUD.prefab` y revisar en TextMesh Pro el tamaño de «EL ASCENDIDO LLEGA EN» para la resolución de referencia de 1920 × 1080.

**Esperado.** Tamaño de 14 px como mínimo. **Observado.** El prefab tiene tamaño 12. Confirmado en el editor durante la revisión de [[03 - Accesibilidad]].

### 12. Deslizamiento de los pies al caminar

**Comprobación.** Alternar reposo y caminata lenta y observar los pies de Eco-10, incluida la marcha hacia atrás.

**Esperado.** Los pasos acompañan el desplazamiento. **Observado antes de la corrección.** La mezcla de reposo y caminata igualaba la duración de ambas tomas y los pies patinaban. Se separó reposo en el controlador y se ajustó la velocidad de locomoción. Git `830ef87`, 2026-11-05.

## Antecedente pendiente de precisar

El commit `93bedab` del 2026-10-30 registra «assets faltantes». Los cambios muestran ajustes de paquetes y configuración. El mensaje del commit deja sin identificar los recursos que faltaban y la forma de reproducirlo.


> **Navegación:** [[00 - Índice]] · ← [[02 - Pruebas]] · [[04 - Criterios de Aceptación]] →
