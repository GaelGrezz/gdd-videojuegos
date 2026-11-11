# Requisitos Técnicos

## Plataforma de la primera versión

AfterLight se entrega como juego de escritorio para **Windows x64**, para un jugador, con teclado y mouse. La partida se ejecuta sin conexión. Las preferencias se guardan localmente y cada partida comienza desde cero. Véase [[04 - Datos y Persistencia]].

La primera versión usa Unity **6000.6.2f1**, URP y el perfil de compilación `Windows.asset`. El orden de juego es `MenuPrincipal.unity` → `CentroHades.unity`. La interfaz se diseñó para **1920 × 1080** en **16:9**. El proyecto tiene la sincronización vertical desactivada.

## Compatibilidad de base

- **Sistema operativo.** Windows 10 21H1 o posterior según los requisitos del motor. Windows 11 x64 es la referencia para la prueba de entrega.
- **Procesador.** x64 con SSE2.
- **Gráficos.** GPU con controladores del fabricante y compatibilidad con DirectX 12 para los perfiles de prueba. La API efectiva se registra al ejecutar la compilación.
- **Entrada.** Teclado y mouse.
- **Almacenamiento.** Se registrará el tamaño real de la carpeta distribuida una vez descomprimida.

Referencia de plataforma. [Compatibilidad de Unity 6.6 con Windows](https://docs.unity.com/en-us/engine/6000.6/manual/platform-specific/windows/requirements-and-compatibility).

## Perfiles de prueba

Estos perfiles sirven para medir la primera compilación. Los requisitos mínimos y recomendados del juego se publican con los resultados de las pruebas.

| Parámetro | Equipo de entrada | Equipo de referencia |
|---|---|---|
| CPU | x64 de 4 núcleos | x64 de 6 núcleos |
| GPU | Compatible con DirectX 12, integrada o dedicada | Dedicada compatible con DirectX 12 |
| RAM del sistema | 8 GB | 16 GB |
| Almacenamiento de prueba | SSD | SSD |
| Resolución | 1280 × 720, 16:9 | 1920 × 1080, 16:9 |
| FPS objetivo | 30 FPS de media | 60 FPS de media |

## Metas de carga y memoria

- **Carga.** Hasta 10 s en el equipo de referencia, desde Iniciar despliegue hasta recibir el control de Eco-10.
- **Memoria.** Hasta 4 GB de RAM en uso por el proceso del juego en el equipo de referencia.
- **Medición.** Ejecutar una compilación de Windows y registrar hardware, API gráfica, resolución, FPS medios y pico de memoria. Incluir la parte de la partida con mayor actividad de enemigos y el combate contra el Ascendido. Véase [[02 - Pruebas]].

Los valores de rendimiento, carga y memoria son metas iniciales. La validación de la compilación sigue pendiente.

> **Navegación:** [[00 - Índice]] · ← [[02 - Motor y Herramientas]] · [[04 - Datos y Persistencia]] →
