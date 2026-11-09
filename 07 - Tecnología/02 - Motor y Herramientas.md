# Motor y Herramientas

## Descripción de la sección

Documenta las herramientas utilizadas para crear el videojuego y por qué fueron seleccionadas.

## Motor

**Motor:** Unity 6

**Versión:** 6000.6.2f1

**Renderizado:** Universal Render Pipeline (URP), con un efecto de cámara pixelada. El filtro VHS está por implementar.

**Física:** Física 3D de Unity. El soldado se mueve con `CharacterController` y los enemigos con NavMesh (AI Navigation).

**Sistema de entrada:** Input System.

## Lenguajes

| Lenguaje | Uso |
|---|---|
| C# | Lógica del juego y herramientas del editor |
| HLSL | Shader del efecto de cámara pixelada |
| Python | Animación de la Cáscara y exportación de los modelos de Eco-10 y la Cáscara desde Blender |

## Herramientas

| Herramienta                            | Propósito                                                                              | Versión     |
| -------------------------------------- | -------------------------------------------------------------------------------------- | ----------- |
| Unity                                  | Motor del juego                                                                        | 6000.6.2f1  |
| Blender                                | Modelado y animación de Eco-10 y la Cáscara,<br>y kit de escenario                     | 5.2         |
| Substance                              | Texturas del soldado                                                                   | Por definir |
| Figma                                  | Diseño de la interfaz: https://www.figma.com/design/CsKcKS3qtpDfb43BoK5x95             | —           |
| Photoshop, Illustrator y After Effects | Por definir                                                                            | Por definir |
| Google Drive                           | Recursos: <br>https://drive.google.com/drive/folders/1ulW_KsSiVsZJhayOrtwSla0eNZTLi1HK | —           |
| Obsidian                               | Redacción del GDD                                                                      | —           |
| Git y GitHub                           | Control de versiones                                                                   | —           |

## Dependencias

Lista librerías, paquetes, plugins o servicios externos.

- Universal RP 17.7.0
- AI Navigation 2.0.14
- Input System 1.20.0
- Visual Effect Graph 17.6.0
- uGUI 2.6.0, con TextMesh Pro

## Convenciones del proyecto

- **Estructura de carpetas:** `Assets/Art` (modelos, kit, generador, texturas, fuentes e interfaz), `Assets/Audio`, `Assets/Code` (`Scripts` con Combat, Core, Enemies, Level, Player, Progression, Render, UI y Upgrades; `Shaders` y `Editor`), `Assets/Level` (escenas, prefabs, interfaz y datos), `Assets/Docs` y `Tools/Blender`.
- **Nomenclatura:** Clases en inglés o en español; las entidades y los sistemas propios del juego usan su nombre en español (`Cascara`, `Generador`, `DirectorIA`). Textos y comentarios en español.
- **Control de versiones:** Git, con el repositorio indicado en [[01 - Ficha del Proyecto]].
- **Formato de assets:** Modelos FBX exportados desde Blender y texturas PNG.
- **Convenciones de código:** Espacio de nombres `AfterLight`. Las cartas de mejora son `ScriptableObject` en `Assets/Level/Data/Mejoras`; los demás valores de balance se editan en el inspector de los prefabs y de la escena, con los valores de `AfterLight_Stats.xlsx`.


> **Navegación:** [[00 - Índice]] · ← [[01 - Arquitectura Técnica]] · [[03 - Requisitos Técnicos]] →
