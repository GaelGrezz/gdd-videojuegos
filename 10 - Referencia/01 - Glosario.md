# Glosario
## Términos de desarrollo y diseño

| Término            | Definición                                                                                                                                                                                   |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **GDD**            | _Game Design Document_. Documento que centraliza las decisiones de diseño del videojuego.                                                                                                    |
| **Mecánica**       | Regla o interacción individual mediante la cual el jugador puede actuar sobre el juego.                                                                                                      |
| **Sistema**        | Conjunto de mecánicas, componentes y reglas que interactúan entre sí.                                                                                                                        |
| **Core Loop**      | Secuencia principal de acciones que el jugador repite durante la experiencia.                                                                                                                |
| **Gameplay**       | Conjunto de interacciones y experiencias que surgen mientras el jugador controla el juego.                                                                                                   |
| **MVP**            | _Minimum Viable Product_. Versión mínima funcional necesaria para validar las mecánicas principales.                                                                                         |
| **Vertical Slice** | Sección pequeña pero representativa de la calidad y funcionamiento esperados del producto final.                                                                                             |
| **Prototipo**      | Implementación temprana utilizada para comprobar si una mecánica o sistema funciona antes de producirlo completamente.                                                                       |
| **Build**          | Combinación de mejoras, estadísticas y efectos seleccionados por el jugador durante una partida. También puede referirse a una versión ejecutable del juego según el contexto de desarrollo. |
| **Run / Partida**  | Sesión de juego comprendida desde el inicio de una operación hasta la victoria, derrota o abandono.                                                                                          |
| **Oleada**         | Grupo o incremento temporal de enemigos enviado contra el jugador o un objetivo.                                                                                                             |
| **Spawn**          | Aparición de una entidad dentro del escenario.                                                                                                                                               |
| **Cooldown**       | Tiempo que debe transcurrir antes de que una habilidad pueda volver a utilizarse.                                                                                                            |
| **Buff**           | Efecto positivo que aumenta temporal o permanentemente una característica.                                                                                                                   |
| **Debuff**         | Efecto negativo aplicado a una entidad.                                                                                                                                                      |
| **Drop**           | Objeto o recurso generado como recompensa, generalmente después de derrotar un enemigo.                                                                                                      |
| **VFX**            | Visual Effects. Efectos visuales utilizados para representar disparos, impactos, cristales, habilidades y otros eventos.                                                                     |
| **SFX**            | Sound Effects. Efectos de sonido asociados con acciones o eventos del juego.                                                                                                                 |
| **UI**             | User Interface. Elementos visuales mediante los cuales se comunica información al jugador.                                                                                                   |
| **HUD**            | Parte de la interfaz visible durante el gameplay, como vida, batería, munición o indicadores.                                                                                                |

---

# Términos de gameplay

| Término               | Definición                                                                                                                                                   |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Jugador**           | Personaje controlado directamente por el usuario durante una operación.                                                                                      |
| **Vida**              | Cantidad de daño que el jugador puede recibir antes de ser derrotado.                                                                                        |
| **Batería**           | Recurso energético utilizado principalmente para mantener operativa la linterna y sus funciones.                                                             |
| **Linterna**          | Herramienta principal de iluminación del jugador. También puede aplicar efectos o vulnerabilidades a determinados Vimers.                                    |
| **Alcance de luz**    | Distancia efectiva cubierta por la linterna.                                                                                                                 |
| **Generador**         | Objetivo estratégico que proporciona energía a sectores de la instalación y que puede requerir reparación y defensa.                                         |
| **Reparación**        | Acción mediante la cual el jugador restaura el funcionamiento de un generador u otro sistema.                                                                |
| **Cristal**           | Recurso que puede ser liberado por determinados enemigos y utilizado para progresión durante la partida.                                                     |
| **Mejora**            | Modificación que aumenta, altera o especializa las capacidades del jugador, arma, linterna o sistema.                                                        |
| **Carta de mejora**   | Representación dentro de la interfaz de una mejora disponible para ser seleccionada.                                                                         |
| **Racha**             | Progresión acumulativa obtenida mediante determinadas acciones consecutivas y que puede perderse al recibir daño.                                            |
| **Jefe**              | Enemigo de alta peligrosidad diseñado como punto culminante de una fase o partida.                                                                           |
| **Enemigo élite**     | Variante más peligrosa de un enemigo convencional con estadísticas o capacidades adicionales.                                                                |
| **Director de IA**    | Sistema encargado de regular dinámicamente la presión sobre el jugador mediante aparición, cantidad y tipo de enemigos.                                      |
| **Tickets**           | Recurso interno utilizado por el Director de IA para determinar qué enemigos puede generar. Enemigos más peligrosos requieren una mayor cantidad de tickets. |
| **Zona de aparición** | Área válida desde la cual pueden generarse enemigos.                                                                                                         |


---

# Términos del universo

| Término                   | Definición                                                                                                                                                                                  |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **AfterLight**            | Nombre del videojuego y del proyecto.                                                                                                                                                       |
| **Hades**                 | Colonia humana y escenario principal de los acontecimientos del juego. Posee grandes depósitos de cristales utilizados como fuente energética.                                              |
| **CERBERUS**              | Organización encargada de responder a amenazas extraordinarias, contener brotes, proteger instalaciones estratégicas y controlar Zonas de Exclusión.                                        |
| **Zona de Exclusión**     | Área cerrada por CERBERUS debido a contaminación, presencia de Vimers o riesgo extraordinario para la población.                                                                            |
| **Cristales de Hades**    | Formaciones minerales con un elevado potencial energético cuya explotación está relacionada con la crisis de la colonia.                                                                    |
| **Violeta Mortífera**     | Nombre utilizado para la infección o fenómeno asociado con la exposición a los cristales y la transformación de organismos vivos.                                                           |
| **Vimer**                 | Individuo afectado y transformado por la Violeta Mortífera.                                                                                                                                 |
| **Vimers**                | Plural de Vimer. Designa colectivamente a los individuos infectados.                                                                                                                        |
| **Infectado**             | Término genérico utilizado para describir a una persona u organismo afectado por la Violeta Mortífera. Puede utilizarse antes de que la transformación alcance el estado considerado Vimer. |
| **Centro científico**     | Instalación de investigación de Hades dedicada originalmente al estudio de los cristales y anomalías del planeta. Constituye uno de los principales escenarios de _AfterLight_.             |
| **Operativo**             | Miembro de CERBERUS desplegado directamente en operaciones de campo.                                                                                                                        |
| **Contención**            | Conjunto de procedimientos destinados a impedir que una amenaza abandone una zona determinada.                                                                                              |
| **Operación de limpieza** | Intervención militar destinada a recuperar sectores contaminados y eliminar focos activos de Vimers.                                                                                        |
| **Perímetro**             | Línea defensiva establecida alrededor de una Zona de Exclusión para controlar accesos y evitar fugas.                                                                                       |
| **Área contaminada**      | Sector donde existe evidencia de infección, crecimiento cristalino o presencia activa de Vimers.                                                                                            |

---

# Convenciones de nombres

Esta sección establece cómo deben escribirse los principales términos del proyecto en documentación, código, interfaces y material narrativo.

## Nombre del juego

Escribir siempre:

**AFTERLIGHT**

Evitar:

- Afterlight
- After Light
- AFTER LIGHT

En títulos o material gráfico puede utilizarse **AFTERLIGHT** únicamente como decisión tipográfica.

---

## CERBERUS

El nombre de la organización debe escribirse siempre:

**CERBERUS**

puede utilizarse también:
**CERBERUS — Centralized Emergency Response Bureau for Extranormal Recovery & Urban Security**

Evitar:

- Cerberus
- Cerbero, cuando se esté hablando de la organización.
- C.E.R.B.E.R.U.S., salvo que se establezca específicamente como variante gráfica.

**Cerbero** se reserva exclusivamente para la criatura de la mitología griega.

---

## Hades

Escribir:
**Hades**

Se utiliza como nombre propio de la colonia.

Evitar utilizar:
- HADES, excepto en señalética o elementos gráficos.
- El Hades, salvo cuando se esté hablando específicamente del concepto mitológico.

---

## Violeta Mortífera

Utilizar:
**Violeta Mortífera**

para referirse a la infección o fenómeno.

Utilizar:
**Vimer**

para un individuo transformado.

Utilizar:
**Vimers**

para varios individuos transformados.

Por tanto:

> La Violeta Mortífera infectó al personal del laboratorio.

> El soldado encontró un Vimer.

> Una oleada de Vimers se aproxima al generador.

Evitar utilizar **Vimer** simultáneamente como nombre de la enfermedad y del infectado, ya que genera ambigüedad dentro de la narrativa.

---

## Cristales

Cuando se hable del recurso en términos generales:
**cristales de Hades**

Cuando el contexto ya sea evidente:
**cristales**

No utilizar **Vimer** como nombre del cristal salvo que posteriormente se establezca oficialmente un mineral o compuesto con ese nombre.

---

## Zonas de Exclusión

Como clasificación oficial:
**Zona de Exclusión**

Plural:
**Zonas de Exclusión**

Cuando se use de manera genérica puede escribirse en minúscula:

> CERBERUS estableció varias zonas de exclusión alrededor del complejo.

---

## Enemigos

Los nombres oficiales de tipos de Vimer utilizan mayúscula inicial, ejemplo: **Cáscara**

Los nombres internos de desarrollo deben evitar sustituir los nombres oficiales una vez que estos hayan sido establecidos.

Por ejemplo, evitar mantener términos como:

- Zombie básico
- Enemy01
- Enemigo gordo
- Bicho de cuatro patas

Estos pueden utilizarse durante prototipado, pero deben reemplazarse cuando la criatura tenga un nombre definitivo.

---

## Sistemas de gameplay

Los nombres de sistemas se escriben con mayúscula inicial cuando hacen referencia a un sistema específico documentado:

- **Director de IA**
- **Sistema de Tickets**
- **Sistema de Mejoras**
- **Sistema de Generadores**
- **Sistema de Batería**

Cuando se describa el concepto genéricamente se utilizan minúsculas.

---

# Regla general

Siempre que se introduzca un nuevo personaje, enemigo, organización, recurso, lugar, sistema o término propio del universo deberá añadirse a este glosario.

Si existen dos palabras diferentes para describir exactamente el mismo concepto, deberá seleccionarse una como término oficial y utilizarla de manera consistente en todo el GDD.
> **Navegación:** [[00 - Índice]] · ← [[04 - Criterios de Aceptación]] · [[02 - Referencias e Inspiración]] →
