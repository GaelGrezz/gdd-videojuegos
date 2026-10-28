# Motor y Herramientas

## Descripción de la sección

Documenta las herramientas utilizadas para crear el videojuego y por qué fueron seleccionadas.

## Motor

**Motor:** Unity 6

**Versión:** 6000.6.2f1

**Renderizado:** Universal Render Pipeline (URP), con el filtro VHS como efecto de posproceso.

**Física:** Física 3D de Unity. Los enemigos se desplazan con NavMesh (AI Navigation).

**Sistema de entrada:** Input System.

## Lenguajes

| Lenguaje | Uso |
|---|---|
| C# | Lógica del juego y herramientas del editor |
| HLSL | Shader del filtro VHS |
| Python | Exportación del modelo del soldado desde Blender |

## Herramientas

| Herramienta | Propósito | Versión |
|---|---|---|
| Unity | Motor del juego | 6000.6.2f1 |
| Blender | Modelado y animación del soldado | 5.2 |
| Substance | Texturas del soldado | Por definir |
| Figma | Diseño de la interfaz: https://www.figma.com/design/JkL3M7721mwAdL0gTmdZaW/Untitled | — |
| Photoshop, Illustrator y After Effects | Por definir | Por definir |
| Obsidian | Redacción del GDD | — |
| Git y GitHub | Control de versiones | — |

## Dependencias

Lista librerías, paquetes, plugins o servicios externos.

- Universal RP 17.7.0
- AI Navigation 2.0.14
- Input System 1.20.0
- Visual Effect Graph 17.6.0

## Convenciones del proyecto

- **Estructura de carpetas:** `Assets/Art`, `Assets/Audio`, `Assets/Code` (Core, Player, Combat, Enemies, Systems, UI, Prototype y Editor), `Assets/Level` y `Assets/Docs`.
- **Nomenclatura:** Clases en inglés, salvo las entidades del juego (`Ascendido`, `Quimera`); textos y comentarios en español.
- **Control de versiones:** Git, con el repositorio indicado en [[01 - Ficha del Proyecto]].
- **Formato de assets:** Modelos FBX exportados desde Blender y texturas PNG.
- **Convenciones de código:** Espacio de nombres `AfterLight`. Los valores de balance se agrupan en `GameConfig` y se editan desde el inspector.


> **Navegación:** [[00 - Índice]] · ← [[01 - Arquitectura Técnica]] · [[03 - Requisitos Técnicos]] →
